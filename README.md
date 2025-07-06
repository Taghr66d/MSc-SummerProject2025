# MSc-SummerProject2025
## Project Overview:
- This project focuses on building and evaluating a machine learning model specifically a Convolutional Neural Network (CNN) to classify gravitational wave signals from cosmic string cusps against noise and blip glitches. The goal is to distinguish astrophysical signals (cusp-like) from non-astrophysical events using custom generated waveform data, synthetic noise, and EMILY, a real-world LIGO data analysis pipeline.

## Objectives:
- Generate realistic cusp waveforms using analytical models.
- Inject generated waveforms into Gaussian noise to simulate LIGO-like data.
- Train a CNN classifier to distinguish between: Cusp signals vs. Noise / Cusp signals vs. Blip glitches.
- Integrate and test the model on EMILY's trigger outputs.
- Evaluate model performance with accuracy, loss, and false alarm rate.

## Tools & Frameworks:
- Python, NumPy, Matplotlib
- TensorFlow / Keras for CNN modeling
- EMILY pipeline for injection and testing on real-like data
- Google Colab for training and prototyping
- LIGO Cluster (SSH) for scalable training

## Methodology:
1. Waveform Generation: use formulae from literature to simulate cusp signals.
   - Parameters:
      - Amplitude sampled uniformly
      - High-frequency cutoffs between 30–500 Hz
   - Inject into Gaussian noise using generator() from EMILY.
     
2. CNN Model Training:
   - Input: 1-second timeseries sampled at 1024 Hz
   - Labels: 0 = Noise / Glitch, 1 = Cusp Signal
   - Initial results show ~97% accuracy with basic architecture and 6,000 samples.
   - Plan to scale to 10k–30k samples for robustness.

3. Blip Comparison:
   - Generate blip-like glitches using EMILY’s glitch_generator() or similar.
   - Train the CNN to distinguish between cusp vs. blip.

4. EMILY Integration:
   - Project signals into LIGO detectors using project_wave().
   - Inject into EMILY's test pipeline.
   - Evaluate which triggers the classifier rejects or accepts.
   - Analyze false alarm rates and missed detections.
     
