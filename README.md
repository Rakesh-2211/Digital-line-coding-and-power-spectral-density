
# Digital Line Coding and Power Spectral Density Simulation

This repository contains a Python implementation for analyzing various digital line codes from scratch, without the use of dedicated communications toolbox encoders. 

## Objectives
* Generate common line codes manually.
* Compare DC content, bandwidth, and self-clocking properties.
* Estimate Power Spectral Density (PSD) using Welch's method.
* Analyze the impact of long runs of identical bits.

## Implemented Line Codes
1. Unipolar NRZ
2. Polar NRZ
3. Polar RZ
4. Manchester
5. Differential Manchester
6. Alternate Mark Inversion (AMI)

## Features
* **Mandatory Validation**: Encodes a specified 8-bit word (`[1, 0, 1, 1, 0, 0, 1, 0]`) to precisely compare signal transitions.
* **Power Spectral Density**: Uses `scipy.signal.welch` to compute the normalized PSD (in dB) to analyze the frequency bandwidth of each line code.
* **Running Digital Sum (RDS)**: Continuously integrates the signal to demonstrate baseline wander and DC component presence.
* **Long-Run Behavior Test**: Simulates random bits combined with long sequences of 0s and 1s to evaluate self-clocking capabilities (e.g., clock loss in NRZ/AMI).

## Requirements
Ensure you have the following Python libraries installed:
```bash
pip install numpy matplotlib scipy
```

## Usage
Run the main Python script to generate the visualizations and print the theoretical comparisons:
```bash
python line_coding_sim.py
```

## Visualizations Output
The script generates a comprehensive 4-panel figure:
1. **Aligned Line-Code Waveforms**: Visual validation of transitions.
2. **Normalized PSD**: Highlights bandwidth differences and DC nulls.
3. **Running Digital Sum**: Shows continuous drift for unipolar/polar NRZ versus zero drift for Manchester/AMI.
4. **Long-Run Behavior**: Demonstrates clocking failure (flatlining) in Unipolar and AMI during a 20-bit sequence of zeros.

## Theoretical Observations
* **DC Component**: Unipolar and Polar NRZ suffer from DC wander. AMI, Manchester, and Differential Manchester successfully bound the RDS to zero.
* **Bandwidth**: NRZ codes concentrate power at low frequencies, while Manchester/Differential Manchester peak at 0.75 Rb and feature a null at DC.
* **Self-Clocking**: NRZ and AMI lose synchronization during long runs of identical bits (zeros). Manchester encoding guarantees a mid-bit transition, preserving self-clocking regardless of the data sequence.
README.md
Displaying README.md.
