# 🥁 TR-DZ: The Hacker's Groovebox (v13)

![Daisy Platform](https://img.shields.io/badge/Platform-Daisy%20Seed-yellow) ![License](https://img.shields.io/badge/License-MIT-blue) ![Status](https://img.shields.io/badge/Status-v13%20Industrial-green)

> **A DIY, Open-Source Tech House Drum Machine built on the Electro-Smith Daisy Seed.** > *Code-first, breadboard-friendly, and ready for the club.*

[![TR-DZ Demo](https://img.youtube.com/vi/K2HNfEA7Zsw/0.jpg)](https://www.youtube.com/shorts/K2HNfEA7Zsw)
*(Click above to watch the previous v9 Demo - v13 Demo coming soon!)*

---

## ⚡️ What's New in v13 (Industrial Edition)?
The **v13** update transforms the TR-DZ from a prototype into a performance instrument:
* **Procedural Randomizer:** Long-press the button to generate instant, coherent Tech-House patterns (Kick on beat, Snare on backbeat, syncopated Hats).
* **Quadratic Sidechain:** New DSP algorithm providing a heavy, "French Touch" style pumping effect between Kick and Bass.
* **Soft Clip Drive:** Optimized cubic saturation for a louder, warmer sound without CPU overload.
* **Acid Bass:** Switched from Square to **Sawtooth** wave for more aggressive harmonics.

---

## 🎛️ Audio Engine Features
The TR-DZ runs at **48kHz / 24-bit** with a custom C++ engine optimized for Arduino IDE.

| Instrument | Type | Parameters |
| :--- | :--- | :--- |
| **Kick** | Sine + Pitch Env | Decay, Pitch Drop |
| **Snare** | Triangle + White Noise | Tone Balance (Shell/Wires) |
| **Hi-Hat** | Filtered Noise | Volume, Decay |
| **Bass** | Sawtooth (PolyBLEP) | Resonance, Cutoff (Acid Style) |
| **Master** | Global FX | **Soft Clipper** + **Swing** |

---

## 🔌 Hardware Setup & Wiring

**⚠️ IMPORTANT CHANGE v13:** The Multiplexer address pins have been moved to **D3-D6** to improve USB Serial stability. Please update your wiring.

### Components
* 1x **Daisy Seed** (v1.1 or v1.2)
* 1x **CD74HC4067** (16-Channel Analog Multiplexer)
* 1x **OLED Display** (SH1106 or SSD1306, I2C)
* 1x **Push Button** (Momentary)
* 8x **Potentiometers** (10k Linear)

### Pinout Configuration

| Component Pin | Connect To (Daisy Seed) | Notes |
| :--- | :--- | :--- |
| **MUX SIG (Z)** | **A0** (ADC 0) | Analog Signal Input |
| **MUX S0** | **D3** | Address Bit 0 |
| **MUX S1** | **D4** | Address Bit 1 |
| **MUX S2** | **D5** | Address Bit 2 |
| **MUX S3** | **D6** | Address Bit 3 |
| **Button** | **D28** | Input Pullup |
| **OLED SDA** | **D11** | I2C Data |
| **OLED SCL** | **D12** | I2C Clock |

---

## 🎚️ Control Mapping (Multiplexer)

The potmeters are read via the Multiplexer using a **hysteresis algorithm** to prevent value jitter.

| Mux Channel | Parameter | Description |
| :--- | :--- | :--- |
| **C0** | **BPM** | Tempo (60 - 200 BPM) |
| **C1** | **Kick Decay** | Short thump to long Boom |
| **C2** | **Cutoff** | Master Low-Pass + Bass Filter |
| **C3** | **Resonance** | Bass "Acid" Factor |
| **C4** | **Snare Tone** | Mix between Tone and Noise |
| **C5** | **Hat Vol** | Hi-Hat Level Mixer |
| **C6** | **Swing** | Groove amount (0 - 25%) |
| **C7** | **Drive** | Master Saturation (Soft Clip) |

### Button Logic
* **Short Press:** Toggle Step (Kick)
* **Long Press (>1s):** **RANDOMIZE PATTERN** (Generates a new full beat)

---

## 🚀 Installation

1.  Install **Arduino IDE**.
2.  Install **DaisyDuino** via the Library Manager.
3.  Install **U8g2** library (for OLED).
4.  Select Board: `Generic Daisy Seed`.
5.  Upload `TR-DZ_v13.ino`.

---

## 📜 License
This project is open-source under the MIT License. Feel free to fork, hack, and build your own!

*Created by [Zifou-maker]*
