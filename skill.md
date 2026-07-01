---
name: unearth-research
description: Use when someone says "unearth this", "unearth research on X", "run unearth on X", or "give me an unearth report on X". Also trigger when a user wants to investigate a topic where institutional narratives may be distorted by financial or political incentives, where suppressed or excluded voices are central to understanding the truth, where the formal record may not reflect lived experience, or where mainstream and alternative sources are both potentially captured by different incentive structures. UNEARTH sits alongside storm-research as a companion tool — use UNEARTH instead of STORM when the topic involves contested claims where the peer-review record itself may be compromised, where practitioners are divided in ways that matter, or where the dominant narrative has identifiable financial or institutional motivations. Examples: public health policy controversies, pharmaceutical safety signals, regulatory capture, media suppression claims, whistleblower accounts, contested environmental or scientific claims.
argument-hint: "[topic to investigate]"
---

# UNEARTH Research

## What this does

UNEARTH turns a contested topic into a verified, incentive-audited, suppression-aware HTML briefing. Unlike STORM — which applies five fixed epistemological lenses — UNEARTH first maps the distortion landscape of the topic itself, then selects lenses based on who has direct proximity to the phenomenon and whose testimony has been excluded from the formal record by verifiable mechanisms. The result is a report that surfaces what existing incentive structures suppress, without becoming a vehicle for bad-faith suppression claims.

**The founding principle:** Suppression is orthogonal to truth. A voice can be genuinely suppressed and wrong. A voice can be loud and right. UNEARTH's job is to surface excluded testimony and subject it to the same adversarial scrutiny as everything else — not to validate it by virtue of its suppression.

**Sits alongside storm-research.** STORM is optimized for socially contested, historically-patterned topics where the formal evidence record is reliable. UNEARTH is optimized for topics where the formal record itself is distorted by incentive structures — where peer review, institutional messaging, and media coverage are all potentially compromised in identifiable ways.

Run the full pipeline end to end. Do not shortcut any phase. The pre-processing layer is what makes this tool different — skipping it produces a report indistinguishable from a biased summary.

---

## Phase 0: Scope the topic

1. If `$ARGUMENTS` has the topic, use it. Otherwise ask what to investigate.
2. State your interpretation of the topic in one sentence — strip political framing, describe the phenomenon mechanically. Example: not "vaccine safety controversy" but "discrepancy between institutional safety signals and patient-reported adverse experience."
3. Identify the **reader's role** so the actionable section can target it. Infer from context; default to "a practitioner, researcher, or informed citizen trying to understand this topic honestly."
4. Derive a kebab-case `topic-slug` for the filename.
5. Tell the user: pipeline running — pre-processing first, then lenses, then verify. One line.

---

## Phase 1: Pre-processing layer

This is what separates UNEARTH from every other research framework. Three sequential steps. Do not skip or merge them. The output of each step feeds the next.

### Step 1 — Phenomenon mapping

Strip the topic of its social, political, and media framing. Describe what is actually happening as a mechanical or empirical question:

- What is the thing being claimed or observed?
- Who has **direct proximity** to it — who experienced it, witnessed it, or measured it firsthand?
- What is the gap between the official account and the firsthand account?
- What would we expect to see in the evidence record if the official account is correct? If it is incomplete or wrong?

Output: a one-paragraph mechanical description of the phenomenon and a named list of actors with direct proximity to it.

### Step 2 — Incentive landscape audit

Map every major actor in the information space around this topic. For each actor, answer two questions: **what do they financially and institutionally profit from**, and **in which direction does that pressure push their coverage or claims?**

Apply this to ALL sources without exemption:

- Government agencies and regulators
- Pharmaceutical or industry actors
- Legacy media and publishing
- Academic and peer-review institutions
- Alternative media, Substack, podcasts
- Advocacy organizations (both mainstream and outsider)
- Platform and social media trust-and-safety teams
- Political actors and parties

**Critical design rule:** Both mainstream and alternative sources must be audited. Legacy media may be incentivized toward institutional alignment by advertiser relationships and government trust designations. Alternative media may be incentivized toward contrarianism by subscription models that profit from differentiation and engagement algorithms that reward outrage. Neither exemption is granted. Both distortion vectors are named.

Output: a named table of actors, their financial/institutional incentives, and the direction of distortion pressure each creates.

### Step 3 — Mechanism test for suppression

For each voice or category of testimony that is **absent or underrepresented** in the formal record, apply the mechanism test:

> *Can a specific institutional, financial, or procedural barrier be identified that explains why this testimony did not enter the formal record?*

Examples of verifiable mechanisms:
- A clinician who observed an adverse pattern but did not document a causal connection for fear of professional consequences
- A regulatory reporting system that captures reports but is structurally designed not to establish causation, creating a gap between signal and official record
- A journal that rejected a case series without peer review under unusual speed or pressure
- A patient whose symptoms were attributed to anxiety rather than investigated, preventing formal diagnosis
- A platform that removed or suppressed content under policies driven by advertiser or government pressure

**The test is falsifiable.** If no specific mechanism can be identified — if the only evidence of suppression is the feeling of being ignored, or the existence of a large platform from which the "suppressed" voice broadcasts — the claim of suppression does not pass. That voice is treated as a regular source subject to standard scrutiny, not elevated to lens candidacy.

Output: for each candidate suppressed voice — MECHANISM IDENTIFIED (describe it specifically) or MECHANISM NOT VERIFIED (treat as standard source). Only voices that pass become lens candidates.

---

## Phase 2: Lens selection

Using the Phase 1 output, select **5–6 lenses**. These are not fixed — they are chosen for this specific topic based on the pre-processing diagnostic.

**Lens selection criteria:**

1. **Direct proximity to the phenomenon** — prioritize voices that experienced, witnessed, or measured it firsthand over voices that commented on it from outside
2. **Outside the identified distortion vectors** — do not select lenses whose primary incentive structure was identified in Step 2 as pushing them toward a predetermined conclusion
3. **Cover different time horizons and evidence relationships** — at least one lens should look at pattern and precedent; at least one should be grounded in present lived experience
4. **Genuine tension between lenses** — lenses that always agree aren't lenses, they're echoes. The selection must include perspectives that will contradict each other
5. **At least one structurally suppressed voice** — if any voice passed the mechanism test in Step 3, it must appear as a primary lens, not a footnote

**Document the selection reasoning.** For each lens chosen, write one sentence explaining why it was selected and one sentence explaining what distortion vector it is positioned outside of. This reasoning appears in the report.

**Example lens sets by topic type** (illustrative, not prescriptive):

*Pharmaceutical safety signal topic:*
- The injured patient (passed mechanism test — diagnosis denied)
- The frontline clinician (observes patterns before literature catches up)
- The regulatory scientist (understands surveillance system design and its limits)
- The incentive auditor (maps who profits from each possible finding)
- The investigative journalist (attempted to cover safety signals — what happened)
- The epidemiologist (signal-to-noise in population surveillance data)

*Regulatory capture topic:*
- The whistleblower (passed mechanism test — internal suppression documented)
- The affected community (direct proximity to the harm)
- The regulator (understands the agency's constraints and incentives from inside)
- The legal analyst (what remedies exist, why they are or aren't used)
- The historian (prior regulatory capture cases and how they resolved)

*Contested scientific claim:*
- The practitioner (what works in practice vs. what the literature says)
- The methodologist (how was the research designed, who funded it)
- The skeptic (steelman the counterargument rigorously)
- The replication researcher (what has and hasn't replicated)
- The affected patient or community (what they experience vs. what they're told)

---

## Phase 3: Research pipeline

Spawn all selected lenses in parallel. Each lens receives the same topic framing plus its own prompt:

**Per-lens prompt template:**

`You are THE [LENS NAME] for: {TOPIC} ({PHENOMENON DESCRIPTION from Phase 1}). {One sentence on your structural position and what you see that others miss.} Do real web research — prioritize sources that have direct proximity to the phenomenon, not secondary commentary. Return EXACTLY: 1) CORE POSITION in 2 sentences. 2) STRONGEST EVIDENCE — 3-5 bullets each with a concrete data point, named source, and URL. 3) THE ONE THING only someone in your position would say. Cite real sources with URLs. Under 400 words.`

When all lenses return, post a 2–3 line note in chat: where they converge, and the sharpest contradiction between them.

### Contradiction mapping

Working from all lens outputs, identify:

1. **Direct conflicts** — where two or more lenses claim opposite things. Name the specific clashing claims.
2. **Strongest vs. weakest evidence** — rank by source hierarchy: peer-reviewed causal > official surveillance data > firsthand testimony with mechanism > firsthand testimony without mechanism > secondary commentary > assertion
3. **The resolving question** — the single empirical question that would settle the biggest contradiction
4. **Universal agreement** — what every lens confirms. This is the load-bearing finding.
5. **The blind spot** — what no lens addressed. This becomes the missing 6th lens and the Frontier Question.

---

## Phase 4: Synthesize the HTML report

Use the same HTML template structure as storm-research. Fill every section:

- **Pre-processing summary** *(UNEARTH-specific — appears near the top, before findings)*
  - Phenomenon description (mechanical, stripped of framing)
  - Incentive landscape table (all actors, their incentives, distortion direction)
  - Mechanism test results (which voices passed, what mechanism was identified, which did not pass and why)
  - Lens selection reasoning (why each lens was chosen, what distortion it is positioned outside of)
  - This section is the audit trail — the reader can evaluate whether the pre-processing was done honestly

- **60-second summary** — lead with the settled fact, then the contested interpretation. Decision-maker grade.

- **5 key findings ranked by reliability** — highest reliability first. Each carries a confidence score and Supported-by / Challenged-by chips from the contradiction map.

- **Hidden connection** — the non-obvious link that only appears when all lenses are read together.

- **Missing 6th lens** — the blind spot from contradiction mapping, framed as the perspective that could change the conclusions.

- **Actionable insights** — 3–6 specific moves for the reader's role from Phase 0.

- **Claim safety guide** — assert / caveat / avoid. Populated after Phase 5 verification. The avoid section must explicitly name: claims that only one distortion-captured source supports; claims where mechanism of suppression was not verified; claims that conflate correlation with causation in surveillance data.

- **Frontier question** — the one question that would change everything.

- **References** — every citation with verification status tag.

Write to `storm-reports/{topic-slug}-briefing.html`.

---

## Phase 5: Adversarial verification

**Do not skip. A report delivered without Phase 5 is not an UNEARTH report.**

**5a. Self-review (inline).** Score each finding 1–10 for reliability. Identify the weakest link. Run a capture check: did any lens end up dominated by a source that failed the incentive audit? Did the suppressed voice lens get elevated beyond what its evidence warrants? Assign an honest overall grade.

**5b. Verify every citation.** Spawn verification agents per citation cluster. Each agent:

`Independently verify this citation against its PRIMARY source. Be skeptical of secondary summaries. CLAIM: {claim + figure + named source}. Find the actual primary source. Confirm or correct: exact title/authors/venue/year/URL, the real figure as published, method and limits, peer-review status. For contested claims, find the strongest credible counter-source. Return: VERDICT = CONFIRMED / PARTIALLY CONFIRMED (corrections listed) / UNVERIFIED / FALSE. Then corrected citation. Then 2–4 specifics with primary URL. Under 280 words.`

**5c. Apply corrections.** Fix wrong figures, titles, dates. Downgrade confidence scores where evidence was thinner than claimed. Demote any claim where the only supporting source failed the incentive audit. Fill verification banner. Populate claim safety guide from verdicts.

---

## Output

1. Final file: `storm-reports/{topic-slug}-briefing.html`
2. Present the file to the user.
3. In chat: verification tally (N/N checked, X fabricated, Y corrected, Z demoted), the one universal finding, the frontier question, and the claim safety summary. Keep it tight.

---

## Notes and guardrails

**The mechanism test is mandatory.** Never elevate a suppressed voice to a primary lens based on assertion of suppression alone. The mechanism must be specific and verifiable. This is the primary guard against the tool being used to launder conspiracy theory as balanced research.

**Audit all sources equally.** The incentive landscape audit applies to alternative and mainstream sources without exemption. A Substack with a subscription model has financial incentives just as a pharmaceutical company does. Name them both.

**Suppression is orthogonal to truth.** The tool's job is to surface excluded testimony and examine it rigorously — not to validate it. The claim safety guide must reflect this: assert what the evidence supports, regardless of which direction that points.

**The pre-processing summary is non-negotiable.** It must appear in the report and must show the actual reasoning, not a summary. This is what allows the reader to audit the tool's integrity. "Shows its work" is the primary safety guardrail.

**Real research only.** Every lens and every citation must trace to a real, fetched source. No invented studies, numbers, or URLs. If a figure cannot be verified, demote or cut it.

**The panel is author-built.** Always disclose this. Convergence across lenses is a strong hypothesis, not independent proof of consensus.

**Relationship to storm-research.** UNEARTH and STORM are companion tools. STORM when the formal evidence record is reliable and the question is contested interpretation. UNEARTH when the formal record itself is a subject of investigation. When in doubt about which to use, run the Phase 1 incentive landscape audit first — if it reveals significant distortion vectors across multiple source categories, use UNEARTH.
