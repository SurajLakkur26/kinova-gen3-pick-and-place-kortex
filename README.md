# Kinova Gen3 Pick-and-Place with Kortex API

This repository contains a modular Python implementation of a **pick‑and‑place task** on the **Kinova Gen3 (7‑DOF) robot** using the **Kinova Kortex API**. The lab task arranges two blocks into a **“T” shape** using Cartesian movements and gripper commands.

## 1. Project Overview

The **Kinova Gen3** is an ultra‑lightweight 7‑DOF robotic arm designed for mobile and collaborative applications. It integrates with other technologies via the **Kortex API** and supports programming in C++ and Python.

In this project:

- Python and the Kortex API are used to control the Gen3.
- Multiple **Cartesian movements** and **gripper commands** are defined for a pick‑and‑place task.
- The robot executes a sequence to place two blocks into a **“T” configuration**, demonstrating precise Cartesian control and basic task automation.

This work was carried out as part of a **Robotics Lab** at Hochschule Furtwangen University.

## 2. Requirements

```txt
python>=3.9
kortex_api # from Kinova Kortex SDK (not on PyPI)
numpy
```

## 3. Quickstart

```bash
# Clone repository
git clone https://github.com/<your-username>/kinova-gen3-pick-and-place-kortex.git
cd kinova-gen3-pick-and-place-kortex

# (Optional) create and activate virtual environment
python -m venv .venv
source .venv/bin/activate      # Windows: .venv\Scripts\activate

# Install Python dependencies
pip install -r requirements.txt
```

## 4. Architecture

The code is organized into three main modules:

- `src/kinova/motions.py`  
  Home motion and reusable Cartesian motion helpers (relative moves using the current tool pose).

- `src/kinova/gripper.py`  
  Gripper **open / close** commands implemented via Kortex gripper messages (speed and position control).

- `src/kinova/pick_and_place.py`  
  Main script that orchestrates the full pick‑and‑place sequence to realize the “T” shape using motions and gripper actions.

Kinova’s **`utilities`** module from the Kortex SDK is used for:

- Device connection (IP, username, password).  
- Argument parsing for network configuration.  

> Note: This repository assumes that the **Kinova Kortex SDK** is already installed and that `kortex_api` and `utilities` are importable.
