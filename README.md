# Clint McLean's Research on Havana Syndrome & RF Detection

A comprehensive research archive on **Havana Syndrome**, RF biological effects, and electromagnetic detection methods by **Clint McLean**.

---

## Quick Start

| If you want to... | Go to... |
|-------------------|----------|
| **Get equipment and start detecting** | [EQUIPMENT_GUIDE.md](EQUIPMENT_GUIDE.md) |
| **Understand the science in 5 minutes** | [QUICK_REFERENCE.md](QUICK_REFERENCE.md) |
| **Review RF/neural patents** | [PATENT_ANALYSIS.md](PATENT_ANALYSIS.md) |
| **Watch the detection demo** | [YouTube Video](https://www.youtube.com/watch?v=sP4ZjyrfuUo) |
| **Read the full books** | [Book 1](01-Solving-Havana-Syndrome/) / [Book 2](02-Methods-for-Detecting/) |

---

## Repository Index

### Books (Primary Sources)

| Book | Topic | Location |
|------|-------|----------|
| **Book 1** | Solving Havana Syndrome (Hodgkin-Huxley Model) | [01-Solving-Havana-Syndrome/](01-Solving-Havana-Syndrome/) |
| **Book 2** | Methods for Detecting RF Frequencies | [02-Methods-for-Detecting/](02-Methods-for-Detecting/) |

### Study Materials

| Document | Description | Audience |
|----------|-------------|----------|
| [STUDY_NOTES.md](STUDY_NOTES.md) | Chapter-by-chapter analysis | Deep study |
| [QUICK_REFERENCE.md](QUICK_REFERENCE.md) | One-page reference card | Quick review |
| [PRESENTATION.md](PRESENTATION.md) | 21-slide presentation deck | Teaching |
| [DATA_TABLES.md](DATA_TABLES.md) | All extracted data tables | Research |
| [BOOK2_DEEP_ANALYSIS.md](BOOK2_DEEP_ANALYSIS.md) | In-depth Book 2 review | Advanced |

### Research & Analysis

| Document | Description |
|----------|-------------|
| [PATENT_ANALYSIS.md](PATENT_ANALYSIS.md) | **NEW** - Comprehensive analysis of 7 RF/neural effect patents |
| [EEG_RESEARCH_ANALYSIS.md](EEG_RESEARCH_ANALYSIS.md) | **NEW** - Analysis of external EEG research repository |

### Equipment & Hardware

| Document | Description |
|----------|-------------|
| [EQUIPMENT_GUIDE.md](EQUIPMENT_GUIDE.md) | Complete hardware buying guide (RTL-SDR, HackRF, Portapack, antennas) |
| [HACKRF_INVESTIGATION.md](HACKRF_INVESTIGATION.md) | Deep investigation into HackRF support claims |

### Video Resources

| Document | Description |
|----------|-------------|
| [VIDEO_ANALYSIS.md](VIDEO_ANALYSIS.md) | Comprehensive video analysis with methodology |
| [VIDEO_TRANSCRIPT.md](VIDEO_TRANSCRIPT.md) | Full transcript with timestamps and glossary |

### Code & Software

| Document | Description |
|----------|-------------|
| [CODE_REPOSITORIES.md](CODE_REPOSITORIES.md) | Guide to McLean's GitHub repositories |

---

## Key Facts at a Glance

### The Science

| Fact | Value | Significance |
|------|-------|--------------|
| Current RF safety threshold | +1°C | ICNIRP/IEEE standard |
| McLean's minimum effect threshold | **+0.0001°C** | 10,000x below "safe" |
| Neurons in error at +0.01°C | >20% | Network amplification |

### Human Resonant Frequencies

| Subject | Frequency | Wavelength |
|---------|-----------|------------|
| Adult head | **400-500 MHz** | ~60-75 cm |
| Baby head | **~700 MHz** | ~43 cm |
| Body (standing) | ~80 MHz | ~3.75 m |

### Detection Equipment

| Setup | Cost | Complexity |
|-------|------|------------|
| Basic (RTL-SDR + antenna) | ~$50 | Low |
| Standard (RTL-SDR + Yagi) | ~$100 | Medium |
| Advanced (Portapack H4M+) | ~$150-250 | Medium |

---

## Books

### Book 1: Solving Havana Syndrome

**Full Title:** Solving Havana Syndrome and Biological Effects of RF Using the Hodgkin-Huxley Neuron Model

| Field | Value |
|-------|-------|
| Author | Clint McLean |
| Publisher | McLean Research Institute |
| Copyright | © 2022 |
| ISBN | 978-0-6397-2006-7 |
| Formats | PDF, EPUB, MOBI, AZW3, DOCX, MD, HTML |

**Key Discovery:** Temperature changes as small as **0.0001°C** can affect neural signaling when amplified through neural networks.

**Topics Covered:**
- Hodgkin-Huxley neuron model
- Temperature-induced neural effects (Nernst equation)
- Four mechanisms: Threshold Inhibition, Spike Reduction, Rate Excitation, Anode Break
- Neural network amplification
- Sub-thermal effects below safety standards

---

### Book 2: Methods for Detecting

**Full Title:** Methods for Detecting Biology Affecting Electromagnetic Frequency Ranges Causing Havana Syndrome

| Field | Value |
|-------|-------|
| Author | Clint McLean |
| Formats | PDF, EPUB, MOBI, AZW3, DOCX, MD, HTML |

**Topics Covered:**
- SDR detection methodology
- 433 MHz signal analysis
- Cazzamalli's historical research
- Bio-radar principles
- Human resonant frequencies
- Equipment setup

---

## Video Demonstration

| Field | Value |
|-------|-------|
| **Title** | Detection of frequency ranges used for electronic harassment |
| **Channel** | The Science Of Electronic Harassment |
| **Duration** | 8:51 |
| **Date** | August 15, 2020 |
| **URL** | [Watch on YouTube](https://www.youtube.com/watch?v=sP4ZjyrfuUo) |

### Key Findings from Video

| Finding | Detail |
|---------|--------|
| Detection range | ~10 meters |
| Frequency range | 400-500 MHz |
| Equipment cost | Under $100 |
| Signal behavior | Strength increases when subject enters detection region |

---

## McLean's Code Repositories

| Repository | Language | Purpose | Status |
|------------|----------|---------|--------|
| [Hodgkin-HuxleyCode](https://github.com/ClintMclean74/Hodgkin-HuxleyCode) | C/C++ | Neural simulation | Active |
| [SDRSpectrumAnalyzer](https://github.com/ClintMclean74/SDRSpectrumAnalyzer) | C# | Original detection (Windows) | Abandoned 2019 |
| [SDRReradiationSpectrumAnalyzer](https://github.com/ClintMclean74/SDRReradiationSpectrumAnalyzer) | C | Advanced detection | Last commit Oct 2023 |

### HackRF Support Investigation

**Claim (Aug 2020):** McLean said he would add HackRF support.

**Reality (Discovered Jan 2025):**

| Phase | Date | Status |
|-------|------|--------|
| Claim made | Aug 2020 | HackRF promised |
| **Implemented** | ~2020-2021 | Via `hackrf=0` in GNU Radio |
| **Removed** | Jun 22, 2021 | Commit `b79f25d` |
| Current | Jan 2025 | Auto-detection works |

**The Smoking Gun:**
```diff
- osmosdr.source( args="numchan=" + str(1) + " " + 'hackrf=0' )
+ osmosdr.source( args="numchan=" + str(1) + " " + "" )
```

HackRF was implemented then removed to enable generic device auto-detection. See [HACKRF_INVESTIGATION.md](HACKRF_INVESTIGATION.md) for full details.

---

## Repository Structure

```
McLean-Books/
│
├── README.md                      # This file (index)
│
├── STUDY MATERIALS
│   ├── STUDY_NOTES.md             # Chapter-by-chapter analysis
│   ├── QUICK_REFERENCE.md         # One-page reference
│   ├── PRESENTATION.md            # Slide deck (21 slides)
│   ├── DATA_TABLES.md             # Extracted data tables
│   └── BOOK2_DEEP_ANALYSIS.md     # Deep analysis of Book 2
│
├── RESEARCH & ANALYSIS (NEW)
│   ├── PATENT_ANALYSIS.md         # 7 RF/neural patents analyzed
│   └── EEG_RESEARCH_ANALYSIS.md   # External EEG research review
│
├── EQUIPMENT & HARDWARE
│   ├── EQUIPMENT_GUIDE.md         # Hardware buying guide
│   └── HACKRF_INVESTIGATION.md    # HackRF deep dive
│
├── VIDEO RESOURCES
│   ├── VIDEO_ANALYSIS.md          # Video analysis
│   └── VIDEO_TRANSCRIPT.md        # Full transcript
│
├── CODE DOCUMENTATION
│   └── CODE_REPOSITORIES.md       # GitHub repos guide
│
├── BOOKS
│   ├── 01-Solving-Havana-Syndrome/
│   │   ├── *.pdf, *.epub, *.mobi, *.azw3, *.docx, *.md, *.html
│   │   └── figures/ (99 figures)
│   │
│   └── 02-Methods-for-Detecting/
│       ├── *.pdf, *.epub, *.mobi, *.azw3, *.docx, *.md, *.html
│       └── figures/ (18 figures)
```

---

## Author Information

**Clint McLean** - RF biological effects researcher

| Contact | Link |
|---------|------|
| GitHub | [@ClintMclean74](https://github.com/ClintMclean74) |
| Website | [mcleanresearchinstitute.com](https://www.mcleanresearchinstitute.com) |
| Email | clint@mcleanresearchinstitute.com |
| Amazon | [Solving Havana Syndrome (Kindle)](https://www.amazon.com/Solving-Syndrome-Biological-Effects-Hodgkin-Huxley-ebook/dp/B0BCNG8H89) |

---

## License

| Content | License |
|---------|---------|
| Books | © 2022 Clint McLean, McLean Research Institute |
| Code | GPL v2+ (see individual repositories) |
| Study materials | Educational use |

---

*Repository maintained by Tsukieomie*
*Last updated: January 2025*
