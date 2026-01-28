# HackRF Support Investigation

## Executive Summary: The Real Story

**CRITICAL FINDING:** HackRF support was **IMPLEMENTED** and then **DELIBERATELY REMOVED**.

This investigation uncovered that McLean's claim wasn't unfulfilled vaporware—HackRF support actually existed briefly via the GNU Radio flowgraph, but was **removed on June 22, 2021** to enable generic device auto-detection.

---

## The Claim vs Reality

**The Claim (August 2020):**
> "McLean mentioned he's modifying his SDRSpectrumAnalyzer code to support HackRF, which would make it the preferred hardware for running his detection software."

**The Reality (Discovered January 2025):**

| Phase | Status | Evidence |
|-------|--------|----------|
| Aug 2020 | Claim made | YouTube video |
| ~2020-2021 | HackRF support implemented | GNU Radio flowgraph with `hackrf=0` |
| **June 22, 2021** | **HackRF support REMOVED** | Commit `b79f25d` |
| 2021-2025 | Never re-implemented | Code search confirms |

---

## The Smoking Gun: Commit b79f25d

On **June 22, 2021**, McLean explicitly removed HackRF support:

**Commit Message:**
> "Removed 'hackrf=0', used to specify a HackRF device, from the GNU radio flowgraph so that other devices are detected and used."

**The Actual Code Change:**

```diff
--- a/GNURadioDeviceFlowgraph/top_block.py
+++ b/GNURadioDeviceFlowgraph/top_block.py
- self.osmosdr_source_0 = osmosdr.source( args="numchan=" + str(1) + " " + 'hackrf=0' )
+ self.osmosdr_source_0 = osmosdr.source( args="numchan=" + str(1) + " " + "" )
```

**Also changed in GNURadioDeviceFlowgraph.grc:**
```diff
-      <value>hackrf=0</value>
+      <value></value>
```

**Commit SHA:** `b79f25dbde448ed6da4099e9fad868724d34cba5`

---

## What This Means

### HackRF Support Timeline

```
Aug 15, 2020    Video uploaded, HackRF support promised
    |
    v
~2020-2021      HackRF support EXISTS via 'hackrf=0' in GNU Radio
    |
    v
Jun 22, 2021    McLean REMOVES HackRF-specific code (commit b79f25d)
    |
    v
Oct 29, 2023    Last commit - still no HackRF
    |
    v
Jan 2025        Code search finds zero HackRF references
```

### Why Was HackRF Support Removed?

The commit message reveals the reason:
> "so that other devices are detected and used"

**Technical Explanation:**

The `hackrf=0` argument told osmosdr to **only** use the first HackRF device. This caused problems:
1. Users without HackRF couldn't use the flowgraph
2. Auto-detection of other SDR devices was disabled
3. It forced everyone to have HackRF

By removing `hackrf=0` and leaving empty args `""`, osmosdr now:
1. Auto-detects any connected SDR (RTL-SDR, HackRF, Airspy, etc.)
2. Works for users with any osmosdr-compatible device
3. Is more flexible but less explicit

**The Irony:** McLean removed HackRF support to make the software work for MORE devices, including HackRF via auto-detection. But this also means HackRF is no longer explicitly supported.

---

## Complete Commit History Analysis

### SDRReradiationSpectrumAnalyzer Timeline

| Date | Commit | Significance |
|------|--------|--------------|
| Mar 10, 2021 | Initial commit | Repo created |
| Apr 22, 2021 | GNU Radio integration | `hackrf=0` added |
| **Jun 22, 2021** | **b79f25d** | **HackRF support REMOVED** |
| Jun 22, 2021 | Launch files updated | 400-500 MHz range set |
| Oct 29, 2023 | Last commit | RF Power detection |

### SDRSpectrumAnalyzer Timeline

| Date | Commit | Significance |
|------|--------|--------------|
| May 30, 2019 | Last commit | Waterfall bug fix |

The original SDRSpectrumAnalyzer (C#, Windows-only) was **abandoned in 2019**, before the HackRF claim was ever made.

---

## Fork Analysis

### Community Forks (No HackRF Additions)

| Fork | Owner | Created | HackRF Changes |
|------|-------|---------|----------------|
| Felssca | @Felssca | Nov 2023 | None - exact copy |
| centexmsp | @centexmsp | Jul 2025 | None - exact copy |

Neither fork has attempted to restore or improve HackRF support.

---

## Technical Architecture

### How HackRF Support Worked (When It Existed)

```
[HackRF Hardware]
       |
       v
[osmosdr driver with hackrf=0 argument]
       |
       v
[GNU Radio flowgraph (top_block.py)]
       |
       v
[UDP stream to port 4321]
       |
       v
[SDRReradiationSpectrumAnalyzer]
```

### How It Works Now (After Removal)

```
[Any osmosdr-compatible SDR]
       |
       v
[osmosdr driver with auto-detection]
       |
       v
[GNU Radio flowgraph (top_block.py)]
       |
       v
[UDP stream to port 4321]
       |
       v
[SDRReradiationSpectrumAnalyzer]
```

**Key Difference:** HackRF still works, but via auto-detection rather than explicit targeting.

---

## Why This Matters

### The Narrative Changes

| Original Assumption | Actual Reality |
|---------------------|----------------|
| HackRF support never implemented | HackRF support existed, then removed |
| McLean couldn't figure out HackRF | McLean chose device-agnostic approach |
| Promise broken | Promise fulfilled differently |

### The Real Story

McLean **did** implement HackRF support. He then **chose** to remove explicit HackRF targeting in favor of generic device auto-detection. This was a **design decision**, not a failure to implement.

The flowgraph now supports:
- RTL-SDR (auto-detected)
- HackRF (auto-detected)
- Airspy (auto-detected)
- Any osmosdr-compatible device

---

## Native Support Still Missing

Despite the GNU Radio flowgraph supporting HackRF via auto-detection, the C/C++ analyzer itself still only natively supports RTL-SDR.

**DeviceReceiver.cpp** remains tightly coupled to librtlsdr:
```cpp
rtlsdr_set_dithering(device, 1);
rtlsdr_set_gpio(device, 0, 1);
rtlsdr_set_center_freq(device, freq);
```

For true native HackRF support (without GNU Radio), you would need:
1. Add libhackrf as a dependency
2. Create device abstraction layer
3. Handle sample rate differences
4. Handle multi-stage gain control

This was never done and probably never will be.

---

## Current Status (January 2025)

| Feature | Status | Notes |
|---------|--------|-------|
| RTL-SDR Native | Implemented | Direct librtlsdr integration |
| HackRF Native | Not implemented | Would require major refactoring |
| HackRF via GNU Radio | Works | Auto-detected by osmosdr |
| Explicit HackRF targeting | Removed | Was `hackrf=0`, now auto-detect |

---

## Practical Recommendations

### If You Have HackRF

1. **Use the GNU Radio flowgraph** - it will auto-detect your HackRF
2. Connect HackRF via USB
3. Launch `GNURadioDeviceFlowgraph.grc`
4. Run the analyzer with GNU Radio mode

### If You Have RTL-SDR

1. **Use native support** - it's simpler and better supported
2. Direct USB connection works without GNU Radio
3. Better documentation and community support

### Cost-Benefit Analysis

| Approach | Cost | Complexity | Works? |
|----------|------|------------|--------|
| RTL-SDR native | $35 | Low | Yes |
| HackRF via GNU Radio | $200+ | Medium | Yes |
| HackRF native | N/A | N/A | No |

---

## Conclusion

The HackRF investigation reveals a nuanced story:

1. **McLean did implement HackRF support** - via `hackrf=0` in GNU Radio
2. **He then removed it** - to enable generic device auto-detection
3. **HackRF still works** - via osmosdr auto-detection
4. **Native support never existed** - only GNU Radio bridge approach

The claim wasn't broken—it was fulfilled via GNU Radio, then modified for broader compatibility. The current software supports HackRF through auto-detection, just not explicitly.

**The real lesson:** Software evolution is complex. What looks like an abandoned promise may actually be a design decision for broader compatibility.

---

## Evidence Files

| File | Evidence |
|------|----------|
| `GNURadioDeviceFlowgraph/top_block.py` | Empty device args (was `hackrf=0`) |
| `GNURadioDeviceFlowgraph/GNURadioDeviceFlowgraph.grc` | Empty args value |
| Commit `b79f25d` | Explicit removal commit |
| `SDRReradiation/DeviceReceiver.cpp` | RTL-SDR coupling |

---

## Complete Commit Diff (b79f25d)

For reference, here is the complete diff from the HackRF removal commit:

```diff
commit b79f25dbde448ed6da4099e9fad868724d34cba5
Author: clintmclean74 <clintmclean74@gmail.com>
Date:   Tue Jun 22 18:47:19 2021 +0200

    Removed "hackrf=0", used to specify a HackRF device, from the GNU
    radio flowgraph so that other devices are detected and used.

diff --git a/GNURadioDeviceFlowgraph/GNURadioDeviceFlowgraph.grc
--- a/GNURadioDeviceFlowgraph/GNURadioDeviceFlowgraph.grc
+++ b/GNURadioDeviceFlowgraph/GNURadioDeviceFlowgraph.grc
@@ -1729,7 +1729,7 @@
     <param>
       <key>args</key>
-      <value>hackrf=0</value>
+      <value></value>
     </param>

diff --git a/GNURadioDeviceFlowgraph/top_block.py
--- a/GNURadioDeviceFlowgraph/top_block.py
+++ b/GNURadioDeviceFlowgraph/top_block.py
@@ -105,7 +105,7 @@
-        self.osmosdr_source_0 = osmosdr.source( args="numchan=" + str(1) + " " + 'hackrf=0' )
+        self.osmosdr_source_0 = osmosdr.source( args="numchan=" + str(1) + " " + "" )
```

---

*Deep investigation completed January 2025*
*Commit evidence verified via git history*
