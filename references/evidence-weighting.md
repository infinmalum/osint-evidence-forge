# Evidence Weighting, Funnel Reasoning, and Ablation

Core reference for ranking heterogeneous location evidence. Read when several
clues point at an area, or when a leading candidate has already formed.

## The funnel principle

Area reduction is a funnel of intersecting constraints, not a chain of proofs:

```text
wide region
→ structural constraints (transit + destinations + direction)
→ corridor established
→ relational and time-distance constraints
→ candidate settlements on the corridor
→ visual/environment compatibility checks last
```

Test every conclusion with the **evidence ablation test**: remove one clue,
recompute the ranking. If the conclusion collapses after removing a weak clue,
it is over-dependent on that clue. A conclusion reached by intersecting
structural constraints survives removal of the visual clues; a conclusion
reached primarily from visual similarity drifts freely once transit evidence
is removed.

## Three-axis evidence model

Never collapse evidence quality into one number. Score each clue on:

- **Reliability** — is the fact itself true? (source quality, verification,
  contemporaneity)
- **Discriminative power** — how many candidates does it eliminate? A fact can
  be 100% true and eliminate nobody (a common appliance style).
- **Independence** — does it originate from a different fact-source than the
  other clues? Two search engines citing the same page are one source.

Key identity: **reliability ≠ discriminative power.** For each clue ask:

```text
P(clue | candidate A) vs P(clue | candidate B) vs P(clue | anywhere)
```

If the last term is nearly as large as the first two, the clue cannot move the
ranking no matter how reliably it is established.

## Expected discriminative power (default prior, overridable)

1. **Structural mobility constraints** — routine transit lines, commuting
   times, habitual destinations. Usually the main area-reducer; but a line
   covering 70 km of villages has low actual gain — always recompute expected
   gain against the live candidate set.
2. **Relational geography** — family/friends one village over, walkable
   visits. Strong for final narrowing, weak alone.
3. **Visual environment matching** — ridges, terrain, vegetation. Default
   medium-weak (low resolution, unknown focal length and view direction,
   occlusion → false positives); a verifiable unique landmark arrangement can
   be decisive. Compatibility check, never primary locator.
4. **Equipment sighting → site identification** — compatibility with sites
   hosting that equipment (including support/logistics units), not proof of a
   specific site.
5. **Fixture/appliance dating** — very weak; styles span decades and regions
   and are replaced in renovations. Excludes extremes only.
6. **Behavioral durations** — errand/trip lengths carry hours of noise
   (waiting, detours, combined errands, delays). Exclude extreme hypotheses
   only.

## Lightweight information gain

No Bayesian math required — reason in candidate counts:

```text
before clue: ~100 plausible settlements
after clue: ~80  → low gain, barely moves ranking
after clue: ~12  → strong gain, load-bearing evidence
```

## Effect scale (compatibility is locked at zero)

For every clue × candidate pair, record one of:

```text
+2  strong support      (raises this candidate over peers)
+1  weak support        (mildly favors it)
 0  compatible/irrelevant (no conflict — and NO confirmation)
-1  tension             (requires an assumption to keep the candidate)
-2  contradiction       (candidate fails unless the clue is wrong)
```

The critical discipline: **"no conflict" is not "further confirmation".**
A clue compatible with every candidate on the list changes nothing.

## Counterfactual candidates against anchoring

Once a leader forms, anchoring converts ambiguous clues into apparent
confirmation. Mandatory counter-move:

1. list neighboring settlements along the same corridor;
2. re-run every clue against each;
3. ask: "would this clue look identical one stop earlier or later?";
4. keep alternatives visible until a clue discriminates.

If nothing discriminates, the honest output is the corridor segment, not a
single settlement.

## Administrative nesting

Two place names may not be independent alternatives — one can be a district of
the other's municipality. Check the administrative hierarchy before ranking
"A or B"; the choice may already resolve as "that municipality, probably that
district".

## Verbal time-distance bands

"About twenty minutes away" omits mode, traffic, and rounding. Convert to wide
mode-dependent isochrone bands; record transport mode as an explicit unknown.

## Ephemeral sources and the three-state status

Temporary traffic notices, construction schedules, and rerouted timetables
vanish from indexes within weeks. Rules:

- archive at discovery time (page save or screenshot + URL + title + date);
- a failed later re-search does not disprove a contemporaneous note;
- distinguish officially confirmed infrastructure work from the exact segment
  a transit portal labeled at the time;
- two AI search engines citing one page are not two independent sources.

Status vocabulary for such clues:

```text
confirmed                        (source recoverable and official)
contemporaneously observed,
presently unrecoverable          (recorded in notes; source decayed)
unverified                        (no contemporaneous record)
```
Do not promote or demote beyond what the record supports; note partial
independent corroboration (e.g. "general works confirmed, exact segment not
recovered") when it exists.

## Temporal scope does not propagate

Evidence supports a conclusion only for the period it covers:

```text
E supports residence during T0
⇏ E supports residence during T2
```

Association at one time proves nothing about ownership, continuous residence,
or current location.

## Post-hoc scoring (when the truth later becomes known)

Score separately:

- final area judgment;
- evidence selection;
- weight calibration;
- confirmation-bias control;
- **calibration under ablation** — delete every clue later shown weak or
  wrong; if the remaining structural constraints still yield the correct
  area, the method had predictive power. If not, the hit was partly luck.

A correct conclusion reached through over-weighted weak evidence predicts
failure on the next case. Record which evidence class actually carried it.
