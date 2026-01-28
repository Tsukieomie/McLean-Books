# Equipment Guide for RF Detection

A comprehensive guide to hardware and software for replicating Clint McLean's RF detection methodology.

---

## Table of Contents

1. [Quick Start Budget](#quick-start-budget)
2. [SDR Receivers](#sdr-receivers)
   - [RTL-SDR](#rtl-sdr-35)
   - [HackRF One](#hackrf-one-70-200)
   - [Portapack H4M+](#portapack-h4m-with-hackrf-150-250)
3. [Low Noise Amplifiers (LNA)](#low-noise-amplifiers-lna)
4. [Antennas](#antennas)
5. [DIY 450MHz Yagi Antenna](#diy-450mhz-yagi-antenna)
6. [EMF Meters](#emf-meters)
7. [Software](#software)
8. [HackRF Support Status](#hackrf-support-status)
9. [Complete Setup Configurations](#complete-setup-configurations)

---

## Quick Start Budget

| Budget | Configuration | Components | Computer Needed? |
|--------|---------------|------------|------------------|
| **~$50** | Minimum | RTL-SDR + telescoping antenna | Yes |
| **~$100** | Recommended | RTL-SDR + commercial Yagi | Yes |
| **~$150** | Portable | **Portapack H4M+** (standalone) | **No** |
| **~$200** | Portable+ | Portapack H4M+ + Yagi | **No** |
| **~$250** | Advanced | HackRF One + Yagi + NanoVNA | Yes |

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

### Portapack H4M+ with HackRF (~$150-250)

**Best standalone option - no computer required in the field.**

The Portapack H4M+ is an add-on board that transforms HackRF One into a fully portable, standalone device with built-in display and spectrum analyzer.

| Spec | Value |
|------|-------|
| Frequency Range | 1 MHz - 6 GHz |
| Display | 3.2" matte touchscreen (240x320) |
| Battery | 2500 mAh lithium (built-in) |
| Operation | Standalone or USB-connected |
| Firmware | Mayhem (pre-installed) |
| Audio | Built-in speaker + mic |
| Storage | MicroSD slot (card not included) |

**Where to Buy:**

| Retailer | Product | Price |
|----------|---------|-------|
| [Amazon (SUOGOEST)](https://www.amazon.com/SUOGOEST-Signature-Transparent-Electronics-Engineering/dp/B0FJF8JSNY/) | H4M+ Mayhem Edition | ~$150 |
| [OpenSourceSDRLab](https://opensourcesdrlab.com/products/h4m-receiver-and-spectrum-analyzer) | H4M+ Kit | ~$150-200 |
| [Lab401](https://lab401.com/products/portapack-h4m) | H4M + HackRF Bundle | ~$300 |
| [Hacker Warehouse](https://hackerwarehouse.com/product/hackrf-portapack-h4m-combo/) | H4M Combo | ~$250 |

**What's Included (typical kit):**

| Item | Purpose |
|------|---------|
| Portapack H4M | Main unit with display |
| HackRF One R10C | Built-in SDR transceiver |
| Transparent shell | Protective case |
| 20dB LNA | Low noise amplifier (50 MHz - 6 GHz) |
| Telescopic antenna | 40 MHz - 6 GHz general purpose |
| GSM/3G/4G antenna | Cellular bands |
| 2.4/5/5.8 GHz blade | WiFi/Bluetooth |
| 700-2700 MHz whip | UHF/cellular |
| SMA cable | LNA connection |
| USB-C cable | Charging/data |

**Mayhem Firmware Features:**

| Feature | Description |
|---------|-------------|
| Spectrum Analyzer | Real-time RF visualization |
| Signal Scanner | Auto-scan frequency ranges |
| Audio RX | AM/FM/SSB demodulation |
| Replay Attack | Record and replay RF signals |
| Signal Generator | Create test signals |
| ADS-B/AIS | Aircraft and ship tracking |
| POCSAG/Weather | Pager and weather decoding |

**For McLean's Detection Method:**

| Aspect | Assessment |
|--------|------------|
| 400-500 MHz coverage | **Yes** - fully covered |
| Spectrum analysis | **Built-in** on device |
| Portability | **Excellent** - walk around while monitoring |
| McLean's software | **No** - won't run his software directly |
| Alternative approach | Use built-in spectrum analyzer |

**Pros:**
- Fully portable (no laptop needed)
- Built-in spectrum analyzer
- Large touchscreen display
- Battery powered
- Multiple antennas included
- LNA for weak signal boost

**Cons:**
- Won't run McLean's specific software
- More complex than RTL-SDR
- Requires MicroSD card (not included)
- Overkill for basic detection

**Quick Start for Reradiation Detection:**

1. Charge fully via USB-C
2. Insert MicroSD card (32GB+ recommended)
3. Power on (side button)
4. Navigate: **Receive → Spectrum**
5. Set frequency range: 400-500 MHz
6. Attach telescopic antenna
7. Enable LNA if signals are weak
8. Walk around and observe signal changes

**Tip:** The included telescopic antenna covers 400-500 MHz. For directional detection like McLean demonstrated, add a UHF Yagi antenna (~$30-60).

---

## Low Noise Amplifiers (LNA)

### Why LNA Matters

An LNA (Low Noise Amplifier) placed near the antenna can **significantly improve weak signal detection** by amplifying signals before noise is introduced by cables and the SDR's internal electronics.

### The Sensitivity Problem

| SDR | Noise Figure (alone) | Sensitivity |
|-----|----------------------|-------------|
| RTL-SDR | ~6-8 dB | Good |
| HackRF One | ~10-12 dB | Poor |
| HackRF + 20dB LNA | ~2-3 dB | **Excellent** |

**Key insight:** HackRF alone is worse than RTL-SDR for sensitivity, but **HackRF + LNA beats RTL-SDR**.

### Portapack H4M+ Included LNA

Your kit includes a **20dB LNA (50 MHz - 6 GHz)**. This changes the equation:

| Setup | Noise Figure | vs RTL-SDR |
|-------|--------------|------------|
| HackRF alone | ~10-12 dB | **Worse** |
| HackRF + 20dB LNA | ~2-3 dB | **Better** |
| RTL-SDR alone | ~6-8 dB | Baseline |
| RTL-SDR + LNA | ~1-2 dB | Best |

**Expected improvement with LNA: 6-9 dB** (significant for weak signal detection)

### Optimal LNA Placement

```
BEST:   [Antenna] → [LNA] → [Cable] → [SDR]
                      ↑
              Close to antenna

WORST:  [Antenna] → [Cable] → [LNA] → [SDR]
                                 ↑
                    Signal already degraded
```

**Rule:** Place LNA as close to the antenna as possible.

### Recommended Setup for 400-500 MHz

**Optimal (with bandpass filter):**
```
[Yagi] → [400-500 MHz Bandpass Filter] → [20dB LNA] → [Portapack]
```

**Standard (what's included):**
```
[Telescopic Antenna] → [20dB LNA] → [Portapack]
```

### When to Use LNA

| Scenario | Use LNA? | Reason |
|----------|----------|--------|
| Hunting weak reradiation signals | **Yes** | Improves sensitivity |
| Long antenna cable (>3m) | **Yes** | Compensates for cable loss |
| Rural/quiet RF environment | **Yes** | Maximize weak signal detection |
| Urban/strong signal environment | **No** | Risk of overload |
| Near cell towers/transmitters | **No** | Risk of saturation/damage |

### LNA Safety Warnings

| Risk | Details | Prevention |
|------|---------|------------|
| **Overload** | HackRF input damage at +13 dBm | Remove LNA near strong signals |
| **Saturation** | Display clips/distorts | Reduce gain or remove LNA |
| **Interference** | LNA amplifies ALL signals | Use bandpass filter |

**From [GPIO Labs](https://gpio.com/blogs/news/amplifier-for-hackrf):**
> "An LNA will amplify all signals present at its input... Use a band pass filter to block strong out-of-band signals."

### Where to Buy Additional LNAs

| Product | Frequency | Gain | Price |
|---------|-----------|------|-------|
| [Nooelec Lana](https://www.nooelec.com/store/lana.html) | 20 MHz - 4 GHz | 20 dB | ~$25 |
| [RTL-SDR Blog LNA](https://www.rtl-sdr.com/buy-rtl-sdr-dvb-t-dongles/) | Wideband | 20 dB | ~$20 |
| [GPIO Labs LNA](https://gpio.com/products/low-noise-amplifier-10-6000-mhz-gain-20-db) | 10 MHz - 6 GHz | 20 dB | ~$35 |

### Quick Start: Using Your Included LNA

1. **Test without LNA first** - Check for strong signals
2. **Connect:** Antenna → LNA → SMA cable → Portapack
3. **Power:** LNA via USB or Portapack bias-T (if supported)
4. **Monitor:** Watch for signal improvement
5. **If saturated:** Remove LNA, environment too noisy

### Bottom Line

| Configuration | Weak Signal Performance | Cost |
|---------------|------------------------|------|
| RTL-SDR alone | Good | $35 |
| HackRF alone | Poor | $150+ |
| **HackRF + LNA (your setup)** | **Excellent** | $150+ (LNA included) |

Your Portapack H4M+ with the included 20dB LNA is **legitimately better** than standalone RTL-SDR for weak signal detection like McLean's reradiation method.

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
