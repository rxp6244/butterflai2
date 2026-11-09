
# ButterflAI 2.0 — Week 03 Learning Handoff

**Notebook:** `03_latent_belt.ipynb`  
**Status:** Week 03 notebook completed; held-out model comparison discussed.

## Learning Summary

This session focused on understanding magnetic belt width, buoyancy thresholds, and statistical model comparison across hemispheric cycles.

Key insights:

- A stronger magnetic belt can produce sunspot emergence over a wider latitude range without changing its intrinsic width.
- The amplitude-dependent width model achieved a higher reported average held-out log-likelihood than the constant-width model.
- A higher average score does not automatically establish that one model generalizes better.
- Paired comparisons help isolate differences in predictive performance across the same held-out hemicycles.
- Individual hemicycles, particularly 19N, may have a disproportionate influence on the average improvement.

## HANDOFF

**Learner turns:** 8  
**Learning style:** Contrasts, conceptual examples, numerical results, and corrective feedback.

### Domain 1: Point Processes

**Level:** 4  
**Milestone:** Compensator mechanism understood; interpretation of the two-dimensional intensity surface still needs demonstration.

**Next anchor:** Intensity surface

| Target term | Status |
|---|---|
| Emission function | Not yet deployed |
| Intensity surface | Not yet deployed |

Previously demonstrated:
- Intensity function
- Compensator
- Emergence rate
- Event-time term
- Rescaled gap

Still to develop:
- Inhomogeneous Poisson process
- Thinning
- Time-rescaling theorem
- Independent Exp(1) gaps
- Tie-handling assumptions

### Domain 2: Statistical Inference

**Level:** 4  
**Milestone:** Held-out model comparison reasoning developed; interpretation of paired standard error remains to be demonstrated.

**Next anchor:** Paired comparison

| Target term | Status |
|---|---|
| Latent variable | Introduced |
| Gauge freedom | Introduced |
| Partial pooling | Mentioned in an appropriate comparison question; independent explanation pending |
| Leave-one-cycle-out cross-validation | Introduced |
| Held-out log-likelihood | Deployed |
| Quadrature mesh | Introduced |

Learner quote:

> "The amplitude-dependent width model actually had a higher held-out log-likelihood."

Other concepts discussed:
- Confounding
- Identifiability
- Data leakage
- Parameterization
- Paired differences
- Paired standard error
- Influence analysis

### Domain 3: Solar Cycle Physics

**Level:** 4  
**Milestone:** Distinction between intrinsic magnetic belt width and threshold-dependent emergence spread understood.

**Next anchor:** Drift track

| Target term | Status |
|---|---|
| Buoyancy threshold | Deployed |
| Drift track | Introduced |
| Belt width | Deployed |

Learner quote:

> "More of the field becomes strong enough to exceed the buoyancy threshold."

Additional concepts:
- Sunspot groups
- Hemispheric cycles
- Magnetic field amplitude
- Emergence rate
- Fitted belt width

## Week 03 Model Comparison Results

Reported held-out log-likelihood scores:

| Model | Score (nats per hemicycle-year) |
|---|---:|
| Constant-width model | 25.42 |
| Amplitude-dependent width model | 26.11 |
| Difference | +0.69 |

**Note:** Confirm score signs against the notebook output.

The learner also reported a between-hemicycle score spread of approximately 18 nats per hemicycle-year.

Hemicycle **19N** was identified as potentially influential.

### Interpretation

The amplitude-dependent width model has a higher reported average held-out score.

However, this is not sufficient by itself to conclude that the model is superior.

For each held-out hemicycle, define:

\[
d_h = L_{\mathrm{amplitude},h} - L_{\mathrm{constant},h}
\]

Then calculate:

\[
\bar d = \frac{1}{H}\sum_{h=1}^{H}d_h
\]

and

\[
SE(\bar d) = \frac{SD(d_h)}{\sqrt{H}}
\]

The Week 03 comparison rule treats a mean improvement smaller than its paired standard error as a tie.

It is also useful to examine whether the improvement is broadly distributed across hemicycles or dominated by an influential case such as 19N.

## Next Learning Question

Suppose:

- Mean paired improvement: **+0.69 nats per hemicycle-year**
- Paired standard error: **0.85 nats per hemicycle-year**

**Question:** Under Week 03's comparison rule, should the amplitude-dependent width model be considered better, or should the models be treated as effectively tied?

Explain the answer using:

1. Held-out log-likelihood
2. Paired differences
3. Partial pooling

## Next Session Priorities

1. Interpret the paired standard error and decide whether the model comparison is a tie.
2. Distinguish shared-parameter modeling from hierarchical partial pooling.
3. Examine the influence of hemicycle 19N.
4. Connect the fitted amplitude-width relationship to the latent magnetic belt's physical interpretation.
5. Revisit the emission function, gauge freedom, and two-dimensional intensity surface.

---

**Suggested GitHub filename:** `vocal_handoff.md`

**Resume instruction:** Paste this handoff after the Week 03 session prompt to continue the vocabulary-building discussion.
