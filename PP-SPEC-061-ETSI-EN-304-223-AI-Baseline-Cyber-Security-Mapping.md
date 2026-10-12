# PP-SPEC-061: Proof of Efficacy Mapping to ETSI EN 304 223 Baseline Cyber Security Requirements for AI Models and Systems

| Field | Value |
|---|---|
| Status | DRAFT v0.1 |
| Author | Craig Ellrod, Nebulonium, Inc. (dba HACKERverse®) |
| Date | October 8, 2026 |
| License | CC BY 4.0 |
| Maps to | ETSI EN 304 223 V2.1.1 (2025-12), Securing Artificial Intelligence (SAI); Baseline Cyber Security Requirements for AI Models and Systems |
| Series | Proof Protocol Framework Mapping Specifications |

---

## 1. Purpose

This specification defines how the AI security principles and provisions of ETSI EN 304 223 can be bound to Proof Protocol test cases, evidence, and efficacy results.

ETSI EN 304 223 is a European Standard (EN) produced by ETSI Technical Committee Securing Artificial Intelligence (TC SAI). Version V2.1.1 was published in December 2025 following the EN Approval Procedure. Its history records V1.1.1 (April 2025) as publication as ETSI TS 104 223, the Technical Specification that the EN builds on. TS 104 223 was in turn based on the UK Government's voluntary AI Cyber Security Code of Practice (published by the UK Government on 31 January 2025), which the UK Government stated it would submit to ETSI as the basis for a global standard. This mapping targets **ETSI EN 304 223 V2.1.1 (2025-12)**, the latest version confirmed at the time of writing.

The upstream source remains authoritative for its own requirements, identifiers, terminology, and guidance. This document defines a **Proof Protocol mapping** and does not supersede, reproduce, modify, or certify conformance to the upstream source.

## 2. Scope

ETSI EN 304 223 supplies external context that can identify what should be examined or tested across the AI system lifecycle. It is organized into 13 numbered principles grouped under five lifecycle phases (secure design, secure development, secure deployment, secure maintenance, and secure end of life), each principle carrying numbered provisions, with obligations allocated to defined stakeholder roles (Developers, System Operators, Data Custodians, End-users, and Affected Entities). Proof Protocol supplies an independent evidence model for determining what happened during a test and whether a selected control performed as claimed.

Many ETSI EN 304 223 provisions concern governance, documentation, awareness, communication, and process. Those provisions can be referenced by a proof record but are not themselves empirical efficacy claims (see section 4 and rule 9).

Independent witnessing, proof validity, evidence capture, packaging, anchoring, and efficacy semantics are defined elsewhere in the Proof Protocol specification family.

## 3. Core Question

Proof of efficacy asks:

> **Was there a control, and did it work?**

A framework requirement, criterion, principle, or obligation may identify a condition of interest. A product, architecture, policy, process, or safeguard may claim to satisfy or mitigate that condition. Proof Protocol binds the external context, test, control, observed behavior, downstream outcome, and evidence into a result that can be independently examined.

A Proof Protocol result does **not** by itself establish legal, audit, regulatory, or standards conformance unless the applicable authority separately determines that the evidence is sufficient.

## 4. Metric Definitions

Against a defined corpus or test condition, each applicable empirical case is recorded as **blocked**, **detected**, **missed**, or **INVALID** where those verdicts are meaningful.

Relevant measurements can include containment rate, detection rate, miss rate, false-positive rate, robustness under bypass or failure conditions, version-level results, and **INVALID** when required evidence is incomplete or broken.

Not every upstream requirement is empirical. Governance, documentation, organizational, legal, and procedural requirements MUST NOT be converted into efficacy scores merely because they can be referenced by a proof record.

## 5. Evidence Produced

Mapped tests can produce:

- **Proof records** binding external context, test case, control, system/version, verdict, timestamp, and evidence references;
- **ProofStamp™** trusted timestamps bound to evidence/verdict objects;
- **ProofBundle™** packages containing proof records, metrics, corpus manifests, and environment/context;
- **ProofRegister™** records for issued proof artifacts; and
- corpus and environment manifests identifying the tested conditions.

## 6. Mapping to ETSI EN 304 223

Exact upstream identifiers SHOULD be taken from the authoritative version being mapped and recorded in the ProofBundle™. Upstream titles and text SHOULD NOT be copied into the ProofBundle™ unless the upstream terms permit it. This specification does not redefine upstream requirements.

| ETSI EN 304 223 context | Proof Protocol treatment | Evidence |
|---|---|---|
| Lifecycle phase (clause 5.1 to 5.5) | Record the lifecycle phase in which the tested condition arises as test context. | Test metadata |
| Principle (Principle 1 to Principle 13) | Bind the principle number and the EN version to the test or examination record. | Requirement metadata |
| Provision (identifier format such as `5.1.1-1`, with sub-provisions) | Bind the specific provision identifier to one or more test cases where the provision states a testable security outcome. | Proof record; corpus manifest |
| Stakeholder role (Developer, System Operator, Data Custodian, End-user, Affected Entity) | Record which role asserts the control and which role's system is under test, separately from observed behavior. | Control descriptor |
| Asserted security measure | Record the claimed measure separately from whether it was present, configured, active, and effective. | Control descriptor |
| AI-specific threat condition addressed by a provision | Exercise the threat condition against the deployed model or system, including bypass and evasion variants where applicable. | Execution and robustness evidence |
| Testing and evaluation provisions | Distinguish the operator's own testing records from independently generated Proof Protocol test results. | Proof records; ProofBundle |
| Monitoring provisions | Establish whether monitoring detected the exercised condition, and whether detection preceded downstream impact. | Detection result; outcome evidence |
| Asset, infrastructure, and supply chain provisions | Bind model, data, prompt, dependency, and infrastructure versions that are material to the result. | Environment descriptor; corpus manifest |
| Update, patch, and mitigation provisions | Retest after material model, control, or system changes and compare version-level results. | Version-level proof records |
| Governance, documentation, and communication provisions | Reference as non-empirical context; MUST NOT be scored as efficacy. | Requirement metadata |
| Conformance evidence export | Package evidence and provenance for independent examination by the party assessing conformance. | ProofBundle |

## 7. Interoperability Rules

1. The authoritative upstream source, edition/version, and applicable identifier SHOULD be recorded.
2. Upstream identifiers and terminology MUST NOT be silently redefined.
3. Proof Protocol verdicts are Proof Protocol results; they are not upstream certifications, audit opinions, legal determinations, or endorsements.
4. A control's presence, configuration, activation, detection, and efficacy are distinct facts.
5. A policy decision, alert, log entry, or control trigger does not by itself establish efficacy when the claim concerns a downstream protected outcome.
6. Target, application, tool, SIEM, vendor, service, resource, or equivalent evidence SHOULD complete the evidence round trip when required to establish the result.
7. Missing required evidence MUST yield **INVALID**, not PASS.
8. Material changes to the tested system, policy, control, environment, mapping, or corpus SHOULD trigger retesting where they can affect the result.
9. Non-empirical requirements MUST remain distinguishable from empirically tested efficacy assertions.

## 8. Framework-Agnostic Architecture

> **Threat, control, audit, and regulatory frameworks are pluggable inputs to Proof Protocol. Proof Protocol is framework-agnostic.**

External frameworks can identify **what to test or examine**. Proof Protocol independently establishes **whether the control worked and what evidence proves that result**.

No external framework is required for Proof Protocol to operate. An implementation MAY use ETSI EN 304 223, another recognized framework, a proprietary threat model, several frameworks simultaneously, or no external framework when the test condition is otherwise sufficiently defined.

Adding, replacing, muting, or removing a framework mapping does not alter the Proof Protocol architecture, evidence model, Proof of Efficacy determination, ProofBundle™, ProofStamp™, ProofRegister™, or independent corroboration requirements.

A framework mapping therefore establishes **interoperability**, not architectural dependency.

## 9. Relationship to Proof Protocol

This mapping is part of the Proof Protocol specification family maintained by Nebulonium, Inc.

The relationship is intentionally asymmetric:

> **ETSI EN 304 223 supplies baseline AI security principles and provisions as external context. Proof Protocol supplies the evidence model for independently examining whether a selected AI security control performed as claimed.**

No affiliation, endorsement, certification, audit opinion, or sponsorship by ETSI is implied.

## 10. Source Framework, Attribution, and License

ETSI EN 304 223 is external work published by ETSI (European Telecommunications Standards Institute) and produced by ETSI Technical Committee Securing Artificial Intelligence (SAI). Its names, identifiers, trademarks, normative text, and expressive content remain subject to ETSI's ownership and terms.

The deliverable carries an ETSI copyright notification stating that no part may be reproduced or utilized in any form or by any means except as authorized by written permission of ETSI, and that the content of the PDF version shall not be modified without the written authorization of ETSI. ETSI states that the prevailing version of an ETSI deliverable is the one made publicly available in PDF format on the ETSI deliver repository.

The UK AI Cyber Security Code of Practice, from which ETSI TS 104 223 originated, is a separate UK Government publication made available under the Open Government Licence v3.0 except where otherwise stated. This mapping maps to the ETSI deliverable, not to the UK Code; implementers mapping to the UK Code SHOULD record it as a separate source.

This Proof Protocol mapping is independently authored and Licensed under the Greater Good Commercial License 1.0 (see LICENSE.md); text CC BY 4.0 under its Part S. Original inventor: Craig Thomas Ellrod (ORCID 0009-0004-1058-7666).

Contributors MUST NOT copy ETSI normative text, principle wording, provision wording, or definitions into this repository. Reference clause, principle, and provision identifiers and independently authored descriptions only.

### Required attribution

ETSI does not publish a specific attribution line for citing deliverable identifiers. Its deliverables carry the following copyright notification (quoted verbatim from ETSI EN 304 223 V2.1.1 (2025-12), page 2, https://www.etsi.org/deliver/etsi_en/304200_304299/304223/02.01.01_60/en_304223v020101p.pdf):

> No part may be reproduced or utilized in any form or by any means, electronic or mechanical, including photocopying and microfilm except as authorized by written permission of ETSI.
> The content of the PDF version shall not be modified without the written authorization of ETSI.
> The copyright and the foregoing restriction extend to reproduction in all media.
>
> © ETSI 2025.
> All rights reserved.

Recommended attribution and citation for this mapping:

> ETSI EN 304 223 V2.1.1 (2025-12), "Securing Artificial Intelligence (SAI); Baseline Cyber Security Requirements for AI Models and Systems", European Telecommunications Standards Institute. © ETSI 2025. All rights reserved. https://www.etsi.org/deliver/etsi_en/304200_304299/304223/02.01.01_60/en_304223v020101p.pdf

**What this specification reproduces:** the deliverable number, version, date, and title; clause, principle, and provision identifiers and numbering format; the names of the five lifecycle phases and the five stakeholder roles as structural terms; and short independently authored factual statements. **What it does not reproduce:** principle wording, provision text, definitions, tables, or any other expressive content of the deliverable. Because no part of the ETSI deliverable is reproduced or modified, the mapping does not require ETSI's written permission and does not relicense ETSI material.

## 11. Versioning

This mapping is versioned independently of ETSI EN 304 223. Material upstream changes SHOULD trigger a mapping review and, where necessary, a new version identifying the upstream revision mapped.

---

*Proof Protocol · proofprotocol.io · CC BY 4.0*
