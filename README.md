 Isolated (Developed by Spectral Garden)
*Advanced Multi-Band Drum Isolation & Frequency Sweep Processor*

**Isolated** is a specialized real-time audio plugin designed for surgical drum separation, transient management, and dynamic frequency sweeping. Powered by multi-stage transient splitters (TSS) and specialized channel frequency cross-overs, it allows producers to independently isolate, mix, and shape individual drum elements (Kick, Snare, Hats, Percussion, and Other) from a full stereo mix.

---

##  Core DSP Architecture & Signal Processing

1. **Multi-Band Crossover Engine (`channelFilters`)**: Splits incoming audio channels across dedicated frequency bands to segment percussion types.
2. **Transient/Sustain Splitter (TSS)**: Separates transient hits from body sustain per band, allowing independent manipulation of transient attack and release properties.
3. **Non-Linear Saturator & Envelope Tracker**: Adds character and analog warmth based on real-time dynamic envelope profiles.
4. **Synchronized Sidechain Ducking Engine**: Features both classic amplitude envelope ducking and DAW-tempo synchronized sidechain pump rates (1/4, 1/8, 1/16, 1/2 Beat).
5. **Dynamic Sweep Filter**: Includes a sweeping filter with adjustable Q and dynamic depth that reacts dynamically to transient energy peaks.

---

##  Control Parameter Reference

### Dynamic Channel Levels (Mix Matrix)
| Control | Range | Default | Description |
| :--- | :--- | :--- | :--- |
| **Kick Level** (`ID_KICK`) | `0.0` to `1.0` | `0.8` | Adjusts the isolated gain contribution of kick frequencies. |
| **Snare Level** (`ID_SNARE`) | `0.0` to `1.0` | `0.8` | Adjusts the isolated gain contribution of snare elements. |
| **Hats Level** (`ID_HATS`) | `0.0` to `1.0` | `0.8` | Adjusts the isolated gain contribution of high-hats/cymbals. |
| **Perc Level** (`ID_PERC`) | `0.0` to `1.0` | `0.8` | Adjusts the isolated gain contribution of auxiliary percussive hits. |
| **Other Level** (`ID_OTHER`) | `0.0` to `1.0` | `0.5` | Gain scalar for residual or remaining non-drum spectral material. |

### Sweep & Filter Controls
| Control | Range / Options | Default | Description |
| :--- | :--- | :--- | :--- |
| **Sweep Frequency** (`ID_SWEEP_FREQ`) | `20.0` to `20,000.0 Hz` | `1000.0 Hz` | Skew-mapped filter cutoff or sweep center frequency. |
| **Sweep Q** (`ID_SWEEP_Q`) | `0.1` to `8.0` | `1.0` | Resonance factor of the sweep filter. |
| **Sweep Dynamic Depth** (`ID_SWEEP_DEPTH`) | `0.0` to `1.0` | `0.5` | Intensity of how transient energy modulates the filter sweep behavior. |
| **Isolate / Remove Mode** (`ID_SWEEP_MODE`) | Boolean (True/False) | True (Isolate) | Toggles between isolating the selected frequency region or notching/removing it. |

### Dynamics & Transient Shaper Controls
| Control | Range | Default | Description |
| :--- | :--- | :--- | :--- |
| **Isolation Threshold** (`ID_ISOLATION`) | `0.0` to `1.0` | `0.15` | Sensitivity threshold for gating and separating target signals. |
| **Character Saturation** (`ID_CHARACTER`) | `0.0` to `1.0` | `0.10` | Injects harmonic saturation based on real-time envelope tracking. |
| **Transient Attack** (`ID_TRANS_ATTACK`) | `0.5` to `15.0 ms` | `1.5 ms` | Attack time constant for the transient/sustain separator. |
| **Transient Release** (`ID_TRANS_RELEASE`) | `10.0` to `300.0 ms` | `45.0 ms` | Release time constant for the transient/sustain separator. |

### Sidechain & Global Utility Controls
| Control | Range / Options | Default | Description |
| :--- | :--- | :--- | :--- |
| **Sidechain Sync Rate** (`ID_SC_SYNC_RATE`) | Off (Envelope), 1/4, 1/8, 1/16, 1/2 Beat | Off | Tempo-synced LFO pump rate ducking the rhythm section. |
| **Sidechain Offset** (`ID_SC_OFFSET`) | `-50.0` to `+50.0` | `0.0` | Time offset adjustment for sidechain ducking triggers. |
| **Mix** (`ID_MIX`) | `0.0` to `100.0%` | `100.0%` | Parallel dry/wet crossfade balance. |
| **Bypass** (`ID_BYPASS`) | Boolean (True/False) | False | Hard bypasses processor DSP path. |

---

##  State Management & Serialization
* **APVTS Framework**: Uses JUCE's robust `AudioProcessorValueTreeState` architecture to handle parameter automation and host sync.
* **State Recall**: Fully supports chunk-based preset saving and loading via standard XML serialization (`getStateInformation` / `setStateInformation`).

---

##  Compilation Requirements
* **Framework**: JUCE 8.0+
* **Build Target**: VST3 (Windows x64)
* **C++ Standard**: C++20
