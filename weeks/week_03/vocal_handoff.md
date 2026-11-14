
# ButterflAI 2.0 — Week 03 Learning Handoff

**Notebook:** `03_latent_belt.ipynb`  
**Status:** Week 03 notebook completed; held-out model comparison discussed.

## Learning Summary

This session focused on understanding the latent magnetic belt model, its Python implementation, and statistical model comparison across hemispheric cycles.

The learner asked code-focused questions about time alignment, magnetic field intensity, numerical integration, pooled fitting, simulation, and cross-validation.

Key insights:

- A shared drift timescale captures common behavior across hemicycles, while individual time shifts account for differences in cycle timing.
- The two-dimensional intensity surface models both when and where sunspots emerge.
- The point-process log-likelihood balances intensity at observed events against the total expected event count.
- Thinning generates simulated events by accepting or rejecting candidates according to the model intensity.
- A stronger magnetic belt can produce emergence over a wider latitude range without changing its intrinsic width.
- Shared-parameter fitting allows hemicycles to have common model structure and different amplitudes, but is not necessarily hierarchical partial pooling.
- Leave-one-cycle-out validation reduces the risk of overly optimistic evaluation from splitting related events.
- The amplitude-dependent width model achieved a higher reported average held-out log-likelihood than the constant-width model.
- Paired comparisons and influence analysis are needed before concluding that one model generalizes better.

## HANDOFF

**Learner turns:** 8 in the original learning discussion, followed by 6 additional code-focused questions.

**Learning style:** Contrasts, conceptual examples, code interpretation, numerical results, and corrective feedback.

**Coding preference:** Straightforward Python with readable variables, simple loops, and concise comments.

### Domain 1: Point Processes

**Level:** 4  
**Milestone:** Compensator mechanism understood; connection between the two-dimensional intensity surface, likelihood integration, and thinning discussed.

**Next anchor:** Intensity surface

| Target term | Status |
|---|---|
| Emission function | Discussed through Task 23 |
| Intensity surface | Introduced and explained |
| Thinning | Discussed through Task 27 |
| Inhomogeneous Poisson process | Introduced |

Previously demonstrated:
- Intensity function
- Compensator
- Emergence rate
- Event-time term
- Rescaled gap

Still to develop:
- Independent interpretation of the 2D intensity surface
- Time-rescaling theorem
- Independent Exp(1) gaps
- Tie-handling assumptions

### Student Understanding

The learner connected the Week 03 intensity model to Week 02, recognizing that the new model predicts both the timing and latitude of sunspot emergence.b

When discussing Task 24, the learner explained that the integral term prevents the model from artificially increasing its intensity everywhere.

> "The model can't just increase the intensity everywhere to get a better score."

For Task 27, the learner described thinning as generating candidate events and retaining them according to intensity-based probabilities. They also recognized that an underestimated maximum intensity could produce invalid acceptance probabilities.

**Remaining gap:** Explain independently how the intensity surface, compensator, and thinning algorithm relate to the same inhomogeneous Poisson process.

### Domain 2: Statistical Inference

**Level:** 4  
**Milestone:** Held-out model comparison reasoning developed; understanding of shared parameters, alignment, cross-validation, and numerical integration expanded through code discussion.

**Next anchor:** Paired comparison

| Target term | Status |
|---|---|
| Latent variable | Introduced |
| Gauge freedom | Introduced |
| Partial pooling | Discussed; independent explanation pending |
| Leave-one-cycle-out cross-validation | Discussed through Task 28 |
| Held-out log-likelihood | Deployed |
| Quadrature mesh | Discussed through Task 29 |
| Paired standard error | Introduced |

Learner quote from original discussion:

> "The amplitude-dependent width model actually had a higher held-out log-likelihood."

Other concepts discussed:
- Confounding
- Identifiability
- Data leakage
- Parameterization
- Paired differences
- Influence analysis

### Student Understanding

The learner explained that Task 21 uses a shared drift timescale to capture common solar-cycle behavior, while allowing each hemicycle to have its own time adjustment.

> "The separate shifts help align each hemicycle."

For Task 26, the learner distinguished shared model parameters from individual amplitudes and recognized that this structure does not automatically imply hierarchical partial pooling.

> "They're just fitted separately while the other parameters are shared."

The learner also identified why leave-one-cycle-out validation is preferable to randomly splitting individual events: events from the same cycle are related, so random splitting could make predictive performance appear stronger than it actually is.

When discussing the quadrature mesh, the learner recognized that inaccurate numerical integration could change the likelihood independently of any genuine improvement in the model.

> "We need to make sure the score isn't mainly changing because of the numerical calculation."

**Remaining gap:** Independently distinguish shared-parameter modeling from hierarchical partial pooling, and explain how paired standard error affects model selection.

### Domain 3: Solar Cycle Physics

**Level:** 4  
**Milestone:** Distinction between intrinsic magnetic belt width and threshold-dependent emergence spread understood; relationship between drift, amplitude, and latitude spread discussed through Tasks 22 and 30.

**Next anchor:** Drift track

| Target term | Status |
|---|---|
| Buoyancy threshold | Deployed |
| Drift track | Discussed through Task 22 |
| Belt width | Deployed |
| Magnetic field amplitude | Discussed |
| Latent magnetic belt | Introduced |

Learner quote from original discussion:

> "More of the field becomes strong enough to exceed the buoyancy threshold."

Additional concepts:
- Sunspot groups
- Hemispheric cycles
- Emergence rate
- Fitted belt width
- Latitude residuals

### Student Understanding

The learner explained how the magnetic belt model combines a drifting center, a field amplitude, and a Gaussian latitude profile.

> "The drift track tells us where the center of the belt is."

They recognized that observed sunspots represent locations where emergence occurs, rather than direct measurements of the entire magnetic field.

> "We don't directly observe the whole magnetic field."

For Task 30, the learner distinguished raw latitude spread from residual spread after subtracting the drift track. They also recognized that larger residual spread does not necessarily imply a physically wider belt because field amplitude and the buoyancy threshold can affect the observed distribution.

**Remaining gap:** Determine whether the fitted amplitude-width relationship represents a genuine physical change in belt width or an effect of the emergence threshold and model assumptions.

## Week 03 Code Summary

| Tasks | Main focus |
|---|---|
| 20–21 | Time-origin estimation and drift alignment |
| 22–23 | Magnetic belt field and 2D emergence intensity |
| 24–25 | Numerical integration, likelihood, and amplitude fitting |
| 26 | Pooled parameter estimation |
| 27 | Point-process simulation using thinning |
| 28 | Leave-one-cycle-out validation |
| 29 | Quadrature mesh sensitivity |
| 30 | Latitude spread and event-count relationships |
| 31 | Comparison of alternative width models |

The code discussion demonstrated developing understanding of how individual functions contribute to the overall modeling workflow, rather than treating each task as an isolated calculation.

## Week 03 Model Comparison Results

Reported held-out log-likelihood scores:

| Model | Score (nats per hemicycle-year) |
|---|---:|
| Constant-width model | 25.42 |
| Amplitude-dependent width model | 26.11 |
| Difference | +0.69 |

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

### Student Understanding

The learner recognized that paired comparisons are more informative than comparing the overall spread of model scores because both models are evaluated on the same hemicycles.

> "We're comparing both models on the exact same hemicycles."

They also recognized that one influential hemicycle could raise the average improvement without representing a consistent advantage across the remaining cycles.

> "It could increase the average even if most of the other cycles don't improve much."

The learner suggested checking the paired standard error and repeating the comparison without hemicycle 19N.

**Remaining gap:** Apply the paired standard error rule independently and explain why improved average held-out performance may not provide convincing evidence of better generalization.

## Next Learning Question

Suppose:

- Mean paired improvement: **+0.69 nats per hemicycle-year**
- Paired standard error: **0.85 nats per hemicycle-year**

**Question:** The amplitude-dependent width model has a higher average held-out log-likelihood, but its improvement is smaller than the paired standard error. Why should the models be treated as effectively tied under the Week 03 rule, and how might the extra width parameter affect performance on unseen solar cycles?

Explain the answer using:

1. Held-out log-likelihood
2. Paired differences and paired standard error
3. Model complexity
4. Shared parameters versus partial pooling

## Next Session Priorities

1. Interpret paired standard error and determine whether the model comparison is a tie.
2. Distinguish shared-parameter modeling from hierarchical partial pooling.
3. Examine the influence of hemicycle 19N on the average held-out improvement.
4. Connect the magnetic field, buoyancy threshold, and intensity surface to the observed latitude distribution.
5. Explain how numerical integration and quadrature mesh selection affect the point-process likelihood.
6. Revisit gauge freedom and parameter identifiability.

---

**Suggested GitHub filename:** `vocal_handoff.md`

**Resume instruction:** Paste this handoff after the Week 03 session prompt to continue the vocabulary-building discussion. Use the summarized student answers as evidence of concepts discussed, while checking independent understanding before advancing learning milestones.
