# AIRI Assistant

AIRI Assistant is a lightweight, edge-optimized voice assistant designed for real-time wake word detection and offline speech synthesis. It uses custom machine learning models trained for keyword spotting and runs efficiently on resource-constrained systems with minimal latency and memory usage.

The assistant is designed with a privacy-first approach, ensuring core functionality runs locally without requiring cloud processing.

---

## Table of Contents

- [Features](#features)
- [System Architecture](#system-architecture)
- [Repository Structure](#repository-structure)
- [Wake Word Model Development](#wake-word-model-development)
- [Dataset Preparation](#dataset-preparation)
- [Dataset Variants](#dataset-variants)
- [Feature Extraction](#feature-extraction)
- [Model Training](#model-training)
- [Model Testing and Validation](#model-testing-and-validation)
- [Deployment](#deployment)
- [Text-to-Speech](#text-to-speech)
- [Model Optimization](#model-optimization)
- [Supported Platforms](#supported-platforms)
- [Use Cases](#use-cases)
- [Future Improvements](#future-improvements)
- [License](#license)
- [Author](#author)
- [Acknowledgments](#acknowledgments)

---

## Features

- Custom wake word detection ("Hello Airi")
- Fully offline inference
- Optimized INT8 quantized machine learning models
- Synthetic and real voice training support
- Offline text-to-speech synthesis
- Docker-based Linux deployment
- Low CPU and memory usage
- Modular and extensible architecture

---

### System Architecture
```
Microphone Input
│
▼
Wake Word Detection Model
│
▼
Command Processing
│
▼
Text-to-Speech Engine
│
▼
Audio Output
```

---

## Repository Structure
Airi-assistant/
│
├── coqui-tts-synthesizer/ # Text-to-speech engine
├── models-versioned/ # Trained wake word models
├── Dockerfile # Docker deployment configuration
├── README.md # Documentation
├── LICENSE # MIT License
└── .gitignore

---

## Wake Word Model Development

The wake word detection model was developed using Edge Impulse, an end-to-end machine learning platform designed for building optimized models for edge devices.

Edge Impulse enables:

- Audio dataset collection
- Feature extraction
- Neural network training
- Model optimization
- Deployment on edge hardware

The wake word used in this project is:
Hello Airi



---

## Dataset Preparation

The dataset was divided into three balanced classes:

### Wake Word

Audio recordings containing the phrase:

Hello Airi
Recorded using real human voices with variations in:
- Accent  
- Pitch  
- Tone  
- Pronunciation  
- Environmental conditions  

At least **10 minutes of wake word audio samples** were collected to ensure reliable detection.

---

### Unknown Words

Audio samples containing unrelated speech such as:
yes, no, left, right, stop, go
This helps the model distinguish the wake word from normal speech.

---

### Noise

Includes:

- Background noise  
- Silence  
- Environmental sounds  
- Non-speech audio  

This improves model robustness in real-world environments.

---

## Dataset Variants

### Naive Dataset

The naive dataset includes:

- Real human recordings of the wake word
- Public keyword spotting datasets from Edge Impulse documentation

This provides realistic speech variation for improved performance.

---

### Synthetic Dataset

Synthetic wake word samples were generated using the Coqui TTS synthesizer located in:


coqui-tts-synthesizer/


This enables:

- Scalable dataset generation
- Controlled pronunciation
- Improved dataset balance

---

## Feature Extraction

Mel-Frequency Cepstral Coefficients (MFCC) were used for feature extraction.

MFCC helps to:

- Convert raw audio into meaningful features  
- Reduce redundant audio data  
- Highlight speech-relevant frequency components  
- Improve neural network performance  

Edge Impulse provides a Feature Explorer to visualize dataset separation and validate data quality.

---

## Model Training

A neural network classifier was used for wake word detection.

Training process includes:

1. Feature extraction using MFCC  
2. Neural network configuration  
3. Model training  
4. Performance evaluation  

After training, the following metrics were evaluated:

- Accuracy  
- Loss  
- Confusion matrix  
- On-device performance estimation  

The final model was optimized using INT8 quantization for efficient edge deployment.

---

## Model Testing and Validation

The dataset was split into:

- 80% Training Data  
- 20% Testing Data  

Testing ensures:

- Accurate wake word detection  
- Low false positive rate  
- Reliable real-world performance  

The model was also tested on unseen audio samples to validate generalization capability.

---

## Deployment

The AIRI Assistant currently supports deployment on Linux systems using Docker.

### Requirements

- Linux OS  
- Docker installed  
- Microphone access  
- Audio output device  

### Build Docker Image
```bash
docker build -t airi-assistant .

Run AIRI Assistant
docker run --device /dev/snd airi-assistant

