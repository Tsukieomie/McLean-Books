# Methods for Detecting Biology Affecting Electromagnetic Frequency Ranges Causing Havana Syndrome

**Author:** Clint McLean

---

<a id="toc"></a>
## Table of Contents

1. [Abstract](#abstract)
2. [Introduction](#introduction)
3. [Methods](#methods)
   - [2.1 Hypothesis](#hypothesis)
   - [2.2 Equipment and Setup](#equipment)
   - [2.3 SDR Software Configuration](#sdr-config)
   - [2.4 Detection Methodology](#detection-methodology)
4. [Results](#results)
   - [3.1 Initial Scans](#initial-scans)
   - [3.2 433 MHz Detection](#433-detection)
   - [3.3 Signal Analysis](#signal-analysis)
5. [Discussion](#discussion)
   - [4.1 Cazzamalli's Historical Research](#cazzamalli)
   - [4.2 Bio-Radar Principles](#bio-radar)
   - [4.3 Remote Neural Monitoring](#rnm)
   - [4.4 Implications for Havana Syndrome](#implications)
6. [Conclusion](#conclusion)
7. [References](#references)
8. [Figures](#figures-index)

---

<a id="abstract"></a>
## Abstract

This paper presents methods for detecting electromagnetic frequencies that may affect human biology, specifically in the context of Havana Syndrome. Using Software Defined Radio (SDR) technology and spectrum analysis, we investigate the detection of reradiated electromagnetic signals from biological targets. The methodology draws upon historical research by Cazzamalli on brain radio signals and modern understanding of bio-radar technology. Results demonstrate detection of signals at 433 MHz that correlate with known ISM band frequencies used in various electronic devices and potentially in directed energy systems.

[↑ Back to Table of Contents](#toc)

---

<a id="introduction"></a>
## 1. Introduction

Havana Syndrome refers to a set of medical symptoms reported by U.S. and Canadian embassy staff, first in Havana, Cuba in late 2016, and subsequently in other locations worldwide. Symptoms include hearing unusual sounds, headaches, memory loss, nausea, and brain injuries consistent with traumatic brain injury without physical impact.

The cause of Havana Syndrome remains officially unexplained, though theories include microwave weapons, sonic devices, pesticides, or psychogenic factors. This paper focuses on the electromagnetic (EM) hypothesis and presents methods for detecting EM frequencies that could potentially affect human biology.

<a id="figure-1"></a>
![Figure 1: Cazzamalli's Experiment Setup](figures/fig-001.png)
*Figure 1: Cazzamalli's experimental apparatus for detecting brain radio emissions (1920s)*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

The historical research of Dr. Ferdinando Cazzamalli in the 1920s and 1930s provides foundational understanding of how electromagnetic waves interact with the human brain. Cazzamalli demonstrated that the brain could reradiate electromagnetic signals when exposed to certain frequencies, creating what he termed "brain radio."

Understanding these interactions is critical for:
- Detecting potential directed energy attacks
- Developing countermeasures and shielding
- Establishing forensic evidence of EM exposure
- Advancing our understanding of bioelectromagnetic phenomena

[↑ Back to Table of Contents](#toc)

---

<a id="methods"></a>
## 2. Methods

<a id="hypothesis"></a>
### 2.1 Hypothesis

Based on the bio-radar principle and Cazzamalli's research, we hypothesize that:

1. Human tissue acts as a resonant cavity for certain electromagnetic frequencies
2. When illuminated by RF energy at resonant frequencies, the body reradiates detectable signals
3. These reradiated signals can be detected using SDR technology
4. The frequency range of interest is approximately 300 MHz to 3 GHz (UHF band)

<a id="figure-2"></a>
![Figure 2: RF Transmission and Reception Concept](figures/fig-002.png)
*Figure 2: Conceptual diagram of RF transmission to and reception from biological target*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

<a id="equipment"></a>
### 2.2 Equipment and Setup

The following equipment was used for detection experiments:

**Hardware:**
- RTL-SDR Blog V3 dongle (RTL2832U + R820T2)
- Various antennas (dipole, discone, log-periodic)
- USB extension cables for antenna positioning
- Laptop computer (Windows/Linux)
- Faraday cage materials for baseline measurements

**Software:**
- SDR# (SDRSharp) for Windows
- GQRX for Linux
- GNU Radio for advanced signal processing
- Spectrum analyzer plugins

<a id="figure-3"></a>
![Figure 3: SDR Equipment Setup](figures/fig-003.png)
*Figure 3: RTL-SDR dongle and antenna configuration*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

<a id="sdr-config"></a>
### 2.3 SDR Software Configuration

SDR# was configured with the following parameters for initial scanning:

| Parameter | Value |
|-----------|-------|
| Sample Rate | 2.4 MSPS |
| RF Gain | Auto/Manual adjustment |
| FFT Resolution | 32768 |
| Averaging | 10 frames |
| Frequency Range | 24 MHz - 1.7 GHz |

<a id="figure-4"></a>
![Figure 4: SDR# Interface](figures/fig-004.png)
*Figure 4: SDR# software interface showing spectrum analyzer and waterfall display*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

<a id="detection-methodology"></a>
### 2.4 Detection Methodology

The detection methodology follows these steps:

1. **Baseline Measurement**: Record ambient RF spectrum with no subject present
2. **Subject Introduction**: Position subject near receiving antenna
3. **Comparative Analysis**: Compare spectra with and without subject
4. **Frequency Sweeping**: Systematically scan frequency bands of interest
5. **Signal Characterization**: Analyze detected signals for modulation, bandwidth, and temporal patterns

<a id="figure-5"></a>
![Figure 5: Detection Protocol Flowchart](figures/fig-005.png)
*Figure 5: Flowchart showing the systematic detection protocol*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

Key frequencies of interest based on literature review:

- **433 MHz**: ISM band (Europe), common for remote controls and sensors
- **915 MHz**: ISM band (Americas), RFID systems
- **2.4 GHz**: WiFi, Bluetooth, microwave ovens
- **Resonant frequencies**: Calculated based on body dimensions (~400-700 MHz)

[↑ Back to Table of Contents](#toc)

---

<a id="results"></a>
## 3. Results

<a id="initial-scans"></a>
### 3.1 Initial Scans

Initial wideband scans revealed the typical urban RF environment with expected signals from:
- FM radio (88-108 MHz)
- Television broadcasts
- Cellular networks (700, 850, 1900 MHz)
- WiFi (2.4 GHz)
- Various ISM band devices

<a id="figure-6"></a>
![Figure 6: Wideband Spectrum Scan](figures/fig-006.png)
*Figure 6: Wideband spectrum showing typical urban RF environment*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

<a id="433-detection"></a>
### 3.2 433 MHz Detection

Focused scanning at 433 MHz revealed interesting signals that correlated with subject presence:

<a id="figure-7"></a>
![Figure 7: 433 MHz Spectrum Detail](figures/fig-007.png)
*Figure 7: Detailed spectrum view centered on 433 MHz*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

The 433 MHz ISM band showed:
- Periodic burst transmissions
- Signal strength variations correlating with subject movement
- Modulation patterns consistent with bio-radar returns

<a id="figure-8"></a>
![Figure 8: 433 MHz Signal with Subject Present](figures/fig-008.png)
*Figure 8: Signal detected at 433 MHz with subject in proximity to antenna*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

<a id="signal-analysis"></a>
### 3.3 Signal Analysis

Detailed analysis of detected signals revealed:

| Measurement | Value |
|-------------|-------|
| Center Frequency | 433.92 MHz |
| Bandwidth | ~50 kHz |
| Signal Strength | -45 to -65 dBm |
| Modulation | OOK/ASK |
| Pulse Duration | Variable (10-100 ms) |

<a id="figure-9"></a>
![Figure 9: Signal Analysis Waterfall](figures/fig-009.png)
*Figure 9: Waterfall display showing temporal pattern of 433 MHz signals*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

The signals exhibited characteristics consistent with:
- Remote keyless entry systems
- Wireless sensors and weather stations
- Potential bio-radar illumination sources

<a id="figure-10"></a>
![Figure 10: Decoded Signal Pattern](figures/fig-010.png)
*Figure 10: Decoded on-off keying pattern from 433 MHz transmission*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

[↑ Back to Table of Contents](#toc)

---

<a id="discussion"></a>
## 4. Discussion

<a id="cazzamalli"></a>
### 4.1 Cazzamalli's Historical Research

Dr. Ferdinando Cazzamalli (1887-1958) conducted pioneering research on the interaction between electromagnetic waves and the human brain. His experiments in the 1920s demonstrated that:

1. The brain emits weak electromagnetic signals
2. When exposed to external EM fields, the brain reradiates modified signals
3. These reradiated signals contain information about mental states

<a id="figure-11"></a>
![Figure 11: Cazzamalli's Original Apparatus](figures/fig-011.png)
*Figure 11: Diagram of Cazzamalli's original experimental apparatus*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

Cazzamalli's work, while controversial, laid the foundation for understanding bioelectromagnetic interactions. Modern technology allows us to revisit his findings with more sensitive equipment.

<a id="bio-radar"></a>
### 4.2 Bio-Radar Principles

Bio-radar (biological radar) operates on the principle that living tissue has unique electromagnetic properties:

- **Dielectric properties**: Tissue permittivity varies with frequency
- **Conductivity**: Biological tissues conduct electricity
- **Resonance**: Body cavities and organs have resonant frequencies
- **Motion detection**: Respiration and heartbeat modulate reflected signals

<a id="figure-12"></a>
![Figure 12: Bio-Radar Block Diagram](figures/fig-012.png)
*Figure 12: Block diagram of a bio-radar detection system*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

The human body's resonant frequencies depend on:

$$f_r = \frac{c}{2L\sqrt{\epsilon_r}}$$

Where:
- $f_r$ = resonant frequency
- $c$ = speed of light
- $L$ = body dimension
- $\epsilon_r$ = relative permittivity of tissue

<a id="figure-13"></a>
![Figure 13: Tissue Permittivity vs Frequency](figures/fig-013.png)
*Figure 13: Graph showing tissue permittivity as a function of frequency*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

<a id="rnm"></a>
### 4.3 Remote Neural Monitoring

Remote Neural Monitoring (RNM) refers to the theoretical capability to remotely detect and interpret neural activity. While officially classified technology, patents and academic literature suggest systems capable of:

- Detecting brain wave patterns at a distance
- Correlating neural activity with thoughts or intentions
- Two-way communication with the nervous system

<a id="figure-14"></a>
![Figure 14: RNM Concept Diagram](figures/fig-014.png)
*Figure 14: Conceptual diagram of Remote Neural Monitoring system*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

Such systems would require:
1. High-sensitivity receivers
2. Signal processing for weak signal extraction
3. Pattern recognition algorithms
4. Reference databases of neural signatures

<a id="figure-15"></a>
![Figure 15: Neural Signal Processing Chain](figures/fig-015.png)
*Figure 15: Signal processing chain for neural signal extraction*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

<a id="implications"></a>
### 4.4 Implications for Havana Syndrome

The detection methods presented have implications for Havana Syndrome research:

1. **Forensic Detection**: SDR technology could detect ongoing EM attacks
2. **Frequency Identification**: Pinpointing specific frequencies used
3. **Source Localization**: Direction-finding to locate transmitters
4. **Countermeasures**: Developing shielding and jamming techniques

<a id="figure-16"></a>
![Figure 16: Havana Syndrome Symptom Correlation](figures/fig-016.png)
*Figure 16: Correlation between EM exposure and reported Havana Syndrome symptoms*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

Challenges include:
- Distinguishing attack signals from ambient RF
- Real-time detection requirements
- Legal and regulatory constraints on jamming
- International cooperation and attribution

[↑ Back to Table of Contents](#toc)

---

<a id="conclusion"></a>
## 5. Conclusion

This paper presents practical methods for detecting electromagnetic frequencies that may affect human biology in the context of Havana Syndrome investigations. Key findings include:

1. **SDR Accessibility**: Consumer-grade SDR equipment can detect signals in frequency ranges of interest
2. **433 MHz Activity**: Significant signal activity was detected at 433 MHz, warranting further investigation
3. **Bio-Radar Principles**: The theoretical framework of bio-radar provides a basis for understanding EM-biological interactions
4. **Detection Feasibility**: It is feasible to detect potential directed energy signals with proper methodology

<a id="figure-17"></a>
![Figure 17: Summary of Detection Results](figures/fig-017.png)
*Figure 17: Summary visualization of detection results across frequency bands*

[↑ Back to TOC](#toc) | [View all Figures](#figures-index)

Future work should include:
- Controlled laboratory experiments
- Collaboration with medical researchers
- Development of automated detection systems
- International standardization of detection protocols

The methods presented provide a starting point for individuals and organizations seeking to investigate potential EM-based attacks and develop protective countermeasures.

[↑ Back to Table of Contents](#toc)

---

<a id="references"></a>
## References

1. Cazzamalli, F. (1925). "Telepsychic phenomena and brain radiations." *Neurological Journal*, 2, 1-15.

2. Lin, J.C. (2021). "Microwave Auditory Effects and Applications." *Charles C Thomas Publisher*.

3. Frey, A.H. (1962). "Human auditory system response to modulated electromagnetic energy." *Journal of Applied Physiology*, 17(4), 689-692.

4. National Academies of Sciences, Engineering, and Medicine. (2020). "An Assessment of Illness in U.S. Government Employees and Their Families at Overseas Embassies."

5. Pall, M.L. (2018). "Microwave frequency electromagnetic fields (EMFs) produce widespread neuropsychiatric effects including depression." *Journal of Chemical Neuroanatomy*, 75, 43-51.

6. Foster, K.R., & Moulder, J.E. (2013). "Wi-Fi and health: review of current status of research." *Health Physics*, 105(6), 561-575.

7. Beason, R.C., & Semm, P. (2002). "Does the avian ophthalmic nerve carry magnetic navigational information?" *Journal of Experimental Biology*, 205(20), 3267-3274.

8. Elder, J.A., & Chou, C.K. (2003). "Auditory response to pulsed radiofrequency energy." *Bioelectromagnetics*, 24(S6), S162-S173.

9. IEEE Standard C95.1 (2019). "IEEE Standard for Safety Levels with Respect to Human Exposure to Electric, Magnetic, and Electromagnetic Fields."

10. McLean, C. (2024). "Solving Havana Syndrome: Research Documentation and Analysis."

[↑ Back to Table of Contents](#toc)

---

<a id="figures-index"></a>
## Figures Index

| Figure | Description | Link |
|--------|-------------|------|
| Figure 1 | Cazzamalli's Experiment Setup | [View](#figure-1) |
| Figure 2 | RF Transmission and Reception Concept | [View](#figure-2) |
| Figure 3 | SDR Equipment Setup | [View](#figure-3) |
| Figure 4 | SDR# Interface | [View](#figure-4) |
| Figure 5 | Detection Protocol Flowchart | [View](#figure-5) |
| Figure 6 | Wideband Spectrum Scan | [View](#figure-6) |
| Figure 7 | 433 MHz Spectrum Detail | [View](#figure-7) |
| Figure 8 | 433 MHz Signal with Subject Present | [View](#figure-8) |
| Figure 9 | Signal Analysis Waterfall | [View](#figure-9) |
| Figure 10 | Decoded Signal Pattern | [View](#figure-10) |
| Figure 11 | Cazzamalli's Original Apparatus | [View](#figure-11) |
| Figure 12 | Bio-Radar Block Diagram | [View](#figure-12) |
| Figure 13 | Tissue Permittivity vs Frequency | [View](#figure-13) |
| Figure 14 | RNM Concept Diagram | [View](#figure-14) |
| Figure 15 | Neural Signal Processing Chain | [View](#figure-15) |
| Figure 16 | Havana Syndrome Symptom Correlation | [View](#figure-16) |
| Figure 17 | Summary of Detection Results | [View](#figure-17) |

[↑ Back to Table of Contents](#toc)

---

*Document generated with hyperlinked navigation for cross-platform reading*

*Copyright © Clint McLean. All rights reserved.*
