---
title: "Rocket Apogee Detection System"
excerpt: "A physics-driven software and simulation pipeline for detecting peak rocket altitude using sensor fusion and noise modeling."
collection: portfolio
---

### Rocket Apogee Detection System: Physics-Based Peak Prediction

This project focused on detecting a rocket’s apogee—the highest point of flight—by processing simulated sensor streams and modeling real-world noise. The software pipeline incorporated signal-processing logic to reliably determine peak altitude under realistic flight conditions.

**Technical Context**: MASA (Michigan Aeronautical Science Association) — Avionics Team

**Data + Signal Inputs**  
Simulated barometer, accelerometer, and gyroscope data were used to estimate altitude and velocity during flight.

**Methodology**
- Built a simulation framework in C++/Python to model ascent and descent using physics-based equations.
- Injected realistic noise into sensor channels to stress-test detection logic.
- Developed Kalman-style filtering to smooth signals and reduce altitude estimation error.
- Implemented automated apogee detection from processed data for consistent results across flight profiles.
- Used GitHub workflows and shared team conventions to maintain clean, reviewable code.

**Performance**
- Robust detection logic maintained accuracy across varying thrust profiles and high-noise environments.
- Noise modeling exposed sensor behavior sensitivities, improving algorithm tuning before hardware integration.

**Further Thoughts**
Future improvements include validating the detection pipeline with hardware-in-the-loop data and incorporating GPS fusion + adaptive filtering to improve performance under rapidly changing environmental conditions.

