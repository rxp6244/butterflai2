# HANDOFF 02 — ButterflAI 2.0, Week 01

Notebook: `01_counting_process.ipynb` Status: Tasks 1–9 completed and notebook executed, as reported by the learner. Current focus: Interpreting Fano factors, rate-matched Poisson null models, and evidence for sunspot emergence clustering.

## 1. Most recent results

At a counting-window duration of \\(\Delta=27\\) days:

| Hemisphere | Observed Fano factor | One-year null | Three-month null |
| ---------- | -------------------- | ------------- | ---------------- |
| Northern   | 4.03                 | 3.96          | 4.39             |
| Southern   | 3.79                 | 3.80          | 4.15             |

Interpretation reached: Both hemispheres exhibit overdispersion relative to a constant-rate Poisson process, but neither exhibits a consistently larger Fano factor than the rate-matched null models.

The three-month null produces greater dispersion than the observations in both hemispheres.

## 2. Key conceptual breakthrough

The learner asked:

> “Why does the three-month null produce greater dispersion than the observed data, even though it is generated from independent Poisson counts?”

This question identifies the difference between independent increments and rate heterogeneity.

For a nonhomogeneous Poisson process, disjoint-window counts are independent, but their expected values can change over time.

When windows with different expected counts are pooled:

\\[ \operatorname{Var}(N) = \mathbb{E}[M]+\operatorname{Var}(M), \\]

where \\(M\\) represents the expected count associated with a window.

Therefore,

\\[ F=1+\frac{\operatorname{Var}(M)}{\mathbb{E}[M]}. \\]

A Fano factor greater than 1 can arise from temporal variation in the underlying emergence rate without requiring dependence between events.

## 3. Why smoothing matters

A three-month smoothing window may preserve more short-timescale variation in the estimated emergence rate than a one-year window.

Consequently, the three-month null can produce greater variation in expected counts across 27-day windows.

However, a shorter smoothing window can also preserve random fluctuations in the observed data. This raises a potential overfitting concern when the same observations are used to estimate the null intensity and evaluate departures from that null.

The numerical results alone do not establish which mechanism dominates.

## 4. Scientific conclusion reached

The current results do not provide clear evidence for residual emergence clustering at the 27-day counting scale beyond the variability explained by rate-matched Poisson models.

Important qualifications:

- A Fano factor above 1 does not independently establish interactions between emergence events.
- Differences between observed and null Fano factors require uncertainty estimates before statistical significance can be assessed.
- A 27-day counting window does not directly test periodic recurrence at the solar rotation period.
- The results do not prove that emergence events are independent.

## 5. Vocabulary progress

| Domain                | Working level              | Demonstrated or discussed                                                                                                             |
| --------------------- | -------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Point processes       | Applied interpretation     | Point process, event time, counting process, inter-arrival time, Poisson process, independent increments, Fano factor, overdispersion |
| Statistical inference | Developing model criticism | Negative log-likelihood, Earth Mover's Distance, null model, sampling variability, rate heterogeneity, overfitting                    |
| Solar cycle physics   | Developing interpretation  | Emergence, hemispheric cycle, alignment coordinate, solar rotation timescale                                                          |

Terms needing further assessment: Memoryless behavior, residual clustering, statistical significance, null-distribution calibration.

## 6. Scientific conventions to preserve

- The independent replication unit is a hemispheric cycle.
- The alignment coordinate \\(s=t-t_0\\) shifts time relative to the hemisphere-specific 15° crossing without rescaling it.
- The first catalog observation defines the recorded event time, not necessarily the physical emergence time.
- Maximum observed area determines the group-selection threshold.
- The normalized latitude density \\(p(|\lambda|)\\) must not be confused with the emergence-rate intensity \\(\Lambda\\).
- Longitude modeling remains deferred.

## 7. Next learning objective

Evaluate the observed Fano factor against the distribution of Fano factors across repeated null simulations, rather than comparing only individual values.

This will help distinguish descriptive differences from statistically meaningful deviations.

Resume question: Suppose 1,000 independent simulations of the three-month rate-matched null produce a distribution of northern Fano factors centered near 4.39.

If the observed value of 4.03 falls near the middle of that distribution, what does that imply about residual clustering? How would your interpretation change if the observed value exceeded the 99th percentile of the null distribution?

Type handoff anytime for a snapshot of your progress, or wrap up when you're done.
