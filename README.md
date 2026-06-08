# Space Intelligence Digital Twin

![Status](https://img.shields.io/badge/status-prototype-blue)
![Tech](https://img.shields.io/badge/stack-HTML%2FCSS%2FJS-orange)
![Domain](https://img.shields.io/badge/domain-Digital%20Twins%20%2F%20Smart%20Buildings-green)

A browser-based **digital twin prototype** that integrates a photorealistic 3D environment, simulated real-time environmental sensing, and a rule-based decision-support system for smart indoor environments.

---

## Overview

This project demonstrates a lightweight **digital twin of a university workspace**. It combines a spatial 3D reconstruction with live environmental simulation and an explainable decision-support engine.

The goal is to explore how digital twins can enhance:

- Situational awareness
- Environmental monitoring
- Human-centric space optimization
- Decision-making in smart buildings

---

## Live Demo

https://harmonious-raindrop-f4e390.netlify.app/

---

## Features

### Photorealistic 3D Environment

- 3D room reconstructed using Polycam
- Interactive browser-based navigation
- Spatially anchored overlays
- Real-world visual fidelity

---

### 📊 Real-Time Sensor Layer (Simulated)

| Sensor           | Description                    |
| ---------------- | ------------------------------ |
| Occupancy        | Number of people in the room   |
| Temperature      | Indoor temperature (°C)        |
| CO₂ Level        | Air quality indicator (ppm)    |
| Active Devices   | Estimated connected devices    |
| Engagement Score | Derived productivity indicator |

Sensor values are generated using **controlled stochastic simulation** to reflect realistic environmental variability.

---

## 🧠 Environmental Simulation Model

The system uses a **dependency-based causal model** rather than independent random values:

- Occupancy → CO₂ concentration
- Occupancy → Temperature
- CO₂ + Temperature → Engagement Score

This creates realistic interdependencies between environmental variables.

---

## ⚙️ Decision Support Engine

A rule-based reasoning system continuously evaluates conditions and generates actionable recommendations.

### Example Rules:

- Increase ventilation when CO₂ exceeds threshold
- Activate cooling when temperature rises
- Detect overcrowding based on occupancy density
- Reduce energy waste from excessive device usage

An **explainable Decision panel** shows reasoning behind each decision.

---

## 🏗️ System Architecture

```text
3D Room Reconstruction (Polycam)
            │
            ▼
   Sensor Simulation Layer
            │
            ▼
 Environmental State Model
            │
            ▼
 Rule-Based Decision Engine
            │
            ▼
 Recommendations + Explainability Layer
```
