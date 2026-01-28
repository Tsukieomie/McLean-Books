# Clint McLean's Research Books

Research publications by **Clint McLean** on Havana Syndrome, RF biological effects, and electromagnetic detection methods.

---

## Quick Links

| Resource | Description |
|----------|-------------|
| [STUDY_NOTES.md](STUDY_NOTES.md) | In-depth chapter-by-chapter analysis |
| [QUICK_REFERENCE.md](QUICK_REFERENCE.md) | One-page reference card |
| [PRESENTATION.md](PRESENTATION.md) | Slide deck for presentations |
| [DATA_TABLES.md](DATA_TABLES.md) | All extracted data and tables |
| [CODE_REPOSITORIES.md](CODE_REPOSITORIES.md) | Guide to McLean's GitHub code |
| [BOOK2_DEEP_ANALYSIS.md](BOOK2_DEEP_ANALYSIS.md) | In-depth review of Book 2 |
| [VIDEO_ANALYSIS.md](VIDEO_ANALYSIS.md) | Analysis of McLean's detection demo video |
| [VIDEO_TRANSCRIPT.md](VIDEO_TRANSCRIPT.md) | Full cleaned transcript with timestamps |
| [EQUIPMENT_GUIDE.md](EQUIPMENT_GUIDE.md) | Complete hardware/software buying guide |
| [HACKRF_INVESTIGATION.md](HACKRF_INVESTIGATION.md) | Investigation into unfulfilled HackRF claim |

---

## Books

### 1. Solving Havana Syndrome and Biological Effects of RF Using the Hodgkin-Huxley Neuron Model

**Author:** Clint McLean
**Publisher:** McLean Research Institute
**Copyright:** © 2022
**ISBN:** 978-0-6397-2006-7 (ebook)

A scientifically rigorous exploration of how RF (Radio Frequency) radiation affects biological systems, specifically neural signaling. Uses the Hodgkin-Huxley neuron model to explain the mechanisms behind Havana Syndrome.

**Key Discovery:** Temperature changes as small as **0.0001°C** can affect neural signaling when amplified through neural networks.

**Key Topics:**
- Hodgkin-Huxley neuron model fundamentals
- Temperature-induced neural effects (Nernst equation)
- Four mechanisms: Threshold Inhibition, Spike Reduction, Rate Excitation, Anode Break
- Neural network amplification of RF effects
- Sub-thermal effects below safety standards

**Formats:** PDF, EPUB, MOBI, AZW3, DOCX, MD, HTML

**Location:** `01-Solving-Havana-Syndrome/`

---

### 2. Methods for Detecting Biology Affecting Electromagnetic Frequency Ranges Causing Havana Syndrome

**Author:** Clint McLean

Practical methodology for detecting electromagnetic frequencies that may affect human biology, using Software Defined Radio (SDR) technology and spectrum analysis.

**Key Topics:**
- SDR detection methodology with RTL-SDR (~$30)
- 433 MHz signal analysis
- Cazzamalli's historical research on brain radio signals
- Bio-radar principles
- Human resonant frequencies (400 MHz adult head, 700 MHz baby head)
- Equipment setup and configuration

**Formats:** PDF, EPUB, MOBI, AZW3, DOCX, MD, HTML

**Location:** `02-Methods-for-Detecting/`

---

## Key Numbers to Remember

| Fact | Value |
|------|-------|
| Current safety threshold | +1°C |
| McLean's minimum effect | **+0.0001°C** |
| Adult head resonance | ~400 MHz |
| Baby head resonance | ~700 MHz |
| Neurons in error at +0.01°C | >20% |
| Detection equipment cost | ~$30 |

---

## Related Code Repositories

| Repository | Language | Purpose |
|------------|----------|---------|
| [Hodgkin-HuxleyCode](https://github.com/ClintMclean74/Hodgkin-HuxleyCode) | C/C++ | Neural simulation from Book 1 |
| [SDRSpectrumAnalyzer](https://github.com/ClintMclean74/SDRSpectrumAnalyzer) | C# | Original RF detection (Windows) |
| [SDRReradiationSpectrumAnalyzer](https://github.com/ClintMclean74/SDRReradiationSpectrumAnalyzer) | C | Advanced detection (Windows/Linux) |

See [CODE_REPOSITORIES.md](CODE_REPOSITORIES.md) for detailed documentation.

### HackRF Support Status

McLean mentioned HackRF support as a planned feature in his August 2020 video:

> "I'm going to be modifying the code system that I wrote to also use these [HackRF]."

**Deep Investigation Result (January 2025):** The real story is more complex than it appears.

| Phase | Date | Status |
|-------|------|--------|
| Claim made | Aug 2020 | HackRF support promised |
| **IMPLEMENTED** | ~2020-2021 | Via `hackrf=0` in GNU Radio flowgraph |
| **REMOVED** | Jun 22, 2021 | Commit `b79f25d` removed HackRF-specific code |
| Current | Jan 2025 | Auto-detection works, explicit support gone |

**The Smoking Gun - Commit b79f25d:**
```diff
- self.osmosdr_source_0 = osmosdr.source( args="numchan=" + str(1) + " " + 'hackrf=0' )
+ self.osmosdr_source_0 = osmosdr.source( args="numchan=" + str(1) + " " + "" )
```

**Why It Was Removed:**
McLean removed explicit HackRF targeting to enable generic device auto-detection, making the software work with ANY osmosdr-compatible SDR (RTL-SDR, HackRF, Airspy, etc.).

**Current Status:**

| Feature | Status |
|---------|--------|
| RTL-SDR Native | Fully implemented |
| HackRF via GNU Radio | Works (auto-detected) |
| HackRF Native (C/C++) | Not implemented |

**The Real Story:** HackRF support was implemented, then deliberately changed to device-agnostic auto-detection. It still works—just not explicitly.

See [HACKRF_INVESTIGATION.md](HACKRF_INVESTIGATION.md) for the complete technical investigation with commit evidence.

---

## Video Resources

### Detection Demonstration Video

| Field | Value |
|-------|-------|
| **Title** | Detection of frequency ranges used for electronic harassment |
| **Channel** | The Science Of Electronic Harassment |
| **Duration** | 8:51 |
| **Upload Date** | August 15, 2020 |
| **URL** | [Watch on YouTube](https://www.youtube.com/watch?v=sP4ZjyrfuUo) |

**Documentation:**
- [VIDEO_ANALYSIS.md](VIDEO_ANALYSIS.md) - Comprehensive analysis with equipment list, methodology, and assessment
- [VIDEO_TRANSCRIPT.md](VIDEO_TRANSCRIPT.md) - Full cleaned transcript with timestamps and glossary

**Video Summary:**

This video demonstrates real-time RF detection at ~10 meters using RTL-SDR equipment and McLean's open-source software. Key findings:

| Finding | Detail |
|---------|--------|
| Detection range | ~10 meters from detector |
| Frequency range | 400-500 MHz (adult head resonance) |
| Equipment cost | Under $100 total |
| Correlation | Signal strength increases when subject enters detection region |

The video serves as a practical demonstration of the detection methodology described in Book 2.

---

## Repository Contents

```
McLean-Books/
├── README.md                   # This file
├── STUDY_NOTES.md              # Comprehensive study notes
├── QUICK_REFERENCE.md          # One-page quick reference
├── PRESENTATION.md             # Slide deck (21 slides)
├── DATA_TABLES.md              # All extracted data tables
├── CODE_REPOSITORIES.md        # GitHub code documentation
├── BOOK2_DEEP_ANALYSIS.md      # Deep analysis of Book 2
├── VIDEO_ANALYSIS.md           # YouTube video analysis
├── VIDEO_TRANSCRIPT.md         # Cleaned video transcript
├── EQUIPMENT_GUIDE.md          # Hardware/software buying guide
├── HACKRF_INVESTIGATION.md     # Why HackRF claim was never fulfilled
│
├── 01-Solving-Havana-Syndrome/
│   ├── McLean_Solving_Havana_Syndrome.pdf
│   ├── McLean_Solving_Havana_Syndrome.epub
│   ├── McLean_Solving_Havana_Syndrome.mobi
│   ├── McLean_Solving_Havana_Syndrome.azw3
│   ├── McLean_Solving_Havana_Syndrome.docx
│   ├── McLean_Solving_Havana_Syndrome.md
│   ├── McLean_Solving_Havana_Syndrome.html
│   ├── cover.jpg
│   └── figures/                # 99 figures
│
└── 02-Methods-for-Detecting/
    ├── McLean_Methods_for_Detecting.pdf
    ├── McLean_Methods_for_Detecting.epub
    ├── McLean_Methods_for_Detecting.mobi
    ├── McLean_Methods_for_Detecting.azw3
    ├── McLean_Methods_for_Detecting.docx
    ├── McLean_Methods_for_Detecting.md
    ├── McLean_Methods_for_Detecting.html
    └── figures/                # 18 figures
```

---

## Author

**Clint McLean** is a researcher focused on RF biological effects, SDR technology, and neural modeling. His work combines neuroscience (Hodgkin-Huxley model) with practical RF detection methods.

| Contact | Link |
|---------|------|
| GitHub | [@ClintMclean74](https://github.com/ClintMclean74) |
| Website | [mcleanresearchinstitute.com](https://www.mcleanresearchinstitute.com) |
| Email | clint@mcleanresearchinstitute.com |
| Amazon | [Solving Havana Syndrome (Kindle)](https://www.amazon.com/Solving-Syndrome-Biological-Effects-Hodgkin-Huxley-ebook/dp/B0BCNG8H89) |

---

## License

These materials are shared for educational and research purposes. Please respect the author's copyright.

- Books: © 2022 Clint McLean, McLean Research Institute
- Code: GPL v2+ (see individual repositories)
- Study materials in this repo: For educational use

---

*Repository maintained by Tsukieomie*
