# Clint McLean - GitHub Code Repositories

## Comprehensive documentation of McLean's open-source software

---

## Overview

| Repository | Language | Purpose | Stars |
|------------|----------|---------|-------|
| [Hodgkin-HuxleyCode](https://github.com/ClintMclean74/Hodgkin-HuxleyCode) | C/C++ | Neural simulation from Book 1 | 0 |
| [SDRSpectrumAnalyzer](https://github.com/ClintMclean74/SDRSpectrumAnalyzer) | C# | Original RF detection tool | 12 |
| [SDRReradiationSpectrumAnalyzer](https://github.com/ClintMclean74/SDRReradiationSpectrumAnalyzer) | C | Advanced reradiation detection | 5 |

---

# Repository 1: Hodgkin-HuxleyCode

## Purpose
Companion code for the book "Solving Havana Syndrome and Biological Effects of RF Using the Hodgkin-Huxley Neuron Model"

## Structure
```
Hodgkin-HuxleyCode/
├── CMakeLists.txt          # Build configuration
├── README.md               # Documentation
├── src/                    # Source code
├── include/                # Header files
├── settings/               # Experiment configuration files
├── results/                # Output data
├── freeglut/               # OpenGL library (visualization)
├── glew-2.1.0/             # OpenGL extension library
├── libs/                   # Additional libraries
└── .vscode/                # VS Code configuration
```

## Technology
- **Language:** C/C++
- **Build System:** CMake
- **Graphics:** OpenGL (FreeGLUT, GLEW)
- **License:** GPL v2+

## Installation

### Prerequisites
```bash
# Ubuntu/Debian
sudo apt-get install cmake

# Fedora
sudo dnf install cmake

# Arch Linux
sudo pacman -S cmake
```

### Build Instructions
```bash
cd Hodgkin-HuxleyCode/build
cmake ..
cmake --build .
```

## Usage

### Command Line
```bash
HodgkinHuxley.exe settings_file.txt
```

### Example
```bash
HodgkinHuxley.exe ../settings/nn_amplification_layer_activity_testing_6_31C.txt
```

### Configuration Files (settings/)
The `settings/` folder contains configuration files to reproduce experiments from the book:

| File Pattern | Experiment Type |
|--------------|-----------------|
| `nn_amplification_*` | Neural network amplification tests |
| `*_6_31C.txt` | Tests at 6.31°C (baseline) |
| `*_temperature_*.txt` | Temperature variation experiments |

## Key Features
- Implements full Hodgkin-Huxley neuron model
- Temperature-sensitive Nernst equation calculations
- Neural network construction and simulation
- Visualization of membrane voltages and spike trains
- Configurable via text files

---

# Repository 2: SDRSpectrumAnalyzer

## Purpose
RTL-SDR Spectrum Analyzer for detection of reradiated and emitted RF energy from humans. This is the **original** detection software (Windows, C#).

## Structure
```
SDRSpectrumAnalyzer/
├── Build/                      # Compiled executables
│   └── RTLSpectrumAnalyzerGUI.exe
├── RTLSDRDevice/               # RTL-SDR device interface
├── RTLSpectrumAnalyzerGUI/     # Main GUI application
├── COPYING                     # GPL License
└── README                      # Documentation
```

## Technology
- **Language:** C#
- **Platform:** Windows
- **Hardware:** RTL-SDR dongle (RTL2832U + R820T2)
- **Libraries:** librtlsdr, libusb
- **License:** GPL

## Installation

### Prerequisites
1. Install RTL-SDR drivers using Zadig: http://www.rtl-sdr.com/tag/zadig/
2. Install Microsoft Visual C++ 2010 Redistributable (x86) if needed

### Running
Navigate to `Build/` folder and run:
```
RTLSpectrumAnalyzerGUI.exe
```

## How It Works

### Detection Methodology
1. **Proximity Detection**: Uses keyboard/mouse activity to detect when you're near the computer/antenna
2. **Signal Averaging**: Reduces noise by averaging signal strength over time
3. **Interesting Signal Detection**: Identifies signals that increase when subject is present
4. **Leaderboard**: Ranks signals by how often they correlate with subject presence
5. **Transition Analysis**: Compares signal strength before/after subject approaches

### Key Features
- **Automated Analysis**: Scans frequency ranges automatically
- **Transition Graphs**: Shows signal strength changes over 16-second windows
- **Leaderboard System**: Prioritizes most likely reradiated signals
- **Frequency Range Ranking**: Groups signals by 1 MHz bands

### User Interface
- **Record Button**: Monitor signal strength in real-time
- **Check Far to Near Transition**: Perform transition analysis
- **Frequency/Frequency Range Toggle**: Switch between single frequency and band analysis

## Usage Tips
1. Place antenna near your work area
2. Let system run to build baseline
3. Move away for 8+ seconds, then return
4. Check transition graphs for signals stronger when near
5. Signals with >100% increase when near may be reradiated

---

# Repository 3: SDRReradiationSpectrumAnalyzer

## Purpose
Advanced, faster version of the spectrum analyzer with OpenGL visualization. Supports both Windows and Linux. This is the **recommended** detection tool.

## Structure
```
SDRReradiationSpectrumAnalyzer/
├── SDRReradiation/
│   └── bin/
│       ├── Debug_Linux64/
│       ├── Release_Linux64/
│       ├── Debug_Windows/
│       └── Release_Windows/
├── GNURadioDeviceFlowgraph/    # GNU Radio integration
├── rtlsdr_lib/                 # RTL-SDR library
├── cbWorkspace.workspace       # Code::Blocks project
├── no-rtl.conf                 # Kernel module blacklist
└── README.md                   # Documentation
```

## Technology
- **Language:** C
- **Platform:** Windows & Linux
- **Graphics:** OpenGL
- **IDE:** Code::Blocks
- **Hardware:** RTL-SDR, HackRF, or GNU Radio compatible devices
- **License:** GPL

## Installation

### Linux (Ubuntu)

#### Prerequisites
```bash
# Add universe repository
sudo add-apt-repository universe
sudo apt update

# Install Code::Blocks IDE
sudo apt install codeblocks

# Install compiler if needed
sudo apt-get install build-essential

# Install OpenGL development
sudo apt-get install libgl-dev
sudo apt-get install libglu1-mesa-dev freeglut3-dev mesa-common-dev
sudo apt-get install libxss-dev

# Install GNU Radio and SDR drivers
sudo apt-get install gnuradio
sudo apt install gr-osmosdr
sudo apt-get install libusb-1.0-0-dev
```

#### Kernel Module Blacklist (if needed)
If you get "Kernel driver is active" error, create `/etc/modprobe.d/no-rtl.conf`:
```
blacklist dvb_usb_rtl28xxu
blacklist rtl2832
blacklist rtl2830
```

### Windows
1. Install RTL-SDR drivers using Zadig
2. Run from `SDRReradiation/bin/Release_Windows/`

## Usage

### Command Line Options
```
SDRSpectrumAnalyzerOpenGL [options]

Options:
  -a              Automatically detect reradiated frequency ranges
  -m [mode]       Scanning mode: normal, sessions
  -f [frames]     Required frames for sessions
  -s [freq]       Start frequency (Hz)
  -e [freq]       End frequency (Hz)
  -c [freq]       Center frequency
  -sr [rate]      Sample rate
  -S              Enable sound cues
  -rg             Show averaged previous results
```

### Example
```bash
./SDRSpectrumAnalyzerOpenGL -a -s 430000000 -e 470000000
```
(Scans 430-470 MHz automatically)

### Keyboard Controls

#### Display Toggles (1-8)
| Key | Function |
|-----|----------|
| 1 | Toggle data graph (IQ/RF Power/Energy) |
| 2 | Toggle correlation graph |
| 3 | Toggle device FFT graphs |
| 4 | Toggle FFT graph (off/2D/3D) |
| 5 | Toggle strength graph (off/2D/3D) |
| 6 | Toggle average FFT graph |
| 7 | Toggle average strength graph |
| 8 | Toggle full spectrum graph |

#### View Selection (SHIFT + key)
| Key | Function |
|-----|----------|
| SHIFT+1 | View data graph |
| SHIFT+4 | Toggle FFT/waterfall view |
| SHIFT+5 | View strength graph |
| SHIFT+8 | Toggle spectrum/waterfall |
| SHIFT+9 | Toggle results graphs |
| SHIFT+S | View session's strongest frequencies |
| SHIFT+L | View leaderboard |
| SHIFT+C | View all graphs |

#### Recording Controls
| Key | Function |
|-----|----------|
| n | Record near series data |
| f | Record far series data |
| SHIFT+N | Clear near series data |
| SHIFT+F | Clear far series data |

#### Navigation
| Key | Function |
|-----|----------|
| , | Cycle transitions back |
| . | Cycle transitions forward |
| R | Check reradiated frequencies |
| < | Cycle reradiated frequencies back |
| > | Cycle reradiated frequencies forward |
| l | Toggle graph labels |

#### Mouse Controls
| Action | Function |
|--------|----------|
| Center button + drag | Move graphs |
| Right button + drag | Rotate graphs |
| Left button + drag | Select frequency range (zoom in) |
| Right click on graph | Zoom out |
| Mouse wheel | Zoom in/out |

## GNU Radio Integration
For devices requiring GNU Radio:
1. Launch `GNURadioDeviceFlowgraph/GNURadioDeviceFlowgraph.grc`
2. Then run the analyzer

---

# Comparison of Detection Tools

| Feature | SDRSpectrumAnalyzer | SDRReradiationSpectrumAnalyzer |
|---------|--------------------|-----------------------------|
| Platform | Windows only | Windows + Linux |
| Language | C# | C |
| Graphics | Windows Forms | OpenGL (2D/3D) |
| Speed | Slower | Faster |
| GNU Radio | No | Yes |
| Recommended | No | **Yes** |

---

# Quick Start Guide

## Minimum Hardware
- RTL-SDR Blog V3 dongle (~$30)
- USB extension cable (optional, for antenna positioning)

## Recommended Frequency Ranges

| Range | Target |
|-------|--------|
| 400-500 MHz | Adult head resonance |
| 430-440 MHz | 433 MHz ISM band |
| 650-750 MHz | Child/baby head resonance |
| 900-930 MHz | US ISM band |

## Basic Detection Workflow

1. **Setup**: Connect RTL-SDR, position antenna near work area
2. **Launch**: `./SDRSpectrumAnalyzerOpenGL -a -s 400000000 -e 500000000`
3. **Baseline**: Let run for several minutes to establish baseline
4. **Test**: Move away for 8+ seconds, then return
5. **Analyze**: Check leaderboard (SHIFT+L) for correlated signals
6. **Verify**: Use transition analysis (R key) on top signals

---

# Additional Resources

## User Guides
- [SDRSpectrumAnalyzer Guide (PDF)](https://drive.google.com/open?id=1Sc6_Tbxux-O5aAFY-gAXCkrgMpNiRkjv)
- [SDRReradiationSpectrumAnalyzer Guide (PDF)](https://drive.google.com/file/d/1GixkhAa6bBUuEGLTBrWXw7OFkZQBzuxV/view)

## Research Papers
- [Detection Methods Paper](https://drive.google.com/file/d/1Kyl0xJq4ndh9y6mQPjucHfqSpRKAETyK/view)
- [Original Research Paper](https://drive.google.com/open?id=13wX8O4iqdy88WMnNP0QvVjPmfYBROFxf)

## Dependencies
- [librtlsdr](https://github.com/steve-m/librtlsdr) - RTL-SDR library
- [libusb](https://github.com/libusb/libusb) - USB communication
- [Osmocom RTL-SDR](http://osmocom.org/projects/rtl-sdr/wiki) - Project documentation

## Where to Buy Hardware
- [RTL-SDR.com](https://www.rtl-sdr.com) - Official RTL-SDR Blog store

---

*Documentation compiled from ClintMclean74's GitHub repositories*
*For educational and research purposes*
