# McLean Research - Quick Reference Guide

## The Core Theory (One Paragraph)

RF/microwave energy causes tiny temperature fluctuations in brain tissue. These temperature changes alter ion movement through neural membrane channels (describable via the Nernst equation and Hodgkin-Huxley model). Even changes as small as 0.0001°C affect neural signaling. When these effects propagate through neural networks, they get amplified—causing widespread neurological dysfunction. This explains all Havana Syndrome symptoms without requiring burns or tissue damage.

---

## Key Numbers

| What | Value | Why It Matters |
|------|-------|----------------|
| Current safety threshold | +1°C | Based on thermal damage, not neural effects |
| McLean's minimum effect | +0.0001°C | 10,000x below safety threshold |
| Adult head resonance | ~400 MHz | Head acts as antenna at this frequency |
| Baby head resonance | ~700 MHz | Smaller head = higher frequency |
| ISM band (Europe) | 433 MHz | License-free, commonly used |
| Neurons in error at +0.01°C | >20% | At layer 10 of neural network |

---

## The Four Mechanisms

### Inhibitory (Suppress Neural Activity)

| # | Mechanism | What Happens |
|---|-----------|--------------|
| 1 | **Threshold Inhibition** | Membrane voltage shifts away from firing threshold → neuron fails to activate |
| 2 | **Spike Reduction** | Action potentials become shorter/weaker → insufficient to trigger next neuron |

### Excitatory (Increase Neural Activity)

| # | Mechanism | What Happens |
|---|-----------|--------------|
| 3 | **Rate Excitation** | Neurons fire at higher frequency → altered information encoding |
| 4 | **Anode Break** | When RF pulse ends, membrane voltage rebounds → triggers activation |

---

## Havana Syndrome Symptoms

```
□ Ringing in ears (tinnitus)
□ Memory loss / cognitive issues
□ Hearing loss
□ Fatigue / sleep problems
□ Dizziness / balance issues
□ Headaches
□ Nausea
□ Pressure in ears
□ "Buffeting" sensation
```

---

## Detection Equipment (Minimum)

| Item | Model | Cost |
|------|-------|------|
| SDR Dongle | RTL-SDR Blog V3 | ~$30 |
| Software | SDR# (Windows) or GQRX (Linux) | Free |
| Antenna | Included telescopic or dipole | $0-20 |

**Total: ~$30-50**

---

## Detection Protocol (5 Steps)

1. **BASELINE** - Record RF spectrum with no one present
2. **INTRODUCE** - Bring subject near antenna
3. **COMPARE** - Look for new/changed signals
4. **SWEEP** - Scan 300 MHz - 3 GHz systematically
5. **ANALYZE** - Document modulation, timing, patterns

---

## Priority Frequencies to Monitor

| Frequency | Why |
|-----------|-----|
| 400-450 MHz | Adult head resonance + ISM band |
| 433.92 MHz | European ISM (remote controls) |
| 700 MHz | Baby/child head resonance |
| 915 MHz | US ISM band |
| 2.4 GHz | WiFi/microwave frequency |

---

## SDR# Quick Settings

```
Sample Rate:    2.4 MSPS
FFT Resolution: 32768
Averaging:      10 frames
RF Gain:        Start Auto, then adjust
```

---

## The Amplification Effect

```
Layer 1:  Tiny voltage difference (microseconds)
    ↓
Layer 2:  Timing shifts cause desync
    ↓
Layer 3:  Some neurons fire that shouldn't
    ↓
Layer 4:  Effect compounds
    ↓
Layer 10: 20%+ neurons in error state
    ↓
Brain:    Billions of neurons = massive amplification
```

---

## Nernst Equation (Reference)

```
E = (RT/zF) × ln([X]out/[X]in)

E = equilibrium voltage
R = gas constant (8.314 J/mol·K)
T = temperature (Kelvin)  ← THE KEY VARIABLE
z = ion valence
F = Faraday constant (96,485 C/mol)
[X] = ion concentration
```

**Bottom line:** Temperature (T) directly affects equilibrium voltage (E), which affects neural firing.

---

## Shielding Options

| Method | Effectiveness | Notes |
|--------|--------------|-------|
| Faraday cage | Excellent | Full room enclosure |
| RF fabric | Good | Clothing, curtains |
| Window film | Moderate | Blocks external RF |
| RF paint | Moderate | Walls, ceilings |

---

## GitHub Resources

```
Neural Simulation:
https://github.com/ClintMclean74/Hodgkin-HuxleyCode

SDR Detection:
https://github.com/ClintMclean74/SDRSpectrumAnalyzer

Reradiation Detection:
https://github.com/ClintMclean74/SDRReradiationSpectrumAnalyzer
```

---

## Key Quotes

> "Neural networks are incredibly sensitive to such changes."

> "The more layers, or connections, the network has the more the effect is amplified."

> "Temperature increases significantly less than 1°C cause neurological effects."

> "Biological neural networks would not be adapted to these [pulsed RF] effects."

---

## TL;DR

1. **RF → Heat → Neural Effects** (even at 0.0001°C)
2. **Neural networks AMPLIFY** these tiny effects
3. **Current safety standards MISS** sub-thermal effects
4. **You can detect** potential attacks with $30 SDR equipment
5. **Monitor 400-450 MHz** (head resonance range)

---

*Quick reference compiled from Clint McLean's research*
