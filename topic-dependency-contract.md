---
layout: homepage
---

<div style="font-size: x-large; float:top; margin-bottom: 1.0em;">
    <a href="index.html">Home</a>
    <a style="margin-left:2.0em;" href="braindumps.html">Brain Dumps</a>
    <a style="margin-left:2.0em;" href="publications.html">Publications</a>
    <a style="margin-left:2.0em; text-decoration: underline;" href="open-msc-topics.html">Open MSc Topics</a>
    <a style="margin-left:2.0em;" href="media.html">Media</a>
</div>

---

### Automated Dependency and Contract Inference for RESTful APIs

*Supervised by: [Carla Ferreira](http://www-ctp.di.fct.unl.pt/~cf/), [Ana Catarina Ribeiro](index.html) · June 2026*

The standard artefact for describing RESTful APIs is the OpenAPI Specification (OAS), which defines endpoints, HTTP verbs, request and response schemas, and status codes. However, OAS falls short of capturing the full behavioural semantics of an API: it does not express how operations relate to one another, which resources must exist before certain calls can succeed, or what invariants the system must maintain across interactions.

To address this, we developed [Glacier](https://github.com/acm-ribeiro/glacier-generator) — a first-order logic contract language that enriches OAS specifications with executable semantic contracts (preconditions, postconditions, and invariants), enabling automated behavioural verification during test execution. We also developed [IcePick](https://arxiv.org/abs/2604.08633), a framework for black-box testing of RESTful APIs that leverages TLA+ and its model checker TLC to systematically generate test suites covering modelled behaviour.

A key limitation of IcePick in its current form is that both Glacier contracts and TLA+ specifications require manual authoring, which demands formal methods expertise and restricts the framework's applicability.

**Problem**

Two interrelated problems currently limit the practical scalability of IcePick. First, inferring operation dependencies from a bare OAS file is non-trivial: dependencies arise from structural patterns — URI hierarchy, shared schema types, parameter names matching response fields — but also from semantic conventions not explicitly encoded in OAS. Existing tools derive dependencies heuristically, but these approaches are brittle and may miss domain-specific relationships not captured by syntactic patterns.

Second, generating meaningful Glacier contracts automatically from OAS files is an open problem: contracts grounded solely in CRUD semantics are intentionally partial and may omit application-specific consistency constraints. There is a need for richer, more expressive inference mechanisms capable of producing contracts that go beyond what can be derived from generic HTTP semantics alone.

**Objectives**

<div class="topic-list">
    <ol>
        <li><strong>Dependency Inference.</strong> Investigate techniques for extracting operation dependencies from OAS files, using structural signals such as URI hierarchy, path parameter reuse, shared schema references, and CRUD operation naming conventions.</li>
        <li><strong>Contract Inference,</strong> Extend or redesign the existing Glacier generator to support contract inference beyond basic CRUD semantics, including referential integrity constraints from schema cross-references and cardinality bounds from field definitions.</li>
        <li><strong>LLM-Assisted Inference.</strong> Explore whether LLMs can extract latent semantic knowledge from natural language descriptions in OAS files — inferring operation dependencies and generating Glacier-compatible contracts beyond what purely structural analysis can produce.</li>
        <li><strong>Evaluation.</strong> Assess the approach on real-world APIs from the [EvoMaster Benchmark](https://ieeexplore.ieee.org/abstract/document/10132197) and other publicly available REST services, measuring completeness and correctness of inferred contracts, the quality of generated call sequences, and fault-detection rate compared to manually authored specifications.</li>
    </ol>
</div>

**Expected Contributions**

- A dependency extraction pipeline for OAS files grounded in URI structure and schema analysis.
- An extended Glacier contract generator incorporating domain-specific inference heuristics beyond CRUD semantics.
- An LLM-assisted inference module with prompt strategies and mechanisms for validating LLM-generated contracts against OAS schemas and CRUD semantics.
- An empirical evaluation comparing automated and manual contract authoring in terms of coverage and fault detection.

**Team Integration**

The student will be fully integrated into the IcePick research team at NOVA LINCS, working alongside the framework's authors and contributing directly to an active line of research. This includes access to the existing IcePick codebase, Glacier toolchain, and benchmark infrastructure, as well as regular meetings with supervisors and the opportunity to co-author and publish results in relevant software engineering venues.

Interested? Reach out at acm.ribeiro (at) fct.unl.pt · [Download PDF](assets/files/topic-dependency-contract.pdf)
