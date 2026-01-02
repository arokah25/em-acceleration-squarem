# EM Acceleration Methods for Gaussian Mixture Models

This repository contains an implementation and empirical evaluation of
acceleration methods for the Expectation–Maximization (EM) algorithm applied to
Gaussian mixture models (GMMs), with a particular focus on the SQUAREM
(Squared Extrapolation Method) algorithm.

The project studies whether EM acceleration can substantially reduce
computational cost while preserving statistical accuracy and uncertainty
quantification.

---

## Project Overview

The EM algorithm is widely used for maximum likelihood estimation in mixture
models but is known to converge slowly when mixture components overlap.
This project investigates SQUAREM, a vector extrapolation method designed to
accelerate fixed-point iterations such as EM, without requiring gradients or
Hessians.

The main goals are:
- To compare convergence behavior of standard EM and SQUAREM
- To benchmark computational efficiency (iterations and wall-clock time)
- To assess whether acceleration affects statistical uncertainty estimates

---

## Methodology

### Model
- Univariate Gaussian mixture model with \(K = 3\) components
- Synthetic data with partially overlapping components to induce slow EM
  convergence

### Algorithms
- Standard EM algorithm
- SQUAREM acceleration applied to the EM fixed-point mapping

### Evaluation
- Convergence monitored via observed-data log-likelihood
- Computational efficiency measured by iteration count and runtime
- Statistical uncertainty assessed using a parametric bootstrap procedure

Uncertainty quantification is performed after convergence, ensuring that
bootstrap confidence intervals are valid for both EM and SQUAREM despite
differences in optimization paths.

---

## Results Summary

- **Convergence:**  
  SQUAREM converges in substantially fewer iterations than standard EM while
  preserving monotone likelihood ascent.

- **Efficiency:**  
  SQUAREM achieves more than an order-of-magnitude reduction in iteration count
  and approximately a \(3.75\times\) speedup in wall-clock time.

- **Statistical Accuracy:**  
  Final maximum likelihood estimates obtained via EM and SQUAREM are essentially
  identical.

- **Uncertainty Quantification:**  
  Parametric bootstrap percentile confidence intervals for
  \((\pi, \mu, \sigma^2)\) are nearly identical for EM and SQUAREM, confirming
  that acceleration does not affect inferential validity.

---

## Repository Contents

- `EM_Acceleration.ipynb`  
  Jupyter notebook containing:
  - EM and SQUAREM implementations
  - Convergence diagnostics
  - Computational benchmarking
  - Parametric bootstrap uncertainty analysis

- `EM_Acceleration_methods_report.pdf`  
  Written project report detailing methodology, theory, experiments, and results.

---

## Software

- Python
- NumPy
- SciPy
- Matplotlib

---

## References

Kuroda, Y. and Geng, J. (2022).  
*Acceleration of the EM Algorithm*.  
Statistical Science, 37(1), 123–145.

Varadhan, R. and Roland, C. (2008).  
*Simple and Globally Convergent Methods for Accelerating the Convergence of EM*.  

---
