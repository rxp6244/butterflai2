## HANDOFF — ButterflAI 2.0, Week 02

Notebook: `02_rate_1d.ipynb` · Vocabulary session completed · 8 learner turns, including this handoff request

HANDOFF\
turns: 8\
learns by: contrasts, conceptual examples, and corrective feedback\
\
domain: point processes | level: 4 | milestone: compensator and time-rescaling mechanism reached; independent Exp(1) diagnostics not yet demonstrated | anchor: time-rescaling theorem\
inhomogeneous Poisson process | claim: no | prior: none | end: introduced | "no quote"\
intensity function | claim: no | prior: none | end: deployed | "if the intensity is high, even a few days can produce a relatively large transformed gap"\
compensator | claim: no | prior: none | end: deployed | "The compensator adds up the fitted intensity between the two events"\
thinning | claim: no | prior: none | end: unused | "no quote"\
time-rescaling theorem | claim: no | prior: none | end: introduced | "no quote"\
other deployed: emergence rate, event-time term, rescaled gap\
other open: independent exponential gaps, consequences of tied timestamps\
\
domain: statistical inference | level: 3 | milestone: likelihood decomposition reached; formal goodness-of-fit interpretation not yet demonstrated | anchor: identifiability\
log-likelihood | claim: yes | prior: correct | end: deployed | "Model A would have the higher log-likelihood"\
maximum likelihood estimate | claim: no | prior: none | end: unused | "no quote"\
quadrature | claim: no | prior: none | end: introduced | "no quote"\
unconstrained parameterization | claim: no | prior: none | end: unused | "no quote"\
QQ plot | claim: no | prior: none | end: introduced | "no quote"\
Kolmogorov–Smirnov statistic | claim: no | prior: none | end: introduced | "no quote"\
identifiability | claim: no | prior: none | end: introduced | "no quote"\
profile likelihood | claim: no | prior: none | end: introduced | "no quote"\
other deployed: correlation, random variation\
other open: isolated versus systematic model departures, fitted-parameter uncertainty\
\
domain: solar cycle physics | level: 3 | milestone: amplitude–event-count association interpreted; width interpretation remains provisional | anchor: fitted width\
emergence rate | claim: yes | prior: correct | end: deployed | "it predicts a high emergence rate when many sunspot groups are actually observed"\
onset | claim: no | prior: none | end: unused | "no quote"\
other deployed: sunspot groups, hemispheric cycles, amplitude\
other open: physical interpretation of fitted width and onset

### Key observations to carry forward

The learner correctly decomposed the point-process log-likelihood into its event-time reward and compensator penalty. They initially confused short calendar-time gaps with small transformed gaps, then independently corrected the distinction: high fitted intensity causes a given interval to accumulate more compensator, producing a larger rescaled gap.

They also recognized that one unusually large transformed gap does not prove model misspecification because random variation remains possible.

Their reported correlations were \\(r=0.941\\) for event count versus amplitude and \\(r=-0.301\\) for fitted width versus amplitude. The stronger event-count association is a reasonable descriptive conclusion; interpreting fitted width physically requires examining identifiability.

Recommended next teaching step: Ask the learner to explain what systematic departures from an Exponential(1) distribution would mean in a QQ plot, then transition to identifiability and profile likelihood.
