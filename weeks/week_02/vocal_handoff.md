## HANDOFF — ButterflAI 2.0, Week 02

Notebook: `02_rate_1d.ipynb` · Updated after Task 15 discussion · 10 learner turns, including both handoff requests

HANDOFF\
turns: 10\
learns by: contrasts, conceptual examples, numerical results, and corrective feedback\
\
domain: point processes | level: 4 | milestone: compensator and time-rescaling mechanism reached; full Exp(1) diagnostics not yet demonstrated | anchor: time-rescaling theorem\
inhomogeneous Poisson process | claim: no | prior: none | end: introduced | "no quote"\
intensity function | claim: no | prior: none | end: deployed | "if the intensity is high, even a few days can produce a relatively large transformed gap"\
compensator | claim: no | prior: none | end: deployed | "there is no compensator to penalize the total expected number of events"\
thinning | claim: no | prior: none | end: unused | "no quote"\
time-rescaling theorem | claim: no | prior: none | end: introduced | "no quote"\
other deployed: emergence rate, event-time term, rescaled gap\
other open: independence of Exp(1) gaps, tie-handling assumptions, systematic model departures\
\
domain: statistical inference | level: 3 | milestone: likelihood decomposition and missing-compensator failure mechanism reached; MLE derivation not yet independently demonstrated | anchor: maximum likelihood estimate\
log-likelihood | claim: yes | prior: correct | end: deployed | "when I removed the integral term from the log-likelihood"\
maximum likelihood estimate | claim: no | prior: none | end: introduced | "no quote"\
quadrature | claim: no | prior: none | end: introduced | "no quote"\
unconstrained parameterization | claim: no | prior: none | end: introduced | "no quote"\
QQ plot | claim: no | prior: none | end: introduced | "no quote"\
Kolmogorov–Smirnov statistic | claim: no | prior: none | end: introduced | "no quote"\
identifiability | claim: no | prior: none | end: introduced | "no quote"\
profile likelihood | claim: no | prior: none | end: introduced | "no quote"\
other deployed: correlation, random variation\
other open: finite versus unbounded likelihood, fixed-window estimation, parameter uncertainty\
\
domain: solar cycle physics | level: 3 | milestone: amplitude–event-count association interpreted; fitted-width interpretation remains provisional | anchor: fitted width\
emergence rate | claim: yes | prior: correct | end: deployed | "it predicts a high emergence rate when many sunspot groups are actually observed"\
onset | claim: no | prior: none | end: unused | "no quote"\
other deployed: sunspot groups, hemispheric cycles, amplitude\
other open: physical interpretation of fitted width and onset

### Latest experimental result

In Task 15, the learner reported:

| Quantity                   | Correct fitter | Broken fitter                 |
| -------------------------- | -------------- | ----------------------------- |
| Fitted amplitude parameter | 4.59           | \\(9.54\times10^{83}\\)       |
| Predicted event count      | 1,590          | Infinity (numerical overflow) |

The learner correctly hypothesized that removing the compensator allows the event-time term to reward ever-increasing intensity without penalizing the expected total event count.

The tutor explained that for fixed rate shape,

\\[ \ell(a)=n\log a-aG+C, \qquad G=\int\_{-6}^{11}g(s)\\,ds, \\]

so the correct maximum is \\(\hat a=n/G\\), whereas removing the integral leaves \\(n\log a+C\\), which increases without bound.

Important distinction: The learner proposed the correct mechanism, but has not yet independently derived the maximum or explained the optimizer's behavior using derivatives.

### Recommended next step

Return to the unanswered question:

> If we restore the compensator but integrate only over the active years, excluding quiet years near the boundaries, is the resulting maximum likelihood estimate valid for the original 17-year observation window?

Then move toward identifiability and profile likelihood, particularly whether fitted onset and width are sufficiently constrained to support physical interpretation.
