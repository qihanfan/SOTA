Overview：
SOTA estimates the Superiority Onset Time (SOT) and post-onset hazard ratio (HR) for PD-1/PD-L1 inhibitors using reconstructed Kaplan-Meier (K-M) survival curves. 
It is designed to address time-dependent effects such as delayed therapeutic response and crossing survival curves, which violate the proportional hazards assumption and may obscure true treatment benefits in conventional Cox models.

Method Summary：
1. K-M Curve Reconstruction
   Uses the IPDfromKM R package to extract individual patient data (IPD) from published survival curves.

2. Model Classification
   Delayed models: HR ≈ 1 before SOT, HR < 1 after.
   Crossover models: HR > 1 before SOT, HR < 1 after.

3. Piecewise Cox Regression
   Pooled event times used to generate 200 candidate breakpoints (excluding top/bottom 5%). Breakpoints limited to ≤ 12 months.
   Piecewise Cox models fitted with constraints based on model type.
   Optimal SOT identified via AIC minimization.
   Bootstrap Analysis
   1000 bootstrap resamples used to estimate 95% CI for SOT.

4. Post-onset HR Estimation
   Landmark analysis using SOT as the landmark time.



