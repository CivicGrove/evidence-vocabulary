# Capacity Signal™ Evidence Vocabulary

**Version 0.1 · Published 2026-09-14 · Licensed CC BY 4.0**

Canonical address: `https://capacitysignal.ca/spec/evidence-vocabulary/v0.1/`
Current version: `https://capacitysignal.ca/spec/evidence-vocabulary/`

---

## What this specifies

A supplier claim — that a firm welds pressure hulls, holds a certification, or
delivered a contract — is usually published with a single label attached: verified,
approved, qualified, trusted. One label cannot carry three separate facts, and
collapsing them is how a reader ends up unable to tell a government contract record
from a company's own marketing page.

This specification separates those facts into three independent axes. Every graded
claim carries a value on **all three**. No axis substitutes for another, and no value
on one axis implies a value on another.

The vocabulary is published free under CC BY 4.0 so that any register, directory or
report may use it. Attribution is the only condition.

---

## Axis A — Provenance

*Who supports this piece of evidence.* Provenance describes a single source, not a
claim and not a firm. A claim supported by several sources carries the provenance of
each. Provenance is never promoted: a `self_published` source is not upgraded by
repetition. It is corroborated only by an independent source at the same grade or
higher, which is recorded as an additional source at its own grade.

1. **`government_observed`** — a federal or provincial publication records it
   (proactive disclosure, CanadaBuys, an ISED ITB report).
2. **`registry`** — a public registry entry records it (a corporate registry, an
   accredited certification register).
3. **`certifier`** — a certification body's own public record records it.
4. **`counterparty`** — a buyer or prime attests it (a buyer-validated correction, a
   press release naming the supplier).
5. **`supplier_confirmed`** — the supplier confirmed or corrected its own record,
   attributed and dated.
6. **`self_published`** — the supplier's own website or profile.
7. **`inferred`** — derived by a stated rule from public data, with the rule recorded.

---

## Axis B — Event state

*What the claim asserts actually happened.* Event state describes the thing claimed,
independently of who says so. A contract award is `government_observed` plus
`awarded` — the word *delivered* is never applied to an award record.

1. **`claimed`** — asserted, with no event yet asserted beyond the assertion itself.
2. **`qualified`** — admitted to a standing offer, supply arrangement, or
   pre-qualification list.
3. **`awarded`** — a contract was awarded.
4. **`contracted`** — a contract is in force.
5. **`delivered`** — the work or goods were delivered.
6. **`certified`** — a certification was issued and is in force.

---

## Axis C — Review status

*Whether a named person read the source in context, and what they found.* Review status
is set only by a named reviewer and is dated. It is a routing instruction — what to check
next — not a grade of the firm.

1. **`reviewed`** — a named reviewer read the source in context and recorded that it
   directly supports the claim as worded.
2. **`supported`** — one or more open sources are consistent with the claim, but the
   support is indirect, secondary, self-declared, or not yet reviewed in context.
3. **`disputed`** — a named reviewer found credible sources or parties in conflict. The
   conflict is recorded and no single source is treated as settling it. `disputed` is a
   review status, not a separate axis: the conflicting sources keep their own provenance
   and event-state values.
4. **`unverified`** — no adequate open source has been found, or the only source has
   aged out of its stated freshness window.
5. **`no_claim`** — nothing has been asserted about this capability, so there is
   nothing to grade. A real firm is never shown as `unverified` for something nobody
   claimed.

---

## The rules

1. **Every graded claim carries all three axis values.** A record showing fewer than
   three is not conformant.
2. **No axis collapses into another.** A high provenance grade does not set a review
   status. A review status does not imply an event state.
3. **Provenance attaches to a source; review status attaches to a claim; event state
   attaches to the asserted event.** These are different objects and are stored
   separately.
4. **`no_claim` is not a negative finding.** Absence of a claim is recorded as absence,
   never as failure.
5. **Every value is dated.** A review status without a review date is not conformant.
6. **Values are not ranked across axes.** Ordering within an axis is a matter for the
   implementation; this specification does not define a combined score, and a
   conformant implementation does not publish one.

---

## Conformance

An implementation conforms to this specification when, for every graded claim it
publishes, it records one value from each of the three axes using the identifiers
above, and publishes the definitions or a link to this document.

This specification does not define display, colour, layout or ordering. Those are
implementation choices and are deliberately out of scope at v0.1.

---

## Scope and limits

This is version 0.1. It fixes the axes, the identifiers and the rules. It does not
define a capability taxonomy, a source-freshness schedule, worked examples, or a
conformance test suite. Those are candidates for v0.2.

This is the first public version, and it is open to revision. It is published, dated
and citable as it stands; a later version does not amend this document but is
published at its own permanent address, leaving this one unchanged.

Capacity Signal™ is the reference implementation. The vocabulary is not the register:
the selection, arrangement, reviewer annotations and dated reviewer judgments of any
particular register are the work of its publisher and are not placed under this
licence by this document.

---

## Licence

This specification is licensed under a
[Creative Commons Attribution 4.0 International Licence (**CC BY 4.0**)](https://creativecommons.org/licenses/by/4.0/).
You may share and adapt it for any purpose, including commercially, provided you give
attribution.

*Capacity Signal* is a trademark of Civic Grove Ltd. The licence covers this
specification; it does not grant rights in the mark.

## Cite as

> Civic Grove Ltd. (2026). *Capacity Signal™ Evidence Vocabulary, version 0.1.*
> https://capacitysignal.ca/spec/evidence-vocabulary/v0.1/
> DOI: 10.5281/zenodo.22822163

---

## Appendix — derived display annotations (non-normative)

Implementations commonly show short annotations on an evidence row. The following are
derivations from the axes above, not additional values, and are recorded here so that
an implementation does not mistake them for a fourth axis:

- *Self-reported* — provenance `self_published` or `supplier_confirmed`, review status
  `supported`.
- *Estimated* — provenance `inferred`.
- *Stale* — review status `unverified`, reached by a source ageing out of its freshness
  window rather than by absence of a source.

*Disputed* is **not** in this list — it is a review status in its own right
(Axis C, value 3), because a reviewer read the sources and found them in
conflict.
