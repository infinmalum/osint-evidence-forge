# Ledger Schema: Evidence and Candidate Objects

Use a persistent ledger file so hypotheses survive context compression without
distortion. YAML is the file format; in-chat, a compact markdown table is the
acceptable fallback.

## Evidence object

```yaml
evidence_id: E12
source_fact: "<verbatim fact or exact quote>"
temporal_scope: T0            # when this was known / what period it covers
provenance: platform-transcoded  # original | forwarded | transcoded | ...
reliability: medium            # high | medium | low
status: confirmed              # confirmed | contemporaneously-observed-unrecoverable | unverified
discriminative_power: high     # high | medium | low | near-zero
independence_group: transit-corridor   # clues sharing one fact-source share a group
interpretations:
  - I12a: "<literal reading>"
  - I12b: "<competing reading>"
resolved_interpretation: I12a  # or null while unresolved
candidate_effects:            # scale: +2 +1 0 -1 -2 (compatibility locked at 0)
  C1: +2
  C2: +1
  C3: 0
  C4: -2
unknowns:
  - transport_mode
next_discriminator: "<observation that would split candidates>"
```

## Candidate object

```yaml
candidate_id: C3
scope: settlement              # region | corridor | settlement | site
status: active                 # active | weakened | falsified | superseded
support: [E2, E7]              # evidence ids with effect >= +1
contradictions: [E11]          # evidence ids with effect <= -1
compatibilities: [E4, E9]      # effect == 0; never counted as support
assumptions: [A4]              # what must hold for the candidate to survive
failure_conditions:
  - "travel mode confirmed as walking"
confidence: heuristic-medium   # empirical | model-derived | heuristic
```

## Ablation record

After each major re-ranking, and always in post-hoc review:

```yaml
ablation:
  removed: [E1, E5, E9]        # weak or falsified clues
  ranking_after: [C2, C3, C1]
  conclusion_survives: true     # false → over-dependent on removed clues
```

## Rules

1. Every load-bearing number, quote, or visual claim in the report must
   resolve to an evidence_id.
2. Effects come from the resolved interpretation only; an unresolved
   interpretation produces no effects.
3. Compatibility entries never migrate into support.
4. Evidence in the same independence_group counts once for ranking purposes.
5. Falsified or re-parsed evidence invalidates its effects and every
   dependent ranking; keep an audit trail of former rankings.
