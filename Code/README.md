# Code

Numerical simulations for the MSc dissertation *Chaos Synchronization and Secure Communication* (University of Sheffield). All notebooks were run in Google Colab; ODE integration is a hand-written 4th-order Runge–Kutta unless noted otherwise.

Dissertation record: https://doi.org/10.5281/zenodo.10829273

## Contents

| Notebook | System | Coupling / scheme | What it does |
|---|---|---|---|
| `Lorenz_1.ipynb` | Lorenz | — | Single-system attractor: time series + 2D/3D phase portraits. |
| `Lorenz_returnMap.ipynb` | Lorenz | — | `scipy.solve_ivp` integration; Poincaré-style return map (y(t) vs y(t+1)) to show the chaotic structure. |
| `Rossler_1.ipynb` | Rössler | — | Single-system attractor: time series + phase portraits. |
| `Rossler_2.ipynb` | Rössler | — | Attractor shape across four values of parameter `c` (periodic → chaotic); exports a trajectory to CSV for reuse. |
| `RK 4 Master Slave.ipynb` | Lorenz | Unidirectional (Pecora–Carroll drive–response) | Master's `x` drives an identical response subsystem (`y2,z2`); shows sync error `Δy, Δz` decaying to ~0. Custom RK4. |
| `RK45 Master Slave.ipynb` | Lorenz | Same as above, **uncoupled** control case | Same setup solved with `scipy.solve_ivp(method='RK45')` for a library cross-check, systems left uncoupled to show divergence as the baseline. |
| `Old_CS.ipynb` | Lorenz | Bidirectional, all 3 states | Complete synchronization (CS): mean-absolute-error metric, sweeps coupling strength α, small trial count. |
| `New_CS.ipynb` | Lorenz | Bidirectional, all 3 states | Same as above with a Euclidean-distance error metric, more random trials, `joblib`-parallelised α-sweep. Refined version of `Old_CS`. |
| `x_coupling_CS.ipynb` | Lorenz | Bidirectional, **x-only** | CS with coupling injected through the x-variable alone (y, z uncoupled) — tests whether single-variable coupling is sufficient. |
| `GraphAnnotation.ipynb` | Lorenz | — | Reads a pre-computed error-vs-α CSV (`For_Fujisaka_E_new.csv`) and annotates the critical coupling threshold (α ≈ 11.8) for the write-up figure. |
| `Phase Sync-1.ipynb` | Rössler (detuned, ω₁≠ω₂) | Bidirectional | Average frequency difference ΔΩ vs coupling strength α — locates the phase-locking onset. |
| `New Phase Sync-1.ipynb`, `New Phase Sync-2.ipynb` | Rössler (detuned) | Bidirectional | Combines sync-error and average-frequency calculations in one parallelised α-sweep; refines `Phase Sync-1`. |
| `Secure_Communication_CS-1.ipynb` | Lorenz | CS, additive masking | Analogue message masked by adding it to the master's x-signal; recovered by subtracting the synchronized slave's x-signal. Also exports state data (`y1.csv`) used by the parameter-estimation notebook. |
| `Secure_Communication_CS-2.ipynb` | Lorenz | CS, parameter modulation | Digital (binary) message encoded by shifting the drive parameter σ; recovered from the sync-error signal, cleaned with a majority-voting filter. |
| `Secure Communication-PS.ipynb` | Rössler | Phase synchronization | Digital message encoded as a small frequency shift (±0.01) between two coupled oscillators; recovered from the phase-difference signal against a third phase-locked oscillator, cleaned with majority voting. |
| `Try parameter estimation.ipynb` | Lorenz | Auxiliary-system attack | Security check: an eavesdropper's auxiliary system, driven only by the intercepted x-signal, tries to reconstruct the master's state/parameters. Error between the auxiliary and true trajectory measures how much the scheme leaks. |

## Requirements

```
numpy
pandas
matplotlib
scipy
joblib
tqdm
ipywidgets
```

## Notes

- Several notebooks read CSVs (`x1.csv`, `y1.csv`, `For_Fujisaka_E_new.csv`, `x-coupling.csv`, ...). Most of these are committed in the sibling folder `../Graphs and Datasets/CS/`, not in `Code/` itself. A few (`x1.csv`, `y1.csv`) are session-local exports from a companion notebook and aren't committed; regenerate those by running the producing notebook first (see table above).

