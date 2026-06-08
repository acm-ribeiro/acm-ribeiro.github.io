---
layout: homepage
---

<div style="font-size: x-large; margin-bottom: 1.0em; display: flex; flex-wrap: wrap; gap: 0.8rem 0; justify-content: space-evenly;">
    <a href="index.html">Home</a>
    <a href="publications.html">Publications</a>
    <a href="open-msc-topics.html" style="text-decoration: underline;">MSc Topics</a>
    <a href="braindumps.html">Brain Dumps</a>
    <a href="media.html">Media</a>
</div>

---

### Automated Inference of Likely Invariants and TLA+ Specifications for RESTful APIs

*Supervised by: [Carla Ferreira](http://www-ctp.di.fct.unl.pt/~cf/), [Ana Catarina Ribeiro](index.html) · June 2026*

The standard artefact for describing RESTful APIs is the OpenAPI Specification (OAS), which defines endpoints, HTTP verbs, request and response schemas, and status codes. However, OAS falls short of capturing the full behavioural semantics of an API: it does not express how operations relate to one another, which resources must exist before certain calls can succeed, or what invariants the system must maintain across interactions.

To address this, we developed [Glacier](https://github.com/acm-ribeiro/glacier-generator) — a first-order logic contract language that enriches OAS specifications with executable semantic contracts (preconditions, postconditions, and invariants). We also developed [IcePick](https://arxiv.org/abs/2604.08633), a framework for black-box testing of RESTful APIs that leverages TLA+ and its model checker TLC to systematically generate test suites covering modelled behaviour. IcePick has demonstrated that model-checking-guided exploration can reveal subtle multi-operation faults — such as referential integrity violations — that tools relying solely on HTTP status codes would miss.

However, implementing the full pipeline (OAS → Extended OAS → TLA+ Specification → Model → Testing) currently requires substantial manual effort: specifying Glacier invariants and writing TLA+ specifications both demand formal methods expertise, forming a significant barrier to widespread adoption.

**Problem**

Two interrelated problems currently limit the practical scalability of IcePick. First, inferring meaningful API invariants from observed executions is non-trivial. Dynamic invariant detection tools such as [Daikon](https://www.sciencedirect.com/science/article/pii/S016764230700161X) infer likely invariants by observing program executions, but applying these ideas to RESTful APIs is challenging: the system state is distributed across HTTP resources, observations are obtained through API responses rather than internal program variables, and the relevant invariants often describe relational properties over multiple resources.

Second, automatically generating TLA+ specifications from OAS and Glacier contracts is equally challenging. Although TLA+ is well suited for modelling state-transition systems, producing a useful specification requires identifying which API operations induce abstract state transitions, how resources should be represented in TLA+, and how Glacier contracts translate into action guards and next-state predicates.

**Objectives**

<div class="topic-list">
    <ol>
        <li><strong>Invariant Inference.</strong> Investigate how dynamic invariant detection techniques, inspired by Daikon, can be adapted to the RESTful API setting, inferring candidate invariants from sequences of HTTP responses and expressing them in Glacier syntax.</li>
        <li><strong>TLA+ Specification Generation</strong> Formalise the translation from OAS and Glacier files to TLA+ specifications, implementing it as an automated code generator and assessing correctness and completeness against manually authored counterparts.</li>
        <li><strong>Abstraction Control and Scalability</strong> Investigate heuristics for choosing appropriate domain sizes and abstraction levels — such as omitting schema fields irrelevant to reachability — to keep generated specifications within tractable bounds for model checking.</li>
        <li><strong>Evaluation</strong> Assess the full automated pipeline on real-world APIs from the [EvoMaster Benchmark](https://ieeexplore.ieee.org/abstract/document/10132197) and other publicly available services, measuring the quality of inferred invariants, the correctness of generated TLA+ specifications, and the resulting state space sizes.</li>
    </ol>
</div>

**Expected Contributions**

- A REST API automatic invariant inference framework, producing Glacier invariants from OAS files.
- A formal mapping from OAS extended with Glacier to TLA+, and its implementation as an automated specification generator.
- Heuristics for abstraction-level selection to maintain tractable state spaces in generated models.
- An empirical evaluation of the fully automated pipeline on real-world REST APIs.

**Team Integration**

The student will be fully integrated into the IcePick research team at NOVA LINCS, working alongside the framework's authors and contributing directly to an active line of research. This includes access to the existing IcePick codebase, Glacier toolchain, and benchmark infrastructure, as well as regular meetings with supervisors and the opportunity to co-author and publish results in relevant software engineering venues.

Interested? Reach out at acm.ribeiro (at) fct.unl.pt · [Download PDF](assets/files/topic-invariants-tla.pdf)
