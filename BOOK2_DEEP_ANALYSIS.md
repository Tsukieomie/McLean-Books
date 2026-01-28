# Book 2 Deep Analysis: Methods for Detecting RF

## Comprehensive review of "Methods for Detecting Biology Affecting Electromagnetic Frequency Ranges Causing Havana Syndrome"

**Author:** Clint McLean

---

## Overview

This is a **practical companion** to McLean's theoretical first book. While Book 1 explains *why* RF affects neurons, Book 2 shows *how* to detect potential RF attacks using affordable consumer equipment.

---

## Ratings

| Aspect | Rating | Notes |
|--------|--------|-------|
| **Accessibility** | ★★★★★ | $30 equipment, clear instructions |
| **Practicality** | ★★★★★ | Step-by-step detection protocol |
| **Historical Context** | ★★★★☆ | Excellent Cazzamalli coverage |
| **Technical Depth** | ★★★☆☆ | Good intro, could go deeper |
| **Reproducibility** | ★★★★☆ | Anyone can replicate experiments |

**Overall: 4/5 stars**

---

# Chapter 1: Introduction - Deep Analysis

## The Havana Syndrome Context

McLean opens by establishing the stakes:

| Location | Year | Affected |
|----------|------|----------|
| Havana, Cuba | 2016 | US/Canadian diplomats |
| Guangzhou, China | 2017 | US diplomats |
| Moscow, Russia | 2017+ | CIA officers |
| Vienna, Austria | 2021 | US officials |
| White House, USA | 2020-21 | NSC staff |

**Symptoms reported:**
- Hearing unusual sounds (clicking, buzzing, grinding)
- Headaches (often unilateral)
- Memory loss
- Brain injuries visible on MRI (without physical trauma)

## Cazzamalli: The Forgotten Pioneer

McLean resurrects the work of **Dr. Ferdinando Cazzamalli (1887-1958)**, an Italian neurologist whose research was largely ignored.

### Cazzamalli's Experiments (1920s-1930s)

**Setup:**
- Subject placed in Faraday cage
- Exposed to UHF radio waves
- Sensitive receiver monitored for signals

**Findings:**
1. Brain emits weak EM signals naturally
2. When illuminated by RF, brain **reradiates** modified signals
3. Reradiated signals varied with mental states
4. Called this "brain radio" or "psychic radio"

**Why it was ignored:**
- Ahead of its time
- No mechanism understood
- Associated with "fringe" science
- Cold War secrecy

**Modern validation:**
- Bio-radar technology confirms reradiation
- Through-wall human detection uses same principle
- Doppler radar detects heartbeat/breathing through walls

### McLean's Thesis

> "Understanding these interactions is critical for:
> - Detecting potential directed energy attacks
> - Developing countermeasures and shielding
> - Establishing forensic evidence of EM exposure
> - Advancing our understanding of bioelectromagnetic phenomena"

---

# Chapter 2: Methods - Deep Analysis

## The Hypothesis

McLean states four testable claims:

| # | Hypothesis |
|---|------------|
| 1 | Human tissue acts as a resonant cavity for certain EM frequencies |
| 2 | When illuminated by RF at resonant frequencies, body reradiates detectable signals |
| 3 | These reradiated signals can be detected using SDR technology |
| 4 | Frequency range of interest: 300 MHz - 3 GHz (UHF band) |

## Equipment Deep Dive

### RTL-SDR Blog V3 Specifications

| Spec | Value |
|------|-------|
| Chipset | RTL2832U + R820T2 |
| Frequency Range | 24 MHz - 1.766 GHz |
| Max Sample Rate | 3.2 MSPS (stable: 2.4 MSPS) |
| ADC Resolution | 8-bit |
| Input Impedance | 75Ω |
| Connector | SMA female |
| Price | ~$30 |

### Antenna Options

| Type | Frequency Range | Gain | Directional | Use Case |
|------|-----------------|------|-------------|----------|
| Telescopic (included) | Wideband | Low | No | General scanning |
| Dipole | Tuned frequency | Medium | Partial | Specific monitoring |
| Discone | Wideband | Medium | No | Always-on monitoring |
| Log-periodic | Wideband | High | Yes | Direction finding |
| Yagi | Narrow band | High | Yes | Tracking sources |

### Software Options

| Software | Platform | Cost | Difficulty | Best For |
|----------|----------|------|------------|----------|
| SDR# | Windows | Free | Easy | Beginners |
| GQRX | Linux/Mac | Free | Easy | Linux users |
| GNU Radio | All | Free | Hard | Advanced processing |
| SDRReradiation | Win/Linux | Free | Medium | McLean's method |

## SDR# Configuration Explained

### Sample Rate: 2.4 MSPS

**Why 2.4 MSPS?**
- Captures 2.4 MHz bandwidth
- Stable on most computers
- Good balance of resolution vs. CPU load
- Higher rates (3.2) may cause dropouts

### FFT Resolution: 32768

**What this means:**
```
Frequency bin size = Sample Rate / FFT Size
                   = 2,400,000 / 32768
                   = 73.24 Hz per bin
```

Higher FFT = better frequency resolution but slower update rate.

### Averaging: 10 frames

**Purpose:** Reduces noise by averaging multiple FFT frames
- Too low: Noisy display
- Too high: Misses transient signals
- 10 frames: Good compromise

## Detection Protocol Detailed

### Step 1: Baseline Measurement

**Duration:** 5-10 minutes minimum

**Document:**
- Time of day
- Location
- Nearby electronics (on/off)
- Weather conditions
- All visible signals and suspected sources

**Screenshot/record** the spectrum for comparison.

### Step 2: Subject Introduction

**Positioning:**
- Subject 1-3 meters from antenna
- Initially stationary
- Antenna at head height

**Variables to control:**
- Same electronics state as baseline
- No new devices introduced
- Subject wearing minimal electronics

### Step 3: Comparative Analysis

**Look for:**

| Change Type | Possible Meaning |
|-------------|------------------|
| New signal appears | Direct emission or reradiation |
| Signal strength increases | Reflection/absorption effect |
| Signal strength decreases | Body blocking signal |
| Modulation changes | Bio-modulation of carrier |

### Step 4: Frequency Sweeping

**Priority bands:**

| Band | Frequency | Dwell Time |
|------|-----------|------------|
| Adult head resonance | 380-420 MHz | 2+ minutes |
| ISM (Europe) | 430-440 MHz | 2+ minutes |
| ISM (Americas) | 902-928 MHz | 2+ minutes |
| Child head resonance | 500-600 MHz | 2+ minutes |
| Baby head resonance | 680-720 MHz | 2+ minutes |
| WiFi | 2.4-2.5 GHz | 1+ minute |

### Step 5: Signal Characterization

**For each interesting signal, document:**

| Parameter | How to Measure |
|-----------|----------------|
| Center frequency | Peak of signal |
| Bandwidth | -3dB points |
| Signal strength | Peak dBm |
| Modulation | AM/FM/digital? |
| Temporal pattern | Continuous/pulsed? |
| Correlation | Changes with subject movement? |

---

# Chapter 5: Conclusion - Deep Analysis

## Summary of Findings

McLean makes **appropriately modest claims**:

### What WAS demonstrated:

| Claim | Evidence Level |
|-------|----------------|
| Consumer SDR can detect relevant frequencies | **Strong** - Verified |
| 433 MHz shows interesting activity | **Moderate** - Observed |
| Bio-radar principles are sound | **Strong** - Literature supported |
| Detection methodology is feasible | **Strong** - Reproducible |

### What was NOT claimed:

- Definitive proof of attacks
- Ability to attribute signals to weapons
- Complete detection solution
- Medical diagnosis capability

## Future Research Directions

McLean proposes:

1. **Controlled laboratory experiments**
   - Faraday cage environment
   - Known RF sources
   - Multiple subjects
   - Statistical analysis

2. **Medical collaboration**
   - Correlate RF exposure with symptoms
   - EEG during RF exposure
   - Brain imaging studies

3. **Automated detection systems**
   - Machine learning for pattern recognition
   - Real-time alerting
   - Long-term monitoring

4. **International standardization**
   - Common detection protocols
   - Shared databases
   - Cross-border cooperation

## Practical Implications

### For Individuals

| Action | Difficulty | Cost |
|--------|------------|------|
| Purchase RTL-SDR | Easy | $30 |
| Learn SDR# basics | Easy | Free |
| Monitor home environment | Medium | Time |
| Document anomalies | Easy | Free |
| Implement shielding | Hard | $50-500 |

### For Organizations

| Action | Difficulty | Cost |
|--------|------------|------|
| Deploy monitoring stations | Medium | $100-500 each |
| Train security staff | Medium | Time |
| Establish baselines | Medium | Time |
| Create incident response | Hard | Policy work |
| Coordinate with authorities | Hard | Relationships |

### For Researchers

| Action | Priority |
|--------|----------|
| Replicate McLean's observations | High |
| Develop better attribution methods | High |
| Create controlled exposure studies | Medium |
| Build detection databases | Medium |
| Publish peer-reviewed findings | High |

---

## Critiques

| Issue | Severity | Notes |
|-------|----------|-------|
| **Signal attribution** | Medium | Hard to distinguish attack vs. normal RF |
| **Sample size** | Medium | Limited experimental data shown |
| **Replication details** | Low | Could use more specific parameters |
| **Statistical analysis** | Medium | No p-values or confidence intervals |

---

## Comparison to Book 1

| Aspect | Book 1 | Book 2 |
|--------|--------|--------|
| Focus | Theory | Practice |
| Rigor | High (simulations, math) | Medium (observational) |
| Actionability | Low (understanding) | High (do it yourself) |
| Audience | Scientists | General public |
| Cost to replicate | High (computing) | Low (~$30) |

---

## Key Takeaways

1. **Detection is democratized** - Anyone with $30 can monitor RF
2. **400-700 MHz is critical** - Human resonance range
3. **Cazzamalli was ahead of his time** - 1920s research still relevant
4. **Bio-radar is real** - Through-wall detection validates principle
5. **More research needed** - This is a starting point, not definitive proof

---

## Who Should Read This

| Audience | Recommendation |
|----------|----------------|
| Havana Syndrome victims | **Must read** - practical self-monitoring |
| Security professionals | **Recommended** - detection methodology |
| RF engineers | **Useful** - novel application |
| General public | **Accessible** - no prerequisites |
| Scientists | **Supplementary** - read Book 1 first |

---

## Final Assessment

### What makes this book valuable:

1. **Democratizes detection** - No expensive equipment needed
2. **Provides methodology** - Step-by-step process
3. **Historical grounding** - Cazzamalli context
4. **Honest limitations** - Doesn't overclaim
5. **Open source tools** - Free software available

### What's missing:

1. **Statistical rigor** - More data needed
2. **Control experiments** - Laboratory validation
3. **Attribution methods** - Can't identify source
4. **Legal framework** - What to do with evidence

### Bottom Line

This book is a **starting point**, not a complete solution. It gives anyone the tools to begin investigating potential RF exposure, while honestly acknowledging the limitations of current methods.

**Best used as:** A practical field guide alongside Book 1's theoretical foundation.

---

## Detection Checklist

### Equipment Shopping List

| Item | Model | Price | Priority |
|------|-------|-------|----------|
| SDR Dongle | RTL-SDR Blog V3 | $30 | Required |
| USB Extension | Any 2m+ | $10 | Recommended |
| Dipole Antenna | RTL-SDR Dipole Kit | $20 | Recommended |
| FM Filter | RTL-SDR FM Block | $10 | Optional |

**Total minimum: ~$30 | Recommended: ~$70**

### Pre-Detection Checklist

```
□ RTL-SDR connected and recognized
□ SDR# or GQRX installed and working
□ Antenna positioned at head height
□ Nearby electronics documented
□ Baseline spectrum recorded
□ Time and location noted
□ Weather conditions noted
```

### Detection Session Checklist

```
□ Baseline recorded (5+ minutes)
□ Subject introduced (1-3m from antenna)
□ Subject stationary initially
□ 400-450 MHz scanned (2+ minutes)
□ 433 MHz specifically checked
□ 650-750 MHz scanned (if children present)
□ Anomalies documented with screenshots
□ Subject movement correlation tested
```

### Post-Detection Checklist

```
□ All screenshots saved with timestamps
□ Signal parameters documented
□ Comparison to baseline completed
□ Anomalies flagged for follow-up
□ Session notes written
```

---

*Analysis compiled from Clint McLean's publication*
*For educational and research purposes*
