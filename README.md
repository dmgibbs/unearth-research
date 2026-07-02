# unearth-research
Initially based on the M.I.Ts STORM skill for Claude, STORM and UNEARTH both tell you what the evidence says. UNEARTH first checks whether the evidence collection process was rigged — and adjusts accordingly.

# Claude Research Skills Library

A collection of structured research skills for Claude Code. Each skill encodes a distinct research methodology — not just a prompt, but a complete epistemological framework for how to approach a class of problem.

These skills sit in your local `~/.claude/skills/` directory and become available to Claude automatically.

---

## Installation

```bash
# Clone the repo
git clone https://github.com/YOUR_USERNAME/claude-skills.git

# Copy whichever skills you want into your Claude skills directory
cp -r claude-skills/skills/unearth-research ~/.claude/skills/
cp -r claude-skills/skills/storm-research ~/.claude/skills/
```

Then just talk to Claude. The skills trigger on natural language — no special syntax required.

---

## The Skills

### `storm-research` — Multi-perspective research briefing

**Trigger:** "storm research this" / "storm report on X" / "give me a STORM briefing on X"

STORM applies five fixed epistemological lenses to a topic — Practitioner, Academic, Skeptic, Economist, Historian — maps where they contradict each other, and synthesizes everything into a verified HTML report.

**Best for:** Topics with a contested dominant narrative, historical precedent worth drawing on, and a formal evidence record that is broadly reliable. Social policy debates, technology adoption questions, business strategy, cultural history.

**Not ideal for:** Topics where the formal evidence record itself is compromised by incentive structures — where peer review, institutional messaging, and media coverage are all potentially distorted in identifiable ways.

---

### `unearth-research` — Incentive-audited, suppression-aware research briefing

**Trigger:** "unearth this" / "unearth research on X" / "run unearth on X" / "give me an unearth report on X"

UNEARTH runs a three-step pre-processing diagnostic before selecting any lenses — mapping the incentive landscape of every information source, testing suppression claims against a falsifiability standard, and selecting lenses based on structural position rather than epistemological type. The result surfaces testimony that existing incentive structures exclude, without becoming a vehicle for bad-faith suppression claims.

**Best for:** Topics where the formal record may not reflect lived experience — pharmaceutical safety signals, regulatory capture, whistleblower accounts, contested public health policy, media suppression claims, cases where practitioners and patients report experiences that don't appear in the official record.

---

## The Design Philosophy

These two skills emerged from the same underlying question: **what makes a lens set work?**

### What STORM taught us

STORM's five lenses are not five opinions. They are five distinct *epistemological contracts* — different agreements about what counts as valid evidence, what time horizon matters, and what questions are worth asking. The Practitioner says: *what I've seen with my hands is real.* The Academic says: *only what survives replication counts.* The Skeptic says: *the burden of proof hasn't been met.* The Economist says: *follow incentives, not claims.* The Historian says: *this has happened before.*

The power of the framework comes not from any individual lens but from **mapping where they contradict each other**. Claims that survive all five ways of knowing are likely load-bearing truth. Claims that only one lens can see are likely that lens's blind spot.

### What STORM can't do

STORM assumes the formal evidence record is a reliable input. On topics where peer review is subject to publication pressure, where regulatory agencies have institutional credibility tied to a particular outcome, where media coverage is shaped by advertiser relationships or platform trust designations — the Academic and Historian lenses are working with potentially compromised raw material. The framework produces false confidence.

More importantly, STORM's single Practitioner lens flattens important internal divisions. On some topics, the clinician administering a treatment and the patient experiencing an adverse outcome are both practitioners — but their testimony doesn't reconcile, and that tension is the most important thing to surface.

### What UNEARTH adds

UNEARTH introduces a **pre-processing layer** that runs before any lenses are selected:

**1. Phenomenon mapping** — Strip the topic of political and media framing. Describe what is actually happening mechanically. Identify who has direct proximity to the phenomenon.

**2. Incentive landscape audit** — Map every actor in the information space: what do they financially and institutionally profit from, and which direction does that pressure push their coverage? Applied without exemption to mainstream *and* alternative sources. Legacy media may be captured by advertiser relationships and government trust designations. Alternative media may be captured by subscription models that profit from contrarianism and engagement algorithms that reward outrage. Neither exemption is granted.

**3. Mechanism test for suppression** — For each voice absent from the formal record: can a *specific institutional, financial, or procedural barrier* be identified that explains their absence? This is the critical design feature. Suppression claims are cheap — anyone can claim their voice is being silenced. The mechanism test makes the claim falsifiable. A clinician who didn't document an adverse connection for fear of professional consequences is a verifiable mechanism. An influencer with two million subscribers who feels censored is not. Voices that pass the mechanism test are elevated to primary lenses. Voices that don't are treated as standard sources subject to normal scrutiny.

### The founding principle

**Suppression is orthogonal to truth.** A voice can be genuinely suppressed and wrong. A voice can be loud and right. UNEARTH's job is to surface excluded testimony and subject it to the same adversarial scrutiny as everything else — not to validate it by virtue of its suppression.

The pre-processing summary appears visibly in every UNEARTH report — the incentive map, the mechanism test results, the lens selection reasoning. This is the "shows its work" guardrail. The reader can evaluate whether the pre-processing was done honestly, which means the tool can be held accountable.

### The portable design principle

Both skills are instantiations of a more general principle: **a lens set should cover different structural positions relative to the phenomenon, different time horizons, different relationships to incentive, and must have genuine tension between lenses.**

This principle is domain-agnostic. For a technical architecture decision, the right lenses might be: Engineer, Security Auditor, End User, Maintainer, Economist. For a medical decision: Clinician, Researcher, Patient, Regulator, Skeptic. The specific lenses change. The design criteria don't.

---

## Output Format

Both skills produce a self-contained HTML report with:

- Verification banner (citations checked, fabrications found, corrections made)
- 60-second summary (settled fact first, contested interpretation second)
- Key findings ranked by reliability with confidence scores
- Contradiction map
- Hidden connection (the non-obvious link across all lenses)
- Missing 6th lens (the blind spot)
- Actionable insights targeted to the reader's role
- Claim safety guide (assert / caveat / avoid)
- Frontier question
- Full references with verification status

UNEARTH reports additionally include a **Pre-processing Summary** at the top — the incentive landscape table, mechanism test results, and lens selection reasoning — making the tool's diagnostic work visible and auditable.

---

## No Gatekeeping

These skills were developed through iterative conversation exploring what makes a research framework epistemologically honest rather than just comprehensive. The thinking behind them is documented in the README so anyone can understand, critique, extend, or redesign the approach.

If you build a variant — a custom lens set for a specific domain, a modified pre-processing layer, a different output format — contributions are welcome.

---

## Relationship to the Claude Skills Ecosystem

Skills live in `~/.claude/skills/` and are available to Claude Code automatically. The skill description in the YAML frontmatter controls when Claude decides to use the skill — if the description is too narrow, the skill won't trigger when it should. Both skills here are tuned to trigger on natural language phrases and also on topic characteristics, not just explicit invocation.

For more on the Claude skills system: [docs.claude.ai](https://docs.claude.ai)
