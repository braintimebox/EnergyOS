# EnergyOS

**A situational energy-management app for iPhone.** Minimal input, useful interpretation, one practical next action.

EnergyOS is designed for real life: early starts, physically demanding work, variable energy, sleep, caffeine, recovery, and financial guardrails.

## Product thesis

EnergyOS answers:

> Given what I know about today, what is the most useful next action that fits my available resources?

It is not a generic habit tracker, a medical device, or a productivity scoreboard.

## Core loop

1. **Check in** — minimal daily inputs.
2. **Interpret** — transparent rules distinguish facts from estimates.
3. **Recommend** — one primary mission with a clear reason.
4. **Review** — record whether the action was feasible and helpful.
5. **Adapt** — review weekly patterns and cautiously adjust recommendations.

## MVP

- iPhone-first interface.
- Quick check-in: sleep duration, perceived energy (1–5), work strain (1–5), caffeine (mg).
- One daily mission and short rationale.
- Lightweight XP that rewards useful actions, never sleep deprivation or overwork.
- 14-day pilot with baseline and weekly review.
- Local-first data; optional HealthKit integration with explicit permission.
- No account, backend, AI API, or financial account integration required for the first experiment.

## Pilot: 14 days

- **Days 1–3:** baseline tracking without intentionally changing routine.
- **Days 4–7:** one feasible daily mission based on transparent rules.
- **Days 8–14:** cautiously adapt recommendations using check-ins and feedback.

Initial success hypotheses:
- Daily input takes no more than 2 minutes.
- At least 80% of planned check-ins are completed.
- At least 70% of recommendations are rated feasible.
- Compare perceived morning energy and routine adherence against baseline.
- The app itself does not increase stress or workload.

These are product targets, not validated scientific thresholds. A 14-day pilot can assess usability and detect early patterns, but cannot establish causal health effects.

## Data principles

- Collect only data needed for a decision.
- Prefer on-device processing and storage.
- Request permissions only when needed.
- Never treat missing measurements as facts.
- Do not present a synthetic “energy score” as a medical measurement.
- Support data export and deletion.

## Safety and experience rules

- Recovery takes priority over optional productivity when energy is very low or strain unusually high.
- No punishment for missed days and no streak-based guilt.
- XP is feedback, not a measure of personal worth.
- Targets are configurable and are not medical advice.
- Never recommend safety-sensitive work or driving when the user reports impairment.

## Initial technical direction

- UI: SwiftUI.
- Persistence: local store; select SwiftData or simpler storage during the technical spike.
- Health data: optional HealthKit adapter behind a permission boundary.
- Decision engine: deterministic, unit-tested rules before adding AI.
- Notifications: opt-in local notifications, quiet by default.
- Pilot metrics: calculated locally.

Avoid backend infrastructure until the pilot demonstrates a concrete need.

## Documentation

- [Product specification](docs/PRODUCT_SPEC.md)
- [14-day pilot](docs/PILOT.md)
- [Decision engine](docs/DECISION_ENGINE.md)
- [Roadmap](docs/ROADMAP.md)

## Status

**Discovery / specification.** This repository does not yet contain a working iOS app. Next: refine decision rules and the pilot protocol, then build a tiny functional prototype.
