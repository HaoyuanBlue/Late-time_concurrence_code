# Graph spectra and late-time concurrence in a lossy reservoir network: numerical code

This repository contains the code for the article "Graph spectra and late-time concurrence in a lossy reservoir network" by Haoyuan Tian and Gourab Ghoshal. The notebook `graph_concurrence.ipynb` computes Figs. 1 to 5 and the numerical checks described in Appendix E of the article. It reads no precomputed data.

## Requirements

Python 3.11 to 3.13, with NumPy, SciPy 1.9 or later, Matplotlib, mpmath, and Jupyter. The packages are listed in `requirements.txt`. The first cell imports mpmath, so every run requires it. It provides the 40-, 60-, and 80-digit arithmetic of the precision checks. The notebook writes the versions it ran with to `results/summary.json` under `environment`.

## Running

Execute all cells in order, for example with

```
jupyter nbconvert --to notebook --execute graph_concurrence.ipynb --ExecutePreprocessor.timeout=-1
```

A complete run takes about 12 to 16 minutes on one CPU core. The first cell sets `OPENBLAS_NUM_THREADS` and `OMP_NUM_THREADS` to one unless they are already set. The random test states use the NumPy seeds 20260922 and 20260923. SciPy's `expm_multiply` chooses its internal step count with a randomized norm estimator that draws from the global NumPy random state, which the first cell seeds with 20261124. In our tests, two runs in the same environment gave identical output apart from the recorded run times and the creation dates of the PDF files. On other platforms or with other library versions, numerically located times of extrema and zeros can change in their last digits, by up to about 3e-5 at very flat maxima. In our tests no value quoted in the article changed.

## Outputs

The folders `figs/` and `results/` in this repository contain the outputs of the run archived with each release.

* `figs/fig1_model.pdf` to `figs/fig5_general.pdf`: Figs. 1 to 5 of the article, each also saved as PNG.
* `results/summary.json` and `results/validation.json`: parameters, rates, coefficient matrices, revival times, and every independent check of Appendix E.
* `results/arrays.npz`: all computed time series and pair density matrices, including the refined display trajectories.
* `results/spectral_scan.json` and `results/sector_rate_bound_stress.json`: the two bounded spectral scans.
* `results/sampling_refinement.json` and `results/scaled_trough_checks.json`: the located extrema and zeros of the displayed curves and the late rescaled troughs.
* `results/independent_display_audit.json`, `results/display_precision.json`, and `results/refined_revival_witnesses.json`: the independent audit of the displayed values, the resulting precision scale of each displayed series, and the revival witnesses.
* `results/display_comparisons.json`: a record of the plotted data for each panel, with sample counts, minima, points omitted from log axes, and the difference from the asymptotic formulas.
* `results/execution_validation.json`: the execution record.

## Notebook sections and the article

| Notebook section | Article |
| --- | --- |
| Exact dynamics | Secs. II and IV, Appendix E |
| Model and graph labels | Fig. 1 |
| Graph-selected decay and pair ratios | Sec. IV C, Fig. 2 |
| Loss feeding at a fixed one-excitation block | Sec. V C, Fig. 3 |
| Late revival times | Sec. V D, Fig. 4, Appendix E |
| Independent checks | Appendix E |
| Helpers for the equal-rate case | Appendices A 3 and C 2 |
| Bounded spectral checks | Appendices B and E |
| Detuned and strong-coupling checks of the proved bound | Appendices B and E |
| Critical concurrence without a fitted coefficient | Sec. V F, Fig. 5(a), Appendices A 5 and C 2 |
| Uniform detuning and exact equality of sector rates | Secs. III and V E, Fig. 5(b,c), Appendix A 2 |
| Independent general critical validation | Appendices C 2 and E |
| Auxiliary checks: odd cycles with $Q_{RR}=0$ and revival thresholds | Secs. IV A and V B, Appendices A 4, D, and E |
| Leading maxima and detuning | Secs. V D and V E |
| Refined display trajectories | Figs. 2 to 5, Appendix E |
| Positive late troughs after exponential rescaling | Figs. 2(d) and 5(b,c) |
| Independent verification of the displayed values | Appendix E |
| Precision-aware figures | Figs. 2 to 5 |
| Complete execution record | None |

## Citation

Please cite the article and the release of this code that you used. Each release has a version tag. The citation metadata are in `CITATION.cff`.

## License

The code is released under the MIT License. See `LICENSE`.
