# Ostriker-Peebles Galaxy Stability Simulation

An N-body simulation demonstrating the landmark 1973 discovery by Jeremiah Ostriker and Jim Peebles: **Galactic disks are inherently unstable without a massive, invisible Dark Matter halo.**

---

## 🌌 Scientific Background

Before 1973, astronomers believed galaxies were composed primarily of the stars we could see. Ostriker and Peebles simulated rotating disks of stars and found that they were **violently unstable**. Without extra mass, the disks would quickly break symmetry, form a massive rotating "bar," and eventually heat up into a chaotic blob.

They determined that for a galactic disk to remain stable (like our Milky Way), it must be embedded in a massive, invisible halo of **Dark Matter**.

This project visualizes that phenomenon side-by-side:

- **Left Panel**: A disk of stars without Dark Matter (Unstable).
- **Right Panel**: A disk embedded in a Dark Matter halo (Stable).

---

## 🚀 Running the Simulation

This project is a single-file, zero-dependency web application. It runs entirely in your browser using your computer's GPU/CPU.

### Quick Start

**File**: `index.html`

1. Download the `index.html` file.
2. Double-click it to open in any modern web browser (Chrome, Safari, Edge, Firefox).

### Controls

- **Restart**: Resets the simulation to time *t* = 0.
- **Pause**: Freezes the simulation for closer inspection.
- **Parallax**: Move your mouse around the screen to shift the 3D perspective.

---

## ⚙️ Technical Details

### Physics Engine
- Direct summation N-body integrator (*O*(*N*²) complexity).
- **Integrator**: Semi-implicit Euler / Leapfrog (Symplectic) for energy conservation.

### Force Calculation
- **Gravity**: Softened gravitational force to prevent singularities at *r* → 0.
- **Dark Matter**: Modeled as a static external potential (Plummer Sphere).

### Initial Conditions
- **Spatial**: Rejection sampling used to generate an exponential surface density profile (Σ(*r*) ∝ *e*<sup>-*r*/*R*<sub>d</sub></sup>).
- **Velocity**: Particles are initialized in circular orbits based on the enclosed mass (baryonic + dark matter) to start in equilibrium.

---

## 🖥️ Implementation Notes

The simulation uses *N* = 3000 particles (1,500 per galaxy), requiring ~9 million gravitational interactions per time step.

Implementation details:
- **Typed Arrays**: `Float32Array` for physics calculations.
- **Memory Management**: Pre-allocated force arrays.
- **Rendering**: Canvas API with additive blending.

---

## 📚 References

**Ostriker, J. P., & Peebles, P. J. E.** (1973). *A Numerical Study of the Stability of Flattened Galaxies: or, can Cold Galaxies Survive?* The Astrophysical Journal, **186**, 467-480.  
DOI: [10.1086/152513](https://doi.org/10.1086/152513)  
ADS: [1973ApJ...186..467O](https://ui.adsabs.harvard.edu/abs/1973ApJ...186..467O)

---

## 📜 License

MIT License - feel free to use this for educational purposes, demonstrations, or as a base for more complex N-body codes.

---

## 🎓 Educational Use

This simulation is ideal for:
- Undergraduate/graduate astronomy courses
- Physics demonstrations
- Public outreach events
- Understanding the historical importance of dark matter discovery

Open `index.html` in your browser to run the simulation.

