# Ethylene Gas Saturation Time Analysis for FTIR Spectrometer

A physics-based modeling analysis that predicts the time required for ethylene gas at 10 ppm to reach saturation inside an FTIR spectrometer housing. The model uses a Continuous Stirred-Tank Reactor (CSTR) mixing framework to derive an analytical solution for concentration buildup as a function of volume exchanges, and additionally tracks gas bottle depletion over the course of the experiment.

## Background

When introducing a calibration or analyte gas into an FTIR spectrometer's optical housing, the system does not instantaneously reach the target concentration. Gas enters through an inlet and exits through an outlet port, and the internal concentration evolves over time according to mixing dynamics. Understanding how long this takes — and how much bottled gas is consumed in the process — is essential for planning measurements and managing consumables.

## Problem Setup

| Parameter | Value |
|---|---|
| Inlet concentration | 10 ppm ethylene |
| Flow rate | 4 LPM |
| System volume | ~1,750 cm³ (~28.7 L) |
| Gas bottle | 14 L at 240 psig |
| Initial condition | 0 ppm (purged system) |

## Approach

The analysis derives the concentration profile from the governing mass-balance ODE for a well-mixed volume with continuous flow:

$$\frac{\partial C}{\partial t} = \frac{Q}{V}C_{\text{in}} - \frac{Q}{V}C$$

This is a first-order linear inhomogeneous ODE with constant coefficients. Applying the initial condition C(0) = 0 yields the analytical solution:

$$C(t) = C_{\text{in}}\left(1 - e^{-Qt/V}\right) = C_{\text{in}}\left(1 - e^{-n}\right)$$

where *n = Qt/V* is the number of volume exchanges and *τ = V/Q ≈ 7.17 min* is the characteristic time constant for one complete air exchange.

The notebook then computes concentration at each exchange interval, tracks cumulative gas drawn from the bottle, and calculates the remaining bottle capacity as a percentage.

## Key Results

- **Time constant (τ):** ~7.17 minutes per volume exchange
- The system approaches >99% of the inlet concentration after approximately 5 volume exchanges (~36 minutes)
- Bottle depletion is tracked alongside concentration buildup, providing a practical planning tool for experiment duration vs. gas supply

## Visualizations

The notebook produces a dual-axis plot showing:
- System ethylene concentration (ppm) vs. number of volume exchanges
- Bottle gas remaining (%) vs. number of volume exchanges

## Dependencies

- Python 3.x
- `numpy`
- `pandas`
- `matplotlib`

## Usage

```bash
pip install numpy pandas matplotlib
jupyter notebook Ethylene_Saturation_analysis.ipynb
```

No external data sources are required — all parameters are defined inline. Adjust `C_in_ppm`, `Q`, or `V` in the code cell to model different experimental configurations.

## References

1. University of Washington — Problem Set on Mixing Dynamics
2. Physics Stack Exchange — Inline Chamber Fluid Replacement
3. EPA — FTIR Measurement Techniques
4. Wikipedia — Continuous Stirred-Tank Reactor
5. UCSB — Chemical Reactor Material Balance Slides
6. Math Centre UK — Ordinary Differential Equations
7. Newcastle University — Integrating Factor Method

## Author

Kyle O'Connell — MIDAC Corporation (May 2025)
