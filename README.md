# OSINT Evidence Forge

**An epistemic-hygiene skill for AI agents doing open-source investigations.**

OSINT Evidence Forge is a [Hermes Agent](https://hermes-agent.nousresearch.com) skill — also usable as a general agent skill — that teaches an AI agent to reconstruct investigative leads from heterogeneous evidence: chat logs, images, video, metadata, timelines, financial details, transit patterns, and geography.

Its core value is **not** tricks for guessing locations. It is a discipline pipeline that keeps an agent honest when evidence is noisy, partial, contradictory, and contaminated by hindsight:

```text
literal evidence → provenance → competing hypotheses
→ discriminative weighting → counterfactual testing
→ correction propagation → bounded conclusions
```

## What it enforces

The skill is built around ten **hard invariants**, including:

1. **T0/T1/H time boundaries** — separate what was known then, what was learned later, and hindsight-only facts; hindsight never justifies earlier decisions retroactively.
2. **Literal wording before inference** — qualifiers, prepositions, pronouns, and approximators are parsed before paraphrasing; a changed parse invalidates every dependent conclusion.
3. **A competing-hypothesis ledger** — conclusions are revisable candidates scored on support, contradictions, assumptions, and failure conditions; new evidence is tested against *every* candidate, never force-fit to the current favorite.
4. **Compatibility ≠ support** — "no conflict" scores zero and never raises a candidate.
5. **Three-axis evidence scoring** — reliability × discriminative power × independence; a true fact that cannot separate candidates locates nothing.
6. **Funnel, not chain** — structural constraints (transit, destinations, time-distance, relationships) intersect before visual matching; conclusions must survive an ablation test.
7. **Bands, not points** — physical measurements and verbal time estimates propagate as constraint bands, never false precision.
8. **Predictive verification for geolocation** — before announcing a location, predict what else should be visible from the assumed position and confirm each prediction.
9. **Negative evidence requires coverage** — "I looked and found nothing" counts only after search coverage and detectability are recorded.
10. **Safety boundary** — no harassment, doxxing, or unjustified precise private locations; biometric identification stays an external authorized human step; welfare emergencies route to real responders.

## References (loaded on demand)

| File | Purpose |
|---|---|
| `references/evidence-weighting.md` | Evidence classes, three-axis scoring, funnel reasoning, ablation, counterfactual candidates |
| `references/ledger-schema.md` | YAML schemas for evidence/candidate ledgers and ablation records |
| `references/media-provenance.md` | Messaging-app transcoding, timestamp authority |
| `references/video-continuous-validation.md` | Continuous-interval validation for transient visual claims |
| `references/progressive-geolocation.md` | Observation → discriminator → prediction → confirmation pipeline |
| `references/cross-evidence-geometry.md` | Joint geometric/temporal constraints, chronolocation as interval intersection |
| `references/constraint-bands-and-coverage.md` | Measurement bands, shadow geometry, search-coverage ledgers |
| `references/source-recovery-and-attribution.md` | Video source recovery, tracker/registry attribution uncertainty |
| `references/identity-evidence-graphs.md` | Alias-to-person resolution (authorized investigations only) |

## Installation

### skills.sh (works with Claude Code and 40+ agents)

```bash
npx skills add infinmalum/osint-evidence-forge
```

### Hermes Agent (recommended)

This repository currently uses the standalone skill layout, with `SKILL.md` at the repository root. Install it directly from its URL:

```bash
hermes skills install https://raw.githubusercontent.com/infinmalum/osint-evidence-forge/main/SKILL.md
```

Hermes tap installation expects skills under `skills/<skill-name>/`. If this repository is later restructured into that tap layout, the tap method may be used.

### Other agents (Cursor and SKILL.md-compatible runtimes)

The skill follows the standard `SKILL.md` + `references/` agent-skill layout. Point your runtime's skill directory at this repository, or copy `SKILL.md` and `references/` into its skill folder. No code execution is required — the skill is procedural documentation the agent loads as context.

## Methodology sources

The procedures were distilled from real investigations and their post-hoc reviews, including public geolocation and verification case studies in the spirit of [Bellingcat](https://www.bellingcat.com)'s published methods (progressive geolocation, chronolocation, shadow constraints, search grids, source recovery), plus lessons from a civilian welfare-location reconstruction. No real case names, subjects, locations, or data are included — every example is synthetic.

## Safety

This skill is designed for journalists, researchers, safeguarding professionals, and lawful investigators. It explicitly refuses harassment, stalking, doxxing, and unwarranted exposure of private individuals. See the *Safety and Authorization Boundary* section in `SKILL.md` for the full authority + method model, including welfare emergencies, authorized investigations, wanted/sanctioned subjects, and biometric limits.

## License

[MIT](LICENSE)

## Readme translations

- [简体中文](README.zh-CN.md)
- [繁體中文](README.zh-TW.md)
- [Русский](README.ru.md)
- [Українська](README.uk.md)
