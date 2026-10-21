# Underdamped_Mpemba — matrix-continued-fraction solver for the Klein–Kramers operator

Mathematica code (Wolfram 14.2) that solves the Klein–Kramers equation — the underdamped
Fokker–Planck equation for a Brownian particle in a potential — with the matrix continued
fraction (MCF) method, for harmonic and quartic potentials.

## What it does, and what it does not

- **Works:** eigenvalues and **right eigenfunctions** of the Klein–Kramers operator.
  Parameter sweeps were run on UVA's Rivanna cluster.
- **Did not work:** the **left (adjoint) eigenfunctions**, which the Mpemba analysis needs for
  the overlap coefficient *a₂* of the slowest mode. The MCF route did not deliver them reliably
  (the attempt is in `AdjointKK.nb`), so the results in the paper below come from a different,
  perturbative approach. This repository is kept as a working right-eigenfunction solver and as a
  record of what was tried.

Paper: S. Aharony Shapira, G. Chen, M. Vucelja, O. Raz, *Extending the Mpemba effect to the
underdamped realm*, submitted to J. Phys. A: Math. Theor. (2026).
arXiv:2607.11797 — <https://doi.org/10.48550/arXiv.2607.11797>

## Where to look

| File | Role |
|---|---|
| `functionsMCF.nb` | the MCF solver and everything needed to compute *a₂* |
| `Quartic D Matrices.nb` | builds the matrices for the quartic potential used by `functionsMCF.nb` |
| `RivannaMCF.nb` | driver that runs the solver (written for UVA's Rivanna cluster) |
| `Right EIg.nb`, `AdjointKK.nb` | right-eigenfunction calculation; the left (adjoint) attempt |
| `states.wl`, `Max200Ds` | saved data |
| everything else | earlier versions kept for the record (`MCF V8.nb`, `*Apr30.nb`, `* 2.nb`, …) |

## Running it

Evaluate `functionsMCF.nb` first (it defines the solver), then run `RivannaMCF.nb`, adjusting
the paths at the top for your machine. Requires Mathematica 14 or later.
