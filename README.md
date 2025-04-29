# Investigation-of-Structural-and-Dynamical-Properties-of-Liquid-Argon

This repository contains a set of Jupyter notebooks for simulating the behavior of liquid Argon using classical molecular dynamics (MD).  
The focus is on reproducing key results from A. Rahman's 1964 study: diffusion, structural properties (RDF), and dynamical properties (VACF and spectrum).  
All simulations use a Lennard-Jones potential, linked-cell neighbor lists, and various thermostats.

---

## Project Structure

| Script/Notebook | Description |
|:----------------|:------------|
| **Diffusion Coefficient Calculation.jpynb** | Computes the Mean Squared Displacement (MSD) and diffusion constants for Argon atoms under different thermostats (NVE, Berendsen, Langevin). |
| **RDF Calculation.ipynb** | Calculates the Radial Distribution Function (RDF) of liquid Argon, focusing on structural analysis at a specified temperature. |
| **VACF Calculation.ipynb** | Computes the Velocity Autocorrelation Function (VACF) and its Fourier spectrum to analyze vibrational properties of the system. |

---

## Methods Overview

- **Lennard-Jones Interactions**:  
  Argon atoms are modeled via a truncated and shifted 12-6 Lennard-Jones potential, with $\sigma = 3.4$ Å and $\epsilon = 1.656 \times 10^{-21}$ J.
  
- **Linked-Cell Algorithm**:  
  Speeds up force computation by reducing neighbor search complexity from $\mathcal{O}(N^2)$ to approximately $\mathcal{O}(N)$.

- **Thermostats**:  
  - **NVE** (Microcanonical Ensemble): No temperature control, purely Hamiltonian evolution.
  - **Berendsen Thermostat**: Weak coupling to a heat bath, adjusts kinetic energy.
  - **Langevin Thermostat**: Includes random noise and friction forces.

- **Time Integration**:  
  Velocity-Verlet algorithm with a timestep of $2 \times 10^{-15}$ seconds.

---

## Simulation Details

- **Temperature**: Target temperature $T = 94.4\,\mathrm{K}$ unless otherwise stated.
- **Density**: $\rho = 1374\,\mathrm{kg/m^3}$.
- **Particles**: Typically 864 or 1000 particles (to match Rahman's system and test scaling).
- **Cutoff Radius**: $r_\mathrm{cutoff} = 2.5\sigma$.

---

## Features and Outputs

### Diffusion Analysis
- Calculate MSD vs. time for different thermostats.
- Extract diffusion coefficients via the Einstein relation.
- Compare diffusion constants against Rahman's reported value ($D_\mathrm{Rahman} \approx 2.43 \times 10^{-9}\,\mathrm{m^2/s}$).

### Radial Distribution Function (RDF)
- Compute and plot $g(r)$ to analyze short-range order in the liquid.
- Compare the structure to experimental and Rahman's simulation results.

### VACF and Spectrum
- Measure time correlation of velocities to study microscopic dynamics.
- Obtain the vibrational density of states by Fourier-transforming the VACF.
- Normalize the VACF and spectrum for better comparison with literature.

---

## How to Run

Each script is independent and can be run individually inside a Jupyter Notebook or Python environment.  
Simply execute the cells from top to bottom to perform the simulations and visualize the results.

---
