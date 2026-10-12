# HANDOFF — ButterflAI 2.0, Week 01

Notebook: `01_counting_process.ipynb` Session focus: Sunspot emergence events, statistical model evaluation, counting processes, and Poisson simulations.

## 1. Current progress

The learner discussed Tasks 1–8 and demonstrated increasing ability to identify statistical assumptions and implementation pitfalls. These discussions establish conceptual understanding, not verified completion of the notebook.

| Task | Concepts discussed                                                    | Status                                                    |
| ---- | --------------------------------------------------------------------- | --------------------------------------------------------- |
| 1–2  | Negative log-likelihood, Earth Mover's Distance, sampling variability | Conceptually understood; further metric comparison needed |
| 3    | Defining unique emergence events from first observations              | Learner shared and discussed implementation               |
| 4    | Hemispheric-cycle alignment coordinate                                | Introduced                                                |
| 5    | Sorting event times and constructing cumulative counts                | Discussed                                                 |
| 6    | Inter-arrival times, including zero-length intervals                  | Discussed                                                 |
| 7–8  | Poisson event counts, Fano factor, smoothing emergence rates          | Developing understanding                                  |

## 2. Evidence of vocabulary development

STATISTICAL INFERENCE

The learner explained why models with identical mean latitudes can receive different negative log-likelihood scores:

> “Since NLL evaluates the probability density assigned to each observed event, the models could have very different scores even with the same mean.”

They also recognized Monte Carlo sampling variability in EMD:

> “To distinguish sampling variability from an actual model improvement, I would generate multiple samples using different seeds and compare the mean EMD and its variation across runs.”

POINT PROCESSES

The learner distinguished first recorded observation from eventual maximum area:

> “We're interested in when the sunspot group first appears in the catalog, not when it reaches its largest size.”

They recognized that the event count must fluctuate between realizations:

> “But the number of events should fluctuate between realizations.”

RATE ESTIMATION

The learner independently identified the difference between a moving sum and a moving average:

> “Should I divide by the number of contributing days, including adjusting the normalization near the boundaries?”

This was the clearest example of the learner using a statistical concept to diagnose a potential methodological error.

## 3. Vocabulary ledger

| Domain                | Working level                    | Demonstrated                                                            | Introduced / needs reinforcement                                                                      |
| --------------------- | -------------------------------- | ----------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Point processes       | Developing application           | Event time, Poisson process, expected versus realized count             | Counting process, inter-arrival time, independent increments, memoryless, Fano factor, overdispersion |
| Statistical inference | Applied conceptual understanding | Negative log-likelihood, probability density, EMD, sampling variability | Null model, hard support constraints, Monte Carlo variability                                         |
| Solar cycle physics   | Introductory                     | Emergence as catalog observation                                        | Hemispheric cycle, alignment coordinate                                                               |

## 4. Important scientific conventions

- Event time: Earliest recorded observation of a unique sunspot group, not necessarily its true physical emergence.
- Selection threshold: Maximum observed group area over its recorded lifetime.
- Alignment coordinate: \\(s=t-t_0\\), measured in years relative to the hemisphere-specific 15° mean-latitude crossing. This is a time shift, not a rescaling.
- Replication unit: One hemispheric cycle.
- Latitude probability density: \\(p(|\lambda|)\\) integrates to 1 at each alignment time and must not be confused with the emergence-rate intensity \\(\Lambda\\).
- Longitude modeling: Deferred.

## 5. Outstanding learning objectives

1. Explain why a zero-density observed event can produce infinite NLL while EMD remains finite.
2. Construct examples where NLL improves but EMD worsens, and vice versa.
3. Explain why NLL and EMD cannot independently evaluate emergence counts or temporal ordering.
4. Interpret Fano factors relative to homogeneous and time-varying Poisson null models.
5. Distinguish genuine event clustering from apparent overdispersion caused by changing emergence rates.

## 6. Recommended next tutoring prompt

Question: Suppose sunspot emergence follows a nonhomogeneous Poisson process, with a higher emergence rate near the middle of a hemispheric cycle and a lower rate near its beginning and end.

Why might combining counts from different parts of that cycle produce a Fano factor greater than 1, even if the emergence events are conditionally independent?

This question connects the learner's demonstrated understanding of rate smoothing and Poisson count variability to the interpretation of overdispersion.

Tutoring approach: Continue with short, direct explanations. Introduce 2–4 terms in context, wait for a learner response, then ask them to apply the vocabulary. Avoid providing complete notebook solutions.
