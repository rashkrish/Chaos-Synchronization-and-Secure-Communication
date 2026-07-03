# Chaos Synchronization and Secure Communication

MSc dissertation (Mathematical and Theoretical Physics, module MAS6600, University of Sheffield). Numerical study of synchronization in coupled chaotic Lorenz and Rössler systems, and its use as a physical-layer secure-communication scheme.

## Theory

Chaos synchronization is treated as a bridge between chaos theory and its practical applications. The dissertation replicates known results on Complete and Phase Synchronization, then builds Secure Communication models on top of them.

- **Complete (identical) synchronization** — two identical chaotic systems converge to the same trajectory once coupling strength exceeds a critical value, achieved either by directly coupling their state vectors or in a drive–response (master–slave) configuration.
- **Phase synchronization** — the phases of two coupled chaotic systems lock to a bounded difference while their amplitudes stay uncorrelated and hyper-chaotic.
- **Lag synchronization** — the systems reach identical states with a time shift, which shrinks as coupling strength increases; not implemented in `Code/`.
- **Generalized synchronization** — a functional relationship links the trajectories of two non-identical coupled systems; not implemented in `Code/`.
- **Secure communication** — a message is masked in a chaotic carrier and recovered once the transmitter and receiver synchronize — implemented here for analog and digital signals via complete synchronization, and for a digital signal via phase synchronization.

**Implementation:** all synchronization schemes above are demonstrated numerically for the Lorenz and Rössler systems, with ODE integration by a hand-written 4th-order Runge–Kutta (one notebook cross-checks against `scipy.solve_ivp`). A further notebook checks how much of the transmitting system an eavesdropper could reconstruct from the intercepted signal alone.

## Contents

| Path | Description |
|---|---|
| `MAS6600Dissertation_Rashmi_Sarwal.pdf` | Full dissertation. |
| `Literature_Review.pdf` | Literature review. |
| `Code/` | All notebooks (Lorenz/Rössler dynamics, master–slave sync, complete sync, phase sync, secure communication, parameter-estimation security check). See [`Code/README.md`](Code/README.md) for a breakdown of each notebook. |
| `Graphs and Datasets/` | Output figures (PDF) and intermediate CSVs referenced by the notebooks, including the `CS/` subfolder for the complete-synchronization sweeps. |
| `LICENSE` | MIT. |

## Citation

- DOI: https://doi.org/10.5281/zenodo.10829273
- Resource type: Dissertation
- Publisher: Zenodo
- Languages: English

## License

MIT — see [LICENSE](LICENSE).
