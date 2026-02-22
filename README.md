# Assistant
AIRI Assistant is a lightweight, privacy-focused, edge-optimized voice assistant designed for real-time wake word detection and on-device inference. It uses custom-trained machine learning models for keyword spotting and integrates offline speech synthesis for efficient and responsive interaction.

The assistant is optimized to run on resource-constrained systems while maintaining high accuracy and low latency.

---
# Features
* Custom wake word detection ("Hello Airi")
* Fully offline wake word inference
* Optimized INT8 quantized machine learning models
* Synthetic and real voice training support
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
# Repository Structure
```
Airi-assistant/
│
├── coqui-tts-synthesizer/     # Text-to-speech engine
├── models-versioned/          # Trained wake word models
├── Dockerfile                 # Docker deployment configuration
├── README.md                  # Project documentation
├── LICENSE                    # MIT License
└── .gitignore
```

# Wake Word Model Development
The wake word detection model was developed using Edge Impulse, an edge machine learning platform designed for building and deploying optimized ML models for sensor data.

## Dataset Classes
The dataset consists of three balanced classes:
* Wake Word: "Hello Airi"
* Unknown Words: unrelated speech such as "yes", "no", "left", etc.
* Noise: background sounds, silence, and environmental noise
At least 10 minutes of wake word audio was collected to ensure reliable keyword spotting performance.

## Dataset Variants
Naive Dataset
Includes:
* Real human recordings of "Hello Airi"
* High variance in accents, pitch, tone, and speaking style.
* Additional keyword spotting datasets from Edge Impulse documentation.
  This improves real-world robustness.
    
## Synthetic Dataset
The wake word dataset was synthetically generated using the Coqui TTS synthesizer located in: coqui-tts-synthesizer/
Benefits include: 
* Increased dataset scalability
* Consistent pronunciation
* Reduced manual data collection effort

---
# Signal Processing and Feature Extraction
Mel-Frequency Cepstral Coefficients (MFCC) were used for audio feature extraction.

MFCC helps:
* Convert raw audio into meaningful features
* Reduce redundant information
* Highlight speech-relevant frequency patterns

Feature Explorer visualization was used to validate dataset quality and class separation.

---
# Model Training

The wake word detection model was trained using the Edge Impulse platform, which provides an end-to-end pipeline for audio data processing, feature extraction, neural network training, and deployment optimization for edge devices.

A neural network classifier was used within Edge Impulse to train the wake word detection model.

Training included:

* Feature extraction using the MFCC (Mel-Frequency Cepstral Coefficients) signal processing block provided by Edge Impulse, which converts raw audio into meaningful feature representations.
* Neural network training and optimization using Edge Impulse’s built-in classifier, enabling efficient learning of wake word patterns.
* Confusion matrix analysis and performance metrics provided by Edge Impulse to evaluate classification accuracy and identify misclassifications.
* Performance validation on unseen test data using Edge Impulse’s testing framework to ensure reliable real-world wake word detection.

The final model was optimized using INT8 quantization through Edge Impulse’s deployment tools, ensuring efficient edge inference with low memory usage, fast execution, and minimal computational requirements.
---
# Model Testing and Validation
The dataset was split into:
* 80% training data
* 20% testing data

Testing ensured:
* Accurate wake word detection
* Low false positives
* Reliable real-world performance

---
# Deployment 
The AIRI Assistant is currently supported on Linux systems using Docker.

Requirements
* Linux-based OS
* Docker installed
* Microphone access
* Audio output device 

Running with Docker 
Build the container: docker build -t airi-assistant .
Run the container: docker run --device /dev/snd airi-assistant

---
# Text-to-Speech Engine
AIRI Assistant uses Coqui TTS for speech synthesis. 

Features:
* Fully offline
* Natural sounding voice output
* Low latency response

Directory: coqui-tts-synthesizer/

---
# Use Cases

* Personal voice assistant
* Edge AI experimentation
* Offline voice control systems
* Smart home integration
* Embedded AI projects

---
# Future Improvements

* Full command recognition pipeline
* Integration with LLMs for conversational capability
* Cross-platform native support
* Improved voice quality
* Hardware device support
