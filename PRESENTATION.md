# Clint McLean Research Presentation

## RF Biological Effects & Havana Syndrome Detection

---

# SLIDE 1: Title

## Solving Havana Syndrome
### RF Biological Effects & Detection Methods

**Based on Research by Clint McLean**

- McLean Research Institute
- GitHub: @ClintMclean74

---

# SLIDE 2: The Problem

## What is Havana Syndrome?

**First Reported:** Cuba & China (2016-2017)

**Symptoms:**
- Tinnitus (ringing in ears)
- Cognitive dysfunction
- Memory loss
- Hearing loss
- Dizziness / balance issues
- Headaches / nausea
- "Buffeting" sensation

**Spread to:** Russia, Australia, Taiwan, Austria, Poland, Georgia, White House (USA)

---

# SLIDE 3: The Consensus

## Most Probable Cause

Multiple independent studies point to:

### **Pulsed Microwave/RF Radiation**

Sources:
- Professor James Lin
- Dr. Beatrice Golomb
- National Academy of Sciences
- US Intelligence Community

**But HOW does RF cause these symptoms without burns?**

---

# SLIDE 4: The Gap in Science

## The Missing Mechanism

> "No mechanisms for inducing changes in cell-membrane potential at frequencies above ~10 MHz have been demonstrated"
> — IARC Monograph

> "No biophysical mechanisms have been scientifically validated that would link chronic exposures below [thermal] levels to adverse health effects"
> — IEEE Safety Standards

**McLean's research fills this gap.**

---

# SLIDE 5: The Key Insight

## Your Head is an Antenna

| Body Part | Resonant Frequency |
|-----------|-------------------|
| Adult Head | ~400 MHz |
| Child Head | ~500-600 MHz |
| Baby Head | ~700 MHz |

At these frequencies, the head **absorbs maximum RF energy**.

---

# SLIDE 6: The Mechanism

## RF → Temperature → Neural Effects

```
┌─────────────────┐
│   RF Energy     │
└────────┬────────┘
         ↓
┌─────────────────┐
│ Tiny Temp Change│  ← As small as 0.0001°C
└────────┬────────┘
         ↓
┌─────────────────┐
│ Ion Movement    │  ← Nernst Equation
└────────┬────────┘
         ↓
┌─────────────────┐
│ Membrane Voltage│  ← Hodgkin-Huxley Model
└────────┬────────┘
         ↓
┌─────────────────┐
│ Neural Firing   │
└────────┬────────┘
         ↓
┌─────────────────┐
│ Network Amplify │  ← Key Discovery!
└────────┬────────┘
         ↓
┌─────────────────┐
│ Brain Dysfunction│
└─────────────────┘
```

---

# SLIDE 7: The Nernst Equation

## Temperature Affects Ion Voltage

```
E = (RT/zF) × ln([X]out/[X]in)
```

| Variable | Meaning |
|----------|---------|
| E | Equilibrium voltage |
| R | Gas constant |
| **T** | **Temperature** ← Key! |
| z | Ion valence |
| F | Faraday constant |
| [X] | Ion concentration |

**Temperature directly controls voltage.**

---

# SLIDE 8: The Numbers

## Small Temperature = Big Effect

| Temperature at 6.3°C | Temperature at 16.3°C | Difference |
|---------------------|----------------------|------------|
| Na⁺: +52.4 mV | Na⁺: +54.3 mV | +1.9 mV |
| K⁺: -72.2 mV | K⁺: -74.7 mV | -2.5 mV |

**Threshold voltage: ~-55 mV**
**Resting potential: -60 to -70 mV**

A ~2 mV shift can mean **fire vs. don't fire**.

---

# SLIDE 9: Four Mechanisms

## How RF Affects Neurons

### INHIBITORY (Suppress Activity)
1. **Threshold Inhibition** - Harder to fire
2. **Spike Reduction** - Weaker signals

### EXCITATORY (Increase Activity)
3. **Rate Excitation** - Faster firing
4. **Anode Break** - Pulse triggers firing

---

# SLIDE 10: The Amplification Effect

## Neural Networks Magnify RF Effects

| Temp Increase | Neurons in Error (Layer 10) |
|---------------|----------------------------|
| +0.01°C | >20% |
| +0.001°C | ~15% |
| +0.0001°C | ~3.5% |

**All below the 1°C "safe" threshold!**

---

# SLIDE 11: The Cascade

## How Tiny Effects Become Large

```
Layer 1:  Microscopic timing difference
    ↓
Layer 2:  Slight desynchronization
    ↓
Layer 3:  Some wrong neurons fire
    ↓
Layer 4:  Effect compounds
    ↓
Layer 10: 20%+ neurons wrong
    ↓
Brain:    BILLIONS of neurons
          TRILLIONS of connections
          = MASSIVE amplification
```

---

# SLIDE 12: Experimental Proof

## Food-Finding AI Task

273 Hodgkin-Huxley neurons tasked with finding food:

| Temperature | Food Found | Result |
|-------------|------------|--------|
| Normal | All items | Success |
| +0.0001°C | 4 items | Impaired |
| +0.001°C | 2 items | Severely impaired |
| +0.01°C | 0 items | **Complete failure** |

**All temperatures far below 1°C "thermal" threshold.**

---

# SLIDE 13: Why Pulsed RF is Worse

## Continuous vs. Pulsed

| Continuous Wave | Pulsed RF |
|-----------------|-----------|
| Gradual change | Rapid fluctuations |
| Body adapts | No time to adapt |
| Predictable | Unpredictable |
| Natural analogs exist | **No natural analog** |

Biological systems never evolved to handle pulsed RF.

---

# SLIDE 14: Detection is Possible

## You Can Monitor for Attacks

### Minimum Equipment (~$30)

| Item | Cost |
|------|------|
| RTL-SDR dongle | ~$30 |
| Antenna | Included |
| SDR# software | Free |

---

# SLIDE 15: What to Monitor

## Priority Frequencies

| Frequency | Why |
|-----------|-----|
| **400-450 MHz** | Adult head resonance |
| **433.92 MHz** | European ISM band |
| **700 MHz** | Baby/child head |
| **915 MHz** | US ISM band |
| **2.4 GHz** | WiFi/microwave |

---

# SLIDE 16: Detection Protocol

## 5-Step Process

1. **BASELINE** - Record spectrum, no one present
2. **INTRODUCE** - Bring subject near antenna
3. **COMPARE** - Look for changes
4. **SWEEP** - Scan 300 MHz - 3 GHz
5. **ANALYZE** - Document patterns

---

# SLIDE 17: Historical Foundation

## Cazzamalli's "Brain Radio" (1920s)

Dr. Ferdinando Cazzamalli discovered:

1. Brain emits weak EM signals
2. When exposed to RF, brain **reradiates**
3. Reradiated signals contain information

**Modern bio-radar confirms this principle.**

---

# SLIDE 18: Implications

## What This Means

### For Safety Standards
- Current 1°C threshold is **inadequate**
- Sub-thermal effects are **real**
- Standards need **revision**

### For Security
- Attacks are **possible** with commercial equipment
- Detection is **feasible**
- Countermeasures can be **developed**

---

# SLIDE 19: Key Takeaways

## Remember These Points

1. **0.0001°C** can affect neurons
2. **Neural networks amplify** tiny effects
3. **400 MHz** = adult head resonance
4. **$30 SDR** can detect attacks
5. **Pulsed RF** is more dangerous than continuous

---

# SLIDE 20: Resources

## Learn More

### Books
- "Solving Havana Syndrome" (Amazon Kindle)
- "Methods for Detecting RF"

### Code
- github.com/ClintMclean74/Hodgkin-HuxleyCode
- github.com/ClintMclean74/SDRSpectrumAnalyzer
- github.com/ClintMclean74/SDRReradiationSpectrumAnalyzer

### Website
- mcleanresearchinstitute.com

---

# SLIDE 21: Questions?

## Contact

**Clint McLean**
- Email: clint@mcleanresearchinstitute.com
- GitHub: @ClintMclean74
- Web: mcleanresearchinstitute.com

---

*Presentation based on Clint McLean's published research*
*For educational and research purposes*
