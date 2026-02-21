# Assistant
AIRI Assistant is a lightweight, privacy-focused, edge-optimized voice assistant designed for real-time wake word detection and on-device inference. It uses custom-trained machine learning models for keyword spotting and integrates offline speech synthesis for efficient and responsive interaction.

The assistant is optimized to run on resource-constrained systems while maintaining high accuracy and low latency.

---
# Features
* Custom wake word detection ("Hello Airi")
* Fully offline wake word inference
* Optimized INT8 quantized machine learning models
* Synthetic and real voice training support
* Offline text-to-speech using Coqui TTS
* Docker-based deployment for Linux systems
* Low memory and CPU usage
* Modular and extensible architecture

--- 
# System Architecture
The AIRI Assistant consists of the following core components: 
```
Microphone Input
       ↓
Wake Word Detection Model (Edge Impulse)
       ↓
Command Processing Logic
       ↓
Response Generation
       ↓
Coqui TTS Synthesizer
       ↓
Audio Output
```
---
#Repository Structure
