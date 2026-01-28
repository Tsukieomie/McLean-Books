# Equipment Guide for RF Detection

A comprehensive guide to hardware and software for replicating Clint McLean's RF detection methodology.

---

## Table of Contents

1. [Quick Start Budget](#quick-start-budget)
2. [SDR Receivers](#sdr-receivers)
3. [Antennas](#antennas)
4. [DIY 450MHz Yagi Antenna](#diy-450mhz-yagi-antenna)
5. [EMF Meters](#emf-meters)
6. [Software](#software)
7. [HackRF Support Status](#hackrf-support-status)
8. [Complete Setup Configurations](#complete-setup-configurations)

---

## Quick Start Budget

| Budget | Configuration | Components |
|--------|---------------|------------|
| **~$50** | Minimum | RTL-SDR + telescoping antenna |
| **~$100** | Recommended | RTL-SDR + commercial Yagi |
| **~$150** | Better | RTL-SDR + Yagi + NanoVNA |
| **~$250** | Advanced | HackRF One + Yagi + NanoVNA |

---

## SDR Receivers

### RTL-SDR (~$35)

**McLean's primary recommendation for beginners.**

| Spec | Value |
|------|-------|
| Frequency Range | 25 MHz - 1.7 GHz |
| Sample Rate | Up to 2.4 MS/s |
| Resolution | 8-bit |
| Operation | Receive only |
| Connection | USB 2.0 |

**Where to Buy:**
- [RTL-SDR.com](https://www.rtl-sdr.com/buy-rtl-sdr-dvb-t-dongles/) - ~$35 with antennas

**Pros:**
- Affordable entry point
- Well-documented
- Works with McLean's software directly

**Cons:**
- Limited frequency range (misses some ranges)
- Receive only (no TX capability)
- Lower sensitivity than HackRF

---

### HackRF One (~$70-200)

**McLean's recommended upgrade - "10x better than RTL-SDR"**

| Spec | Value |
|------|-------|
| Frequency Range | **1 MHz - 6 GHz** |
| Sample Rate | Up to 20 MS/s |
| Bandwidth | 20 MHz |
| Resolution | 8-bit quadrature |
| Operation | **TX and RX** (half-duplex) |
| Max TX Power | Up to 15 dBm |
| Connection | USB 2.0 |

**Where to Buy:**

| Retailer | Product | Price |
|----------|---------|-------|
| [Great Scott Gadgets](https://greatscottgadgets.com/hackrf/one/) | Official HackRF One | ~$350 |
| [Amazon (Nooelec)](https://www.amazon.com/Software-1MHz-6GHz-Frequency-Bandwidth-Adapters/dp/B0BKH7Z2NJ) | HackRF + ANT500 Bundle | ~$200 |
| [HamGeek](https://www.hgeek.com/products/hamgeek-hackrf-one-r9-v2-0-0-1mhz-6ghz-software-defined-radio-platform-gps-simulator-w-shell-4-antennas) | HackRF R9 V2.0.0 + Antennas | ~$70-100 |
| [Lab401](https://lab401.com/products/hackrf-one) | HackRF One Rev 10 | ~$350 |
| AliExpress (various) | Clone/compatible versions | ~$70 |

**Analysis of "10x Better" Claim:**

McLean claimed HackRF is "10x better" but this is misleading. Here's the reality:

| Specification | RTL-SDR | HackRF One | Ratio | Notes |
|---------------|---------|------------|-------|-------|
| Frequency Range | 25 MHz - 1.7 GHz | 1 MHz - 6 GHz | ~3.5x | HackRF wins |
| **Bandwidth** | 2.4 MHz | 20 MHz | **~8x** | Likely source of "10x" claim |
| **Sample Rate** | 2.4 MS/s | 20 MS/s | **~8x** | Likely source of "10x" claim |
| ADC Resolution | 8-bit | 8-bit | 1x | **Same** |
| Dynamic Range | ~48 dB | ~48-52 dB | ~1x | **Nearly identical** |
| Sensitivity | Good | Similar/Worse | ~1x | **RTL-SDR often better** |
| TX Capability | No | Yes | N/A | HackRF only |
| Price | ~$35 | $70-350 | 2-10x | RTL-SDR much cheaper |

**Where "10x" Comes From:**
- **Bandwidth (8x)** - 20 MHz vs 2.4 MHz (rounded to 10x)
- **Sample rate (8x)** - 20 MS/s vs 2.4 MS/s

**What's NOT 10x Better:**
- **Sensitivity** - Actually similar or WORSE than RTL-SDR in many tests
- **Dynamic range** - Both ~48 dB (8-bit ADC limitation)
- **Noise floor** - Both have similar noise performance

**Expert Opinion ([rtl-sdr.com](https://www.rtl-sdr.com/hackrf-initial-review/)):**
> "Overall reception sensitivity seems to be very similar to the RTL-SDR."
> "The HackRF has no front end filtering (preselectors) so there are many images of strong signals."

**Bottom Line:** HackRF has ~8x more bandwidth, but NOT better sensitivity. For McLean's reradiation detection (narrowband signals at 400-500 MHz), RTL-SDR is equally effective and 10x cheaper

---

## Antennas

### Commercial Yagi Antenna (~$59)

McLean used a Yagi antenna for directional detection in his video.

| Spec | Value |
|------|-------|
| Type | Directional (Yagi-Uda) |
| Target Frequency | 400-500 MHz range |
| Gain | Typically 7-12 dBi |
| Connector | Usually SMA or N-type |

**Where to Buy:**
- AliExpress - Search "UHF Yagi antenna 400-500MHz" (~$59)
- Amazon - Various options available

---

### DIY 450MHz Yagi Antenna

**From @jafinch78's comment - Build your own for ~$20-30**

**Instructables Guide:** https://www.instructables.com/id/-450MHz-Yagi-Antenna/

#### Why 450MHz?

The 450MHz frequency is directly within the **adult head resonant frequency band (400-500 MHz)** that McLean targets. Building a Yagi tuned to this range provides:

- Optimal reception of human resonant frequencies
- Directional detection capability
- Cost savings vs commercial antennas

#### Materials Needed

| Material | Purpose | Approximate Cost |
|----------|---------|------------------|
| Aluminum tubing/rods | Antenna elements | ~$10-15 |
| Wooden dowel or PVC pipe | Boom | ~$5 |
| Coax cable + connector | Feed line | ~$5-10 |
| 3D printed mounts (optional) | Element positioning | Free if you have printer |
| NanoVNA (recommended) | Tuning verification | ~$50-60 |

#### Build Process Overview

```
Step 1: Calculate Dimensions
├── Use Yagi calculator: http://www.k7mem.com/Ant_Yagi_VHF_Quick.html
├── Enter target frequency (450 MHz)
└── Get element lengths and spacing

Step 2: Cut Elements
├── Reflector (longest)
├── Driven element (connects to coax)
└── Directors (shortest, can have multiple)

Step 3: Mount Elements
├── Use non-conductive spacers (~4mm above boom)
├── Keep elements parallel
└── Maintain calculated spacing

Step 4: Connect Feed
├── Connect coax to driven element center
└── Use balun if needed

Step 5: Tune & Test
├── Use NanoVNA to check SWR
├── Adjust element lengths if needed
└── Target SWR < 1.5:1 at 450MHz
```

#### Additional DIY Resources

| Resource | Link |
|----------|------|
| Yagi Dimension Calculator | http://www.k7mem.com/Ant_Yagi_VHF_Quick.html |
| DIY 70cm Yagi Tutorial 1 | https://www.youtube.com/watch?v=kWJncnhc7Z4 |
| DIY 70cm Yagi Tutorial 2 | https://www.youtube.com/watch?v=1Wl6Cy4ovig |
| Instructables 450MHz Yagi | https://www.instructables.com/id/-450MHz-Yagi-Antenna/ |

---

### NanoVNA Antenna Analyzer (~$50-60)

**Highly recommended for DIY antenna building and verification.**

| Spec | Value |
|------|-------|
| Frequency Range | 50 kHz - 3 GHz (NanoVNA-H4) |
| Measurements | SWR, impedance, S-parameters |
| Display | Built-in touchscreen |
| Connection | USB for PC software |

**Use Cases:**
- Verify antenna is tuned to correct frequency
- Measure SWR (Standing Wave Ratio)
- Troubleshoot antenna issues
- Compare commercial vs DIY performance

---

## EMF Meters

*From @policedog4030's video comment - additional detection equipment*

| Meter | Type | Notes |
|-------|------|-------|
| **GQ-EMF 380** | EMF Meter | General purpose |
| **GQ-EMF 390** | EMF Meter | More features |
| **GQ-GMC-600+** | Geiger-Muller | Radiation detection |
| **TriField EMF Meter** | EMF Meter | "Chickenhead knob" model |

**Note:** These are supplementary to SDR detection, not replacements. They can detect strong EMF presence but lack the spectral analysis capability of SDR systems.

---

## Software

### McLean's Software

#### SDRSpectrumAnalyzer (Original)

| Attribute | Value |
|-----------|-------|
| Language | C# |
| Platform | Windows |
| SDR Support | RTL-SDR |
| Last Updated | May 2019 |
| Status | Stable, original version |

**Repository:** https://github.com/ClintMclean74/SDRSpectrumAnalyzer

**User Guide:** https://drive.google.com/open?id=1Sc6_Tbxux-O5aAFY-gAXCkrgMpNiRkjv

---

#### SDRReradiationSpectrumAnalyzer (Advanced)

| Attribute | Value |
|-----------|-------|
| Language | C |
| Platform | **Windows and Linux** |
| SDR Support | RTL-SDR, GNU Radio devices |
| Last Updated | October 2023 |
| Status | Active development |

**Repository:** https://github.com/ClintMclean74/SDRReradiationSpectrumAnalyzer

**Features:**
- 3D visualization
- Automated reradiation detection
- Session-based scanning
- GNU Radio device support via flowgraph

**Research Paper:** https://drive.google.com/file/d/1Kyl0xJq4ndh9y6mQPjucHfqSpRKAETyK/view

---

### Alternative Software

| Software | Platform | SDR Support | Use Case |
|----------|----------|-------------|----------|
| **SDR#** (SDRSharp) | Windows | RTL-SDR, HackRF, many others | General spectrum analysis |
| **GQRX** | Linux/macOS | RTL-SDR, HackRF | Open source alternative |
| **GNU Radio** | Cross-platform | Most SDRs | Advanced signal processing |
| **CubicSDR** | Cross-platform | RTL-SDR, HackRF | Cross-platform GUI |

---

## HackRF Support Status

### Investigation Findings

**Status: PLANNED BUT NOT IMPLEMENTED**

McLean stated in his August 2020 video description:

> "Preferably though you should get the HackRF... I'm going to be modifying the code system that I wrote to also use these."

#### Code Repository Analysis

| Repository | Last Commit | HackRF Code Found |
|------------|-------------|-------------------|
| SDRSpectrumAnalyzer | May 2019 | **No** |
| SDRReradiationSpectrumAnalyzer | October 2023 | **No** |

**GitHub Code Search Results:** Zero results for "hackrf" in either repository.

#### Conclusion

As of the latest commits (October 2023), **native HackRF support has NOT been implemented** in McLean's software. The feature was mentioned as planned but never materialized.

---

### GNU Radio Workaround

The **SDRReradiationSpectrumAnalyzer** does support GNU Radio devices via flowgraph, which could theoretically connect to HackRF:

```
HackRF → GNU Radio Flowgraph → SDRReradiationSpectrumAnalyzer
```

**From the README:**
> "To connect a compatible device using GNU Radio first launch the flowgraph GNURadioDeviceFlowgraph.grc (in the GNURadioDeviceFlowgraph folder) and then the launch files."

**Steps to try:**
1. Install GNU Radio with HackRF support (`gr-osmosdr`)
2. Modify `GNURadioDeviceFlowgraph.grc` to use HackRF as source
3. Run the flowgraph, then launch SDRReradiationSpectrumAnalyzer

**Note:** This is untested and may require additional configuration.

---

### Alternative: Use HackRF with Other Software

If you have a HackRF, you can still perform spectrum analysis using:

| Software | HackRF Support | Notes |
|----------|----------------|-------|
| **SDR#** | Yes (via ExtIO plugin) | Windows, good spectrum view |
| **GQRX** | Yes (native) | Linux/macOS |
| **GNU Radio** | Yes (native) | Full signal processing |
| **Spectrum Analyzer (HackRF)** | Yes | Built-in HackRF firmware mode |

You would lose McLean's specialized reradiation detection features but gain wider frequency coverage.

---

## Complete Setup Configurations

### Configuration 1: Budget Beginner (~$100)

```
┌─────────────────────────────────────────────────┐
│ RTL-SDR V3 (~$35)                               │
│     │                                            │
│     └──► Commercial 450MHz Yagi (~$59)          │
│              │                                   │
│              └──► Laptop with McLean's software │
└─────────────────────────────────────────────────┘
```

**Software:** SDRSpectrumAnalyzer or SDRReradiationSpectrumAnalyzer

---

### Configuration 2: DIY Enthusiast (~$150)

```
┌─────────────────────────────────────────────────┐
│ RTL-SDR V3 (~$35)                               │
│     │                                            │
│     └──► DIY 450MHz Yagi (~$20-30)              │
│              │                                   │
│              ├──► NanoVNA for tuning (~$50-60)  │
│              │                                   │
│              └──► Laptop with McLean's software │
└─────────────────────────────────────────────────┘
```

---

### Configuration 3: Advanced Research (~$250+)

```
┌─────────────────────────────────────────────────┐
│ HackRF One (~$70-200)                           │
│     │                                            │
│     └──► Commercial/DIY Yagi                    │
│              │                                   │
│              ├──► NanoVNA for tuning            │
│              │                                   │
│              └──► GNU Radio + GQRX/SDR#         │
│                   (since McLean's software      │
│                    doesn't support HackRF)      │
└─────────────────────────────────────────────────┘
```

---

### Configuration 4: Comprehensive Detection

*Inspired by @policedog4030's setup*

```
┌─────────────────────────────────────────────────┐
│ Primary: RTL-SDR + Yagi + McLean's Software     │
│                                                  │
│ Secondary: EMF Meters for environmental scan    │
│     ├── GQ-EMF 390                              │
│     └── TriField EMF Meter                      │
│                                                  │
│ Documentation: Camera aligned with antenna      │
│                Screen recording software        │
└─────────────────────────────────────────────────┘
```

---

## Summary Recommendations

| User Type | Recommendation |
|-----------|----------------|
| **Complete Beginner** | RTL-SDR + telescoping antenna → Learn basics first |
| **Serious Experimenter** | RTL-SDR + commercial Yagi → McLean's software |
| **DIY Enthusiast** | RTL-SDR + DIY Yagi + NanoVNA → Full control |
| **Advanced Researcher** | HackRF + Yagi → GNU Radio (wider range, but no McLean software) |

---

## Key Takeaways

1. **RTL-SDR is sufficient** for replicating McLean's experiments exactly as shown
2. **HackRF is better hardware** but McLean's specialized software doesn't support it
3. **DIY Yagi** can match commercial performance if properly tuned
4. **450MHz target frequency** is optimal for adult head resonance detection
5. **GNU Radio workaround** may allow HackRF use with SDRReradiationSpectrumAnalyzer

---

*Equipment guide compiled from McLean's video, book, and community feedback*
*Prices approximate as of January 2026*
