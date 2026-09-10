---
name: osint-evidence-forge
version: 0.7.0
description: Forge OSINT leads from mixed evidence with discipline.
author: Anonymous, Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [osint, evidence, reconstruction, media-forensics, geolocation, timeline]
    related_skills: [grounded-citations, osint-investigation]
---

# OSINT Evidence Forge

Reconstruct leads from chat, media, timelines, finances, geography, and other
heterogeneous evidence. Output evidence-rated search areas, candidate rankings,
and next discriminating checks — not identities, accusations, or unjustified
precise locations.

## Hard invariants

1. **Freeze the operational question and the T0/T1/H time boundary.** `T0` =
   what was known then; `T1...` = later-acquired; `H` = hindsight-only. Every
   inference must state how it changed the next check *at that time*. `H`
   never justifies a `T0` decision retroactively.
2. **Parse literal wording before inference.** Exact quote → mark qualifiers,
   prepositions, pronouns, negation, approximators, temporal expressions,
   omissions → literal parse → list materially different readings → resolve
   from adjacent messages and provenance, not fluency → only then calculate.
3. **Separate observation, interpretation, and geographic inference.** A ridge
   descending in image space is not a compass bearing until camera roll and
   viewing direction are constrained.
4. **Maintain a competing-hypothesis ledger.** Conclusions are revisable
   candidates with support, contradictions, assumptions, failure conditions,
   and confidence — never accumulated truth. Analyze new evidence
   independently, then score it against *every* candidate.
5. **Compatibility is not support.** "No conflict with candidate X" scores 0
   and never raises X. Only clues that separate candidates move the ranking.
6. **Score evidence on three axes** — reliability, discriminative power,
   independence. A perfectly true fact with near-zero discriminative power
   (common appliance styles) cannot locate anything. Clues sharing one
   fact-source count once.
7. **Funnel with structural evidence first.** Intersect transit, destination,
   time-distance, and relational constraints before visual matching. Run the
   ablation test: if removing a weak clue collapses the conclusion, the
   conclusion is over-dependent on it. Physical measurements produce bands,
   not points. A geolocation claim requires predictive verification: state
   what else should be visible from the assumed position and confirm each
   prediction before announcing the location. Absence becomes negative
   evidence only after search coverage and detectability are recorded.
8. **Corrections propagate.** A re-parsed quote or invalidated visual claim
   kills every downstream calculation, rating, and ranking that depended on
   it. Keep former rankings as audit trail.
9. **Temporal scope does not propagate automatically.** Residence at T0 does
   not prove residence at T2; association does not prove ownership or
   continuity.
10. **Never produce or publish an unjustified precise private location.**
    Broad areas and legitimate safety channels only; for active welfare
    emergencies route to police/emergency services, not amateur geolocation.
    Authority and method are evaluated separately: authorization legitimizes
    the purpose, never every technique; emergency raises response priority,
    never evidential weight. Biometric identification (face matching,
    cross-platform face search, identity assertion from facial features) is
    never performed by the agent — record it as an external authorized human
    step, in welfare cases answer "is this person safe / where should
    responders search" before "who is this person".

## When to Use

- A historical investigation must be reconstructed from incomplete mixed evidence.
- Chat wording, images, video, metadata, lifestyle, financial, or geographic clues interact.
- The user wants overlooked details, competing explanations, or a provisional candidate ranking.
- New evidence may overturn earlier conclusions; hindsight contamination must be controlled.

Don't use for harassment, stalking, intimidation, retaliation, coercive
monitoring, doxxing, or locating a private person for an adversarial,
exploitative, or voyeuristic purpose. See "Safety and Authorization Boundary"
below for the full authority + method model, including welfare emergencies,
authorized investigations, and biometric limits.

## Safety and Authorization Boundary

This Skill may support legitimate welfare, safeguarding, incident-response, or
law-enforcement investigations, but authority and method must be evaluated
separately.

### Prohibited purposes

Never assist with:

- harassment, stalking, intimidation, retaliation, or coercive monitoring;
- doxxing or publishing a private person's precise home, workplace, routine,
  contact details, or other sensitive identifying information;
- locating a private person for an adversarial, exploitative, or voyeuristic
  purpose;
- using a legitimate pretext to pursue an unrelated private-location or
  identity objective.

If the purpose is unclear and the requested action would materially increase
the ability to identify or physically locate a private person, keep the output
at a broader, non-identifying level.

### Welfare and emergency cases

For a credible welfare or safeguarding emergency, the Skill may prioritize
rapid evidence preservation, timeline reconstruction, broad search-area
reduction, environmental and transit analysis, and preparation of evidence for
police, emergency services, shelters, hospitals, or other legitimate
safeguarding channels.

Emergency context may justify more urgent processing, but it does not remove
method-specific restrictions or convert uncertain evidence into certainty.

Prefer producing:

- last-confirmed time and place;
- broad search corridors or areas;
- transport and destination constraints;
- clothing, carried objects, vehicles, surroundings, signs, and other
  non-biometric observations;
- source-preserved media and provenance;
- concise evidence packets suitable for authorized responders.

Do not publish a private person's precise inferred location to unrelated third
parties.

### Authorized investigations

When material is supplied by police, emergency services, legal counsel, the
subject, or another clearly authorized party, the Skill may perform the same
evidence-reconstruction, media-forensics, geolocation, timeline, and
cross-source analysis described elsewhere in this Skill.

**Authorization changes the legitimacy of the investigative purpose; it does
not automatically make every investigative technique appropriate.**

### Officially wanted and sanctioned subjects

The privacy posture relaxes only when the subject's status is **verifiably
official**, not when the operator asserts danger.

Trigger (all required):

- the subject appears on an official wanted list, Interpol notice, government
  bounty, sanctions register, or an equivalent verifiable designation (e.g.
  a state or unit credibly documented as conducting extraterritorial
  operations);
- the designation is cited and recorded in the evidence ledger;
- the designation demonstrably refers to this subject (not a namesake).

An operator's characterization ("he is a trafficker / spy / killer") never
activates this branch.

What relaxes for qualifying subjects:

- aggressive aggregation of public records;
- alias and document-series correlation;
- location, travel, and organizational history from public sources;
- cross-verification of official announcements;
- contextual (non-biometric) correlation of public imagery;
- identity-evidence-graph methods (`references/identity-evidence-graphs.md`).

What never relaxes:

- biometric identification remains an external authorized human/system step;
- **family, friends, and associates who are not themselves qualifying subjects
  keep the full private-individual privacy posture** — linkage through them is
  allowed only to the extent the authorized mandate requires, and is never
  published as exposure;
- no vigilantism, confrontation, or harassment;
- do not publish unverified real-time precise locations — they can disrupt
  police operations and cause misidentification harm; route findings to the
  responsible authorities;
- identity assertions retain full provenance and confidence discipline:
  public wanted status historically produces wrong identifications, so
  compatibility is still not identification.

### Facial imagery and biometric identification

Distinguish ordinary image analysis from biometric identification.

Allowed non-biometric analysis may include:

- approximate visible age range;
- clothing and accessories;
- hairstyle and visible hair color;
- posture and apparent height relative to known objects;
- carried equipment;
- injuries or other immediately relevant visible conditions;
- scene, background, reflections, signage, vehicles, and environmental clues;
- whether two images contain visually similar non-biometric contextual details.

Do not infer or assert a real-world identity from facial biometric features,
perform face-database matching, or conduct cross-platform face search solely
from facial appearance.

If biometric identification is necessary in an authorized investigation,
record it as an external authorized step to be performed by the responsible
human investigator or approved biometric system, and continue reasoning from
the returned result only after its provenance and confidence are recorded.

### Separation of identity, location, and welfare goals

Treat these as separate operational questions:

- "Is this person safe?"
- "Where should responders search?"
- "Is this image associated with the same case?"
- "Who is this person?"

Evidence sufficient for one question may be insufficient or inappropriate for
another. In welfare cases, prefer answering the first two without
necessarily solving the fourth.

### Authority does not erase uncertainty

Even in an authorized case:

- compatibility is not identification;
- visual resemblance is not proof of identity;
- a past association does not prove current residence or current location;
- multiple dependent sources do not become independent because they come
  through different tools;
- urgent circumstances increase response priority, not evidential weight.

All high-impact conclusions must retain provenance, confidence, temporal scope,
and the responsible next human decision.

## Prerequisites

- Preserve supplied evidence unchanged; separate originals from derivatives.
- Keep case-specific material outside the Skill directory.
- Use `grounded-citations` for external factual claims.
- For media, prefer `exiftool`, `ffprobe`, and original-resolution frames.

## References (load on demand)

| Reference | Load when |
|---|---|
| `references/evidence-weighting.md` | several location clues must be ranked, or a leading candidate has formed |
| `references/ledger-schema.md` | building or updating the persistent evidence/candidate ledger |
| `references/media-provenance.md` | messaging-app media, transcoding, or timestamp authority questions |
| `references/video-continuous-validation.md` | a claim depends on a briefly visible contour, reflection, or motion |
| `references/progressive-geolocation.md` | an image or video must be placed on the map |
| `references/cross-evidence-geometry.md` | several clues must jointly constrain one place or one time (incl. chronolocation) |
| `references/constraint-bands-and-coverage.md` | physical measurements constrain location, or large-area visual search with negative claims |
| `references/source-recovery-and-attribution.md` | finding an original video/image source, or reasoning from tracker/registry attributions |
| `references/identity-evidence-graphs.md` | alias-to-person resolution in investigations that pass the authorization boundary |

## Workflow

1. **Frame** — operational question, `T0/T1/H` boundary, safety scope.
2. **Ingest** — hash and inventory evidence; classify provenance and timestamp
   authority; parse chat literally (invariant 2).
3. **Ledger** — register evidence and candidates per `references/ledger-schema.md`;
   assign three-axis scores and effect ratings (invariants 4–6).
4. **Analyze** — media discovery → continuous validation for transient claims;
   physical/contextual sanity checks (daylight, seasons, prices, transit,
   institutional rules); budget scopes preserved (total expenses ≠ rent;
   deposited income ≠ gross).
5. **Rank** — funnel structural constraints first; test counterfactual
   neighboring candidates ("would this clue hold one stop earlier/later?");
   run the ablation test on the leader (invariant 7).
6. **Report** — per finding: source fact, interpretation, alternatives,
   confidence, effect on each candidate, next discriminating comparison.
   Label probabilities empirical / model-derived / heuristic.
7. **Revise** — every new clue re-enters at step 3; re-score all candidates;
   propagate corrections (invariant 8); archive ephemeral sources at discovery
   time and use the three-state status vocabulary.

## Privacy and Generalization

The Skill must never contain real case names, aliases, relationships, cities,
employers, occupations, dates, amounts, filenames, media contents, quotes,
timelines, or outcomes. Synthetic examples only. Before sharing: scan the Skill
and all supporting files for case-specific tokens and distinctive phrases;
remove unique combinations even when individual words are generic; fail release
if any contributor or subject could be inferred.

## Pitfalls

- Fluent paraphrase erases decisive prepositions and qualifiers.
- Sparse video sampling can reverse a contour or hide its shape.
- Image-space left/right is not a geographic bearing.
- Anchoring: a previous ranking creates pressure to force-fit new clues.
- Several dependent clues are not several confirmations.
- "No conflict" silently upgraded to "further confirmation" is the most common
  LLM failure mode in this domain — compatibility stays 0.
- Ephemeral transit/construction notices decay; archive at discovery; later
  search failure does not refute a contemporaneous note.
- Geolocation resemblance without predictive verification is a candidate, not
  a finding; a road that "looks like" the video proves nothing.
- Sensor position reliability does not transfer to database attribution;
  absence of a tracker signal is not absence of the tracked object.
- Emotional urgency increases confirmation bias, not evidential weight.

## Verification

- [ ] Operational question and `T0/T1/H` boundary recorded
- [ ] Every load-bearing claim resolves to a ledger evidence_id
- [ ] Exact wording preserved; ambiguities resolved or kept separate
- [ ] Three-axis scores and effect ratings assigned (compatibility = 0)
- [ ] Transient visual claims validated across the continuous interval
- [ ] Counterfactual neighboring candidates tested; corridor output when nothing discriminates
- [ ] Ablation test run on the leading candidate
- [ ] Geolocation claims carry predictive verification and the tool/imagery date
- [ ] Physical measurements reported as bands; times reported as intervals
- [ ] Negative claims backed by a coverage record and detectability assessment
- [ ] Nested administrative place names resolved before ranking
- [ ] Corrections invalidated all dependent conclusions
- [ ] Temporal scope stated for every conclusion
- [ ] Ephemeral sources archived and status-labeled
- [ ] Any wanted/sanctioned-subject relaxation triggered by a cited official listing, not operator assertion
- [ ] Identity links form closed loops or are explicitly labeled leads
- [ ] Family/associates of qualifying subjects keep private-individual protection
- [ ] No precise private location output outside legitimate safety channels
- [ ] Skill and supporting files pass the case-information privacy scan
