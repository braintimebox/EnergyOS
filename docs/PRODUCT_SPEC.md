# EnergyOS — Product Specification v0.1

## 1. Problem

The user has limited time and energy around an early, physically demanding workday. A conventional habit tracker adds tasks and tracking overhead. EnergyOS should interpret a small amount of context and recommend one useful, feasible action.

## 2. Target scenario

Initial design scenario: early start (work begins around 06:00–07:00 and ends around 16:00–17:00), with limited bandwidth after work. This is a configurable scenario, not a hard-coded assumption about every user.

## 3. Primary user promise

**In under 30 seconds, understand today's priority and the next action.**

The daily screen must answer:
1. What is my current context?
2. What matters most today?
3. What is the one next action?
4. Why is it recommended?
5. How do I report whether it helped?

## 4. Minimum inputs

Required manual inputs for the first prototype:
- Sleep duration (hours; user-entered or optionally imported).
- Perceived energy, 1–5.
- Work strain, 1–5.
- Caffeine amount in mg, with quick-add presets.

Optional context:
- Workday / day off.
- Available time for recovery.
- A short outcome rating after a mission.

Avoid asking for weight, location, HRV, detailed nutrition, or broad health history in the first version. Add a data source only if it changes a decision that can be explained.

## 5. Main screens

### Today
- Compact check-in.
- One recommended mission.
- Brief rationale and confidence / uncertainty label.
- Complete, skip, or “not feasible” actions.
- XP feedback without punishment.

### Review
- Seven-day trend for sleep, perceived energy, work strain, caffeine, and mission feasibility.
- Clear distinction between recorded data and inferred patterns.
- One suggested adjustment at a time.

### Settings
- Wake-time range and work schedule.
- Personal caffeine target.
- Notification preferences and quiet hours.
- Data permissions, export, and deletion.

## 6. Recommendation design

- Rules first; AI is not required for the core loop.
- Each recommendation must be traceable to input signals and a named rule.
- Prefer one action over a list.
- Include a short “why this” explanation.
- If inputs are missing, ask one lightweight question or use a safe generic suggestion; do not invent values.
- Never imply that correlations prove causation.

## 7. Gamification

XP rewards actions under the user's control: check-in, trying a feasible mission, and reviewing outcomes. XP must not reward reduced sleep, excessive work, unsafe behaviour, or ignoring symptoms.

No loss of levels for missed days. No streak freeze economy, shame language, or manipulative notifications.

Initial scoring is a hypothesis to test, not a scientifically calibrated measure of energy.

## 8. Privacy

- Local-first by default.
- Explicit, feature-specific HealthKit permission.
- No financial account connection in MVP.
- No cloud AI transmission of personal health data in MVP.
- Explain what is stored and why.
- Provide deletion and export paths.

## 9. Non-goals for MVP

- Medical diagnosis or treatment.
- Predicting exact physiological energy.
- Automated control of banking or spending.
- Complex social leaderboards.
- Subscription or monetization mechanics.
- Large AI agent/backend architecture.

## 10. MVP acceptance criteria

- A check-in can be completed in under 30 seconds.
- Today screen presents one actionable mission.
- Each recommendation shows its rationale.
- User can complete, skip, or mark a mission not feasible.
- Data persists locally across app launches.
- Missing data does not crash or produce fabricated scores.
- Weekly review displays only metrics supported by recorded data.
- User can clear locally stored pilot data.
