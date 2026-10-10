# EnergyOS — Decision Engine v0.1

## Purpose

Select one feasible next action from a small reviewed set. The engine is a transparent decision aid, not a medical model.

## Inputs

- sleepHours: optional number
- morningEnergy: optional integer 1–5
- workStrain: optional integer 1–5
- caffeineMg: optional number
- workday: optional boolean
- userFeedback: completed / notFeasible / skipped / optional helpfulness 1–5

Every input carries a timestamp and provenance (manual, HealthKit, or derived). Unknown is represented as unknown, never as zero.

## Output

- missionId
- actionText
- rationale
- triggeredRules
- uncertainty: low / medium / high
- optional XP award

## Initial rules

Rules are provisional and must be tested for usability.

1. **High strain:** if workStrain >= 4, prioritize a low-effort recovery or basic-needs action; do not add optional productivity tasks.
2. **Low perceived energy:** if morningEnergy <= 2, suggest choosing a smaller scope and checking basic needs. Do not claim a diagnosis.
3. **Short sleep:** if sleepHours is known and < 7, consider a recovery-oriented mission and an earlier wind-down opportunity. Do not recommend compensating with excessive caffeine.
4. **Caffeine target:** if caffeineMg is at or above the user's configured daily target, do not recommend more caffeine; suggest a non-caffeine option if appropriate.
5. **Missing data:** ask at most one quick question if it materially changes the recommendation; otherwise choose a low-risk default and disclose uncertainty.
6. **Repeated infeasibility:** if a mission type is marked notFeasible twice in the recent window, reduce its priority or ask what constraint blocks it.
7. **Positive feedback:** if a mission is repeatedly feasible and helpful, keep it available but do not automatically increase difficulty.
8. **Safety override:** reported impairment, severe symptoms, or a safety-critical context overrides XP and productivity goals. The app must not encourage driving or hazardous work while impaired and should direct users to appropriate help when warranted.

## Priority order

1. Safety and urgent user needs.
2. Recovery and basic needs when strain is high.
3. One practical action aligned with the user's context.
4. Optional productivity.
5. Gamification feedback.

## XP principles

- Award XP for check-in, attempting a feasible mission, and reflecting on the outcome.
- No penalties for skipping or missing days.
- Never reward sleep restriction, overwork, unsafe activity, or ignoring symptoms.
- Do not let XP override the recommendation priority order.

## Explainability

Every recommendation should answer:
- What signal triggered this?
- What action is proposed?
- Why might it help?
- What is uncertain?

## Evaluation

Record recommendation, triggered rules, user feasibility feedback, and optional helpfulness locally. Review false positives (unnecessary advice), false negatives (missed opportunity), and user burden during the pilot.

## Known limitations

- Self-ratings are subjective and context-sensitive.
- A threshold such as 7 hours is a provisional product rule, not a universal biological boundary.
- These rules have not been clinically validated.
- Do not infer energy from HRV or other single metrics without a validated, context-appropriate method.
