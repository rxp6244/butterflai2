# ButterflAI 2.0 — Week 04 Learning Handoff

**Status:** Week 04 conceptual tutoring completed. Ready to resume model evaluation and interpretation.

## 1. Main Experimental Result

The amplitude-dependent belt-width ablation outperformed the constant-width baseline.

| Metric | Result |
|---|---|
| Mean paired held-out gain | +0.6880 nats per hemicycle-year |
| Paired standard error | 0.2926 |
| Gain / SE | 2.35 |
| Hemicycles improved | 16 of 18 |
| Time-rescaling KS | Essentially unchanged |

**Interpretation:** Under the Week 03 comparison rule, this is a predictive win rather than a tie. The improvement is widespread across held-out hemicycles.

The unchanged temporal KS suggests that improved latitude predictions may explain the likelihood gain, but that explanation has not yet been verified.

## 2. Scientific Understanding Established

### Prediction versus physical causation

The learner initially reasoned that the lowest NLL proved amplitude controlled intrinsic belt width. Through discussion, they refined this conclusion:

- Lower held-out NLL supports predictive usefulness.
- Paired differences and standard errors establish the strength and consistency of the comparison.
- Predictive improvement does not establish a physical causal mechanism.
- Stronger magnetic fields can produce wider observed emergence patterns through thresholding even when intrinsic width is unchanged.

### Amplitude versus latitude dependence

The learner independently proposed comparing amplitude-only, latitude-only, and combined-width models, including checking whether the amplitude effect survives adjustment for latitude.

This demonstrates emerging understanding of confounding and parameter identifiability.

### Likelihood versus KS

The learner understands that held-out likelihood evaluates the two-dimensional emergence intensity, whereas time-rescaling KS evaluates the latitude-integrated temporal intensity.

An unchanged KS does not contradict an improved two-dimensional likelihood.

## 3. Week 04 Methodology

The leaderboard compares models under a fixed protocol:

- Nine development cycles, comprising 18 hemicycles.
- Leave-one-cycle-out cross-validation.
- Cycles 16, 20, and 22 remain sealed.
- Observation window: \(s\in[-6,+11]\) years.
- Latitude domain: absolute latitude 0°–60°.
- Two-dimensional quadrature mesh: 201 × 241.
- Headline amplitude source: independent sunspot-area record, using a mapping fitted only on training data.

Variant names identify model configurations, caching preserves experiment results, and the protocol fingerprint identifies the scoring conditions.

Different protocol fingerprints imply that leaderboard scores are not directly comparable.

Changing the observation window changes both the observed event set and the compensator integral, so it cannot be used to improve a model's reported score selectively.

## 4. Model-Family Concepts Reviewed

The learner discussed comparing gamma, Weibull, two-sided, lognormal, and symmetric time profiles, each analytically normalized to a peak of one.

Peak normalization does not imply equal integrated intensity or equal predicted event counts.

Ablations change one model component relative to the baseline; joint candidates change multiple components and can reveal interactions.

The Week 04 notebook also requires the learner to invent an additional model knob independently. That task remains open.

## 5. Outstanding Questions

1. Decompose the held-out two-dimensional log-likelihood into temporal and conditional-latitude contributions.
2. Determine whether the amplitude-width gain primarily reflects spatial improvement.
3. Compare amplitude-only, latitude-only, and combined-width models using paired held-out scores.
4. Examine parameter identifiability and the stability of the amplitude exponent.
5. Assess uncertainty at the cycle level, accounting for possible dependence between hemispheres.
6. Investigate influential hemicycles, including 19N.
7. Keep sealed cycles untouched during model development.

## 6. Recommended Next Learning Anchor

**Conditional-latitude likelihood**

Start from:

\[
\lambda(s)=\int\Lambda(|\lambda|,s)\,d|\lambda|
\]

and

\[
p(|\lambda|\mid s)=\frac{\Lambda(|\lambda|,s)}{\lambda(s)}.
\]

Then reason about:

\[
\log L_{\mathrm{2D}}
=
\log L_{\mathrm{time}}
+
\sum_i\log p(|\lambda_i|\mid s_i).
\]

The learner should explain what each term measures and predict which term might account for the observed amplitude-width improvement.

**Suggested opening question:**

"If amplitude-dependent width improves the conditional-latitude likelihood but leaves temporal likelihood and KS nearly unchanged, what does that tell us about the model's predictive advantage—and what does it still not prove about solar physics?"

## 7. Tutor Guidance

Continue with conceptual questioning before implementation.

Do not supply task solutions or step-by-step reference code. Encourage the learner to propose their own experiments, explain competing hypotheses, and independently invent the additional Week 04 model knob.

**Current learning assessment:** Stronger command of paired comparisons, ablation logic, reproducibility, and the distinction between statistical prediction and physical explanation. Next priority is reasoning about spatial versus temporal likelihood contributions.
