# McLean Research - Extracted Data Tables

## Comprehensive data extracted from Clint McLean's publications

---

## Table 1: Havana Syndrome Symptoms

| Symptom | Category | Mechanism (per McLean) |
|---------|----------|------------------------|
| Ringing in ears (tinnitus) | Auditory | Microwave auditory effect + neural disruption |
| Hearing loss | Auditory | Cochlear neural damage |
| Cognitive dysfunction | Cognitive | Neural network disruption |
| Memory loss (short-term) | Cognitive | Hippocampal interference |
| Fatigue | Systemic | Widespread neural inefficiency |
| Sleep problems | Systemic | Circadian/brainstem disruption |
| Dizziness | Vestibular | Vestibular system interference |
| Lack of balance | Vestibular | Cerebellar/vestibular disruption |
| Headaches | Pain | Meningeal/vascular effects |
| Nausea | Autonomic | Vagus nerve/brainstem effects |
| Pressure in ears | Sensory | Thermoelastic pressure waves |
| Buffeting sensation | Sensory | Pulsed pressure waves |

---

## Table 2: Human Body Resonant Frequencies

| Body Part / Subject | Resonant Frequency | Wavelength | Source |
|--------------------|-------------------|------------|--------|
| Whole body (adult standing) | 70-100 MHz | ~3-4 m | Gandhi et al. 1978 |
| Adult head | ~400 MHz | ~75 cm | ARRL Handbook |
| Child head (5-10 years) | ~500-600 MHz | ~50-60 cm | Calculated |
| Baby head | ~700 MHz | ~43 cm | ARRL Handbook |
| Adult torso | ~150-200 MHz | ~1.5-2 m | Literature |

### Resonance Formula
```
f_r = c / (2L × √ε_r)

Where:
- f_r = resonant frequency (Hz)
- c = speed of light (3×10⁸ m/s)
- L = characteristic dimension (m)
- ε_r = relative permittivity of tissue
```

---

## Table 3: Ion Concentrations in Neurons

| Ion | Outside Cell (mM) | Inside Cell (mM) | Ratio (Out:In) | Source |
|-----|-------------------|------------------|----------------|--------|
| Na⁺ | 440 | 50 | 8.8:1 | Johnston & Wu 1994 |
| K⁺ | 20 | 400 | 1:20 | Johnston & Wu 1994 |
| Cl⁻ | 560 | 52 | 10.8:1 | Johnston & Wu 1994 |
| Ca²⁺ | 10 | 0.0001 | 100,000:1 | Literature |

---

## Table 4: Equilibrium Voltages at Different Temperatures

| Ion | E at 6.3°C | E at 16.3°C | ΔE (10°C change) |
|-----|-----------|-------------|------------------|
| Na⁺ | +52.4 mV | +54.3 mV | +1.9 mV |
| K⁺ | -72.2 mV | -74.7 mV | -2.5 mV |
| Cl⁻ | -59.8 mV | -61.9 mV | -2.1 mV |

### Key Voltage References
| Parameter | Value |
|-----------|-------|
| Resting membrane potential | -60 to -70 mV |
| Threshold voltage | ~-55 mV |
| Action potential peak | +30 to +40 mV |
| After-hyperpolarization | -80 to -90 mV |

---

## Table 5: Hodgkin-Huxley Parameters

| Parameter | Symbol | Value | Units |
|-----------|--------|-------|-------|
| Sodium max conductance | ḡ_Na | 120 | mS/cm² |
| Potassium max conductance | ḡ_K | 36 | mS/cm² |
| Leak conductance | ḡ_L | 0.3 | mS/cm² |
| Membrane capacitance | C_m | 1.0 | µF/cm² |
| Q10 temperature coefficient | Q10 | 3 | - |
| Original squid temperature | T_squid | 6.3 | °C |

### McLean's Synaptic Parameters
| Parameter | Symbol | Value | Units |
|-----------|--------|-------|-------|
| Excitatory Na⁺ conductance | ḡ_Na_syn | 8 | mS/cm² |
| Inhibitory Cl⁻ conductance | ḡ_Cl_syn | 230 | mS/cm² |

---

## Table 6: Neural Network Error Rates

### Without Neural Noise

| Temperature Increase | Layer 5 Error | Layer 7 Error | Layer 10 Error |
|---------------------|---------------|---------------|----------------|
| +0.01°C | ~5% | ~12% | >20% |
| +0.001°C | ~2% | ~7% | ~15% |
| +0.0001°C | ~0.5% | ~1.5% | ~3.5% |

### With Neural Noise

| Temperature Increase | Layer 5 Error | Layer 7 Error | Layer 10 Error |
|---------------------|---------------|---------------|----------------|
| +0.01°C | ~7% | ~14% | >22% |
| +0.001°C | ~4% | ~9% | ~17% |
| +0.0001°C | ~2% | ~4% | ~6% |

**Note:** Standard deviation ~2.1-2.25% across 30 trials

---

## Table 7: Artificial Life Task Results

| Temperature | Food Items Found | Success Rate | Behavior Notes |
|-------------|------------------|--------------|----------------|
| Normal (6.3°C) | All (5+) | 100% | Direct paths |
| +0.0001°C | 4 | ~80% | Some wrong turns |
| +0.001°C | 2 | ~40% | Many errors |
| +0.01°C | 0 | 0% | Complete disorientation |

### Network Architecture
| Layer | Neurons | Connections |
|-------|---------|-------------|
| Input | 3 | - |
| Hidden 1-9 | 30 each | 30×30 = 900 each |
| Output | 10 | - |
| **Total** | **273** | **~8,100** |

---

## Table 8: ISM Band Frequencies

| Frequency | Bandwidth | Region | Common Uses |
|-----------|-----------|--------|-------------|
| 6.78 MHz | ±15 kHz | Global | Industrial |
| 13.56 MHz | ±7 kHz | Global | RFID, NFC |
| 27.12 MHz | ±163 kHz | Global | CB radio, RC |
| 40.68 MHz | ±20 kHz | Global | Industrial |
| 433.92 MHz | ±870 kHz | Europe | Remote controls |
| 868 MHz | Varies | Europe | IoT, sensors |
| 915 MHz | ±13 MHz | Americas | RFID, IoT |
| 2.45 GHz | ±50 MHz | Global | WiFi, Bluetooth, microwave |
| 5.8 GHz | ±75 MHz | Global | WiFi, radar |

---

## Table 9: SDR Detection Parameters

### Recommended SDR# Settings

| Parameter | Value | Notes |
|-----------|-------|-------|
| Sample Rate | 2.4 MSPS | Balance of bandwidth/CPU |
| FFT Resolution | 32768 | High frequency resolution |
| FFT Window | Blackman-Harris | Good dynamic range |
| Averaging | 10 frames | Noise reduction |
| Frequency Range | 24 MHz - 1.7 GHz | RTL-SDR limit |

### Signal Characteristics at 433 MHz

| Measurement | Value |
|-------------|-------|
| Center Frequency | 433.92 MHz |
| Typical Bandwidth | ~50 kHz |
| Signal Strength | -45 to -65 dBm |
| Modulation | OOK/ASK |
| Pulse Duration | 10-100 ms |

---

## Table 10: Tissue Dielectric Properties

| Tissue Type | Permittivity (ε_r) at 400 MHz | Conductivity (S/m) |
|-------------|------------------------------|-------------------|
| Muscle | 57 | 0.80 |
| Fat | 5.5 | 0.04 |
| Bone (cortical) | 13 | 0.09 |
| Bone (cancellous) | 22 | 0.24 |
| Brain (gray matter) | 52 | 0.70 |
| Brain (white matter) | 38 | 0.45 |
| Blood | 64 | 1.20 |
| Skin (dry) | 46 | 0.52 |
| Skin (wet) | 49 | 0.65 |

---

## Table 11: RF Safety Standards Comparison

| Standard | Organization | Thermal Threshold | Frequency Range |
|----------|--------------|-------------------|-----------------|
| C95.1-2019 | IEEE | +1°C | 0 Hz - 300 GHz |
| ICNIRP 2020 | ICNIRP | +1°C | 100 kHz - 300 GHz |
| FCC OET-65 | FCC | +1°C | 300 kHz - 100 GHz |

### McLean's Findings vs Standards

| Parameter | Safety Standard | McLean's Finding | Difference |
|-----------|-----------------|------------------|------------|
| Min. effect threshold | +1°C | +0.0001°C | 10,000× |
| Assumed mechanism | Thermal only | Neural amplification | Paradigm shift |
| Pulsed vs CW | Same limits | Pulsed more harmful | Not addressed |

---

## Table 12: Historical Research Timeline

| Year | Researcher | Discovery |
|------|------------|-----------|
| 1920s | Cazzamalli | Brain "reradiation" of EM signals |
| 1962 | Frey | Microwave auditory effect |
| 1963 | Hodgkin & Huxley | Nobel Prize for neuron model |
| 1974 | Sharp et al. | Acoustic signals from pulsed RF |
| 1978 | Gandhi et al. | Head resonance frequencies |
| 1984 | Barnes | Predicted Nernst temperature effects |
| 2016 | — | First Havana Syndrome cases |
| 2018 | Golomb | RF/microwave hypothesis published |
| 2020 | NAS | Microwave most plausible cause |
| 2022 | McLean | Sub-thermal mechanism discovered |

---

## Table 13: Four Neural Mechanisms Summary

| # | Mechanism | Type | Effect | Temperature Dependence |
|---|-----------|------|--------|----------------------|
| 1 | Further From Threshold | Inhibitory | Prevents activation | Higher T = further from threshold |
| 2 | Shorter/Thinner Spike | Inhibitory | Weaker downstream signal | Higher T = smaller spikes |
| 3 | Increased Spike Rate | Excitatory | Faster firing | Higher T = higher frequency |
| 4 | Anode Break | Excitatory | Triggers activation | T pulse end = rebound activation |

---

## Table 14: Detection Equipment Options

### Budget Setup (~$30-50)

| Component | Model | Price | Notes |
|-----------|-------|-------|-------|
| SDR Dongle | RTL-SDR Blog V3 | $30 | RTL2832U + R820T2 |
| Antenna | Included telescopic | $0 | Basic coverage |
| Software | SDR# | $0 | Windows |
| Software | GQRX | $0 | Linux/Mac |

### Advanced Setup (~$100-300)

| Component | Model | Price | Notes |
|-----------|-------|-------|-------|
| SDR Dongle | RTL-SDR Blog V3 | $30 | - |
| Dipole Antenna | RTL-SDR Blog Dipole Kit | $20 | VHF/UHF |
| Discone Antenna | Diamond D130NJ | $100 | Wideband |
| FM Filter | RTL-SDR FM Block | $10 | Reduces interference |
| LNA | RTL-SDR LNA | $30 | Improves sensitivity |
| Faraday Fabric | Various | $50+ | For shielding tests |

### Professional Setup (~$500+)

| Component | Options | Price Range |
|-----------|---------|-------------|
| SDR | HackRF One, Airspy | $150-300 |
| Spectrum Analyzer | TinySA Ultra | $100 |
| Directional Antenna | Yagi, Log-periodic | $50-200 |
| RF Shielding | Full enclosure | $200+ |

---

## Table 15: Shielding Effectiveness

| Material/Method | Attenuation at 400 MHz | Cost | Practicality |
|-----------------|------------------------|------|--------------|
| Aluminum foil (single layer) | 20-40 dB | Low | Temporary |
| Copper mesh (fine) | 40-60 dB | Medium | Moderate |
| RF shielding fabric | 30-50 dB | Medium | Wearable |
| RF blocking paint | 20-30 dB | Medium | Permanent |
| Faraday cage (proper) | 60-100+ dB | High | Best protection |
| Metallic window film | 15-25 dB | Low | Windows only |

---

*Data extracted from Clint McLean's publications and referenced sources*
*For educational and research purposes*
