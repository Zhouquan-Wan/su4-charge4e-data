# Data

Twelve CSV files provide processed QMC data and accompanying ED benchmark
references for *Quantum Charge-4e Superconductivity and Possible Deconfined
Pseudocriticality in the Attractive SU(4) Hubbard Model*.

All energies use `t = 1`. Filling is per flavor; total density is four times
the filling. `U` denotes the interaction strength.

## Files

| Files | Figures | Contents |
|---|---|---|
| `scalar_observables.csv` | 2, 3(a), S7 | Eighth-filling R2e, M2, C4, and Rphi |
| `scalar_exponents.csv` | 3(b,c), S6 | Effective exponents and crossings for 26 size pairs |
| `fig5_benchmark.csv` | 5(a,b) | Bridge/no-bridge estimates and ED references |
| `fig5_real_space.csv` | 5(c) | Quartet correlations at ordered separations |
| `s8_green.csv` | S8(a) | Effective Green functions and reported errors |
| `s8_gap.csv` | S8(b) | Finite-size gaps and reference extrapolations |
| `s9_value_error.csv` | S9 | Pairing structure-factor grids |
| `s10_value_error.csv` | S10 | Interflavor density structure-factor grids |
| `s11_observables.csv` | S11(a), inset | Quarter-filling R2e, M2, and C4 |
| `s11_exponents.csv` | S11(b,c) | Effective exponents for seven size pairs |
| `s12_value_error.csv` | S12 maps | C4-averaged interflavor real/momentum grids |
| `s12_maxima.csv` | S12 size dependence | Normalized peak estimates and errors for main and late series |

## Columns and observables

Each CSV row records an observable at one parameter or grid point, a size
pair, or an extrapolated result. Parameter columns identify the measurement;
value and error columns supply the processed estimates and the error bars
shown in the figures. Exponent tables give `nu`, `eta`, and `U_cross` with
their corresponding error columns. ED references have no statistical error
bars. The CSV files contain no row-number index.

- `R2e = 1 - S2e(k_min)/S2e(0)`.
- `M2 = S2e(0)/L^2`.
- `C4` is the quartet correlator at `(L/2,L/2)`, with the manuscript's
  Hermitian-conjugate convention; no extra factor of two is needed.
- `Rphi` is the interflavor hopping correlation ratio.
- `S_inter` is the Fourier transform of the connected interflavor density
  correlator, summed over 12 ordered distinct-flavor pairs. There is no
  additional Fourier size normalization.

Spatial tables provide integer indices `ix,iy`, physical coordinates `x,y`,
and a `space` label. Native grids contain each measured point once.
Periodic endpoints are repeated only for display. S12 real-space onsite
values remain in the file and are masked only when plotting. Preserve the
`point_index` order and repeated radii in Fig. 5(c).

## Fits and plotting

**Extrapolations.** Fits use absolute-sigma diagonal weighted least squares,
`X(Leff) = X_inf + a*Leff^(-p)`, with `Leff = sqrt(L1*L2)`.
Eighth-filling fits select `Leff >= 32` and size gaps 8, 12, 16, 20;
quarter-filling fits select `Leff > 20` and gap 8. Exponent powers span
0.5–2; crossing-drift powers span 1–2. The representative O(6) power is
0.758. Gray bands are the union of fitted means plus/minus conditional
one-sigma errors across the stated fit families, using the full intercept/
amplitude covariance. They are model-sensitivity envelopes, not a single-fit
confidence interval. Cross-pair measurement covariance is not used.
Fig. 3(a) uses fixed display parameters `Uc=0.88956`,
`inverse_nu=1.360`.

**S8.** The notebook plots the effective Green functions and their reported
errors directly from the table. For each `U`, it fits the finite-size gaps to
`Delta(L) = a + c*L^(-p)` with `p = 1, 2`, using absolute-sigma diagonal
weighted least squares. Infinite-size rows are reference values; the notebook
recalculates the extrapolations from the finite-size gaps. The fitted errors
are conditional on the selected model and reported input errors.

**S10.** Reported errors do not include incomplete mixing or equilibration
bias; this limitation remains relevant at strong coupling.

**S12.** The maps use fourfold rotational averaging. Peak values and their
errors are divided by `L^2`. The `main` and `late` series are correlated.
Rotational averaging does not establish orientation mixing, and the late
series retains strong-coupling drift. The size curves connect measurements;
they are not fits.
