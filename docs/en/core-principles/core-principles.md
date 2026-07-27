# CHLOYA Core Principles at a Glance

> **Version:** `0.3.1`  
> **Status:** in translation
>
> The principles in this chapter form one new system for revision `0.3.1`. Until the current iteration is complete, their wording, order, number, and composition may change or be extended. The history of individual principles gains normative force only when `0.3.1` is fixed and work moves to `0.3.2`.

## 3.1. Purpose of the principles

The core principles are CHLOYA’s normative core. They define how human governance, responsibility, project knowledge, context, architectural boundaries, authority, actions, and evidence of results relate in AI-assisted development. Later chapters do not replace these principles; they explain how to apply them in projects of different scale and risk.

CHLOYA is not derived from one theory, technology, or software platform. It brings together classical modularity, contract-driven development, management of technical and organizational dependencies, context engineering, human oversight, constrained authority, and verifiable outcomes. David Parnas’s work shows that useful modularity is built around hiding decisions that can change independently rather than incidental division of a program into parts [76]. Research on socio-technical congruence adds that architectural dependencies and actual participant coordination must correspond; otherwise formal decomposition does not remove integration losses [77], [78]. Conway’s Law and *Team Topologies* show feedback between organizational structure, communication flows, and the architecture of the system being created [79], [80].

Agentic development adds the temporary nature of the AI executor. A new model or session does not automatically inherit a human understanding of the project; it reconstructs intent from the available context. A larger context window does not solve this on its own: information can formally be present while used inconsistently, especially when mandatory constraints are mixed with extensive secondary or outdated material [48], [49], [51], [53].

Agent actions also introduce a separate security foundation. Research on indirect prompt injection shows that a model can treat data from an external document, repository, email, or tool result as instructions and use it to choose later actions [1], [2], [24], [34]. CaMeL and Fides architectures, along with systematic patterns for securing agent systems, recommend not relying solely on model robustness: they separate the control flow from untrusted data and apply policy in a deterministic layer [83]–[85].

CHLOYA principles are therefore a system of mutual constraints rather than an independent checklist of good practices. Local work must not hide system consequences; human confirmation must not be ritual; technical capability must not become authority; a successful test must not automatically become proof of correctness; visual presentation must not replace source data; and transforming untrusted material must not silently turn it into trusted instruction.

<a id="compact-summary"></a>

## 3.2. Compact summary of principles

| No. | Principle | Short formulation | Main related chapters |
|---:|---|---|---|
| [P1](#p1) | **Human governance** | A person sets goals, boundaries, and material decisions | 7, 10, 14, 23 |
| [P2](#p2) | **Meaningful human governance** | Confirmation requires understanding consequences and risk | 7, 10, 14, 21, 23 |
| [P3](#p3) | **Assigned responsibility** | A task, change, and integration have an accountable owner | 7, 14, 16, 17, 24 |
| [P4](#p4) | **Temporary and replaceable executor** | A project does not depend on one person, agent, or session | 7, 13, 25, 29 |
| [P5](#p5) | **Proportionality** | Effort and control match scale and risk | 4, 6, 11, 14, 18, 21, 23 |
| [P6](#p6) | **Evolutionary adoption** | The methodology grows from a minimum useful contour | 4, 6, 11, 26, 27, 31, 32 |
| [P7](#p7) | **Human- and machine-readability of artifacts** | Representation works for people while structure remains available to machines | 9, 13, 21, 25, 29 |
| [P8](#p8) | **Project memory belongs to the project** | Canonical knowledge does not remain only in chats and agents | 13, 17, 25, 29 |
| [P9](#p9) | **Tool neutrality and portability** | The methodology is not tied to one model or platform | 13, 18, 26, 28, 29, 30 |
| [P10](#p10) | **Local sufficiency** | Context is constrained but sufficient for correct work | 8, 12, 13, 14 |
| [P11](#p11) | **Known provenance and trust** | Context has a source, status, and trust level | 8, 13, 22 |
| [P12](#p12) | **Data are not instructions** | Text being analyzed gains no authority | 8, 22 |
| [P13](#p13) | **Transformation does not automatically raise trust** | Summarizing, translating, and indexing do not cleanse data provenance | 5, 8, 13, 22 |
| [P14](#p14) | **Uncertainty requires marking and escalation** | Critical gaps must not be hidden by assumptions | 8, 14, 21, 22, 23 |
| [P15](#p15) | **Confidentiality by default** | Data transfer is constrained by purpose and trust boundary | 8, 19, 22, 24, 29 |
| [P16](#p16) | **Explicit policy for machine access and use** | Technical availability does not imply permission for external AI | 5, 19, 22, 24, 25, 29 |
| [P17](#p17) | **Deterministic core and constrained AI role** | Critical rules and policies do not belong to an LLM | 5, 9, 15, 18, 21, 22, 26 |
| [P18](#p18) | **Explicit contracts and semantic transfer** | Change impact is transferred through obligations and guarantees | 12, 15, 16, 17 |
| [P19](#p19) | **Local execution does not mean local consequences** | Execution scope and consequence scope differ | 11, 12, 14, 15, 16, 23, 24 |
| [P20](#p20) | **Separation of analysis, authorization, and execution** | Ability to propose an action gives no right to perform it | 5, 7, 8, 14, 22, 23, 24, 29 |
| [P21](#p21) | **Governed orchestration** | Delegation is constrained, observable, and verifiable | 7, 14, 16, 18 |
| [P22](#p22) | **Readiness is not activation** | An implementation is not enabled or propagated automatically | 14, 17, 21, 24 |
| [P23](#p23) | **Reversibility and limitation of consequences** | Rollback is planned; irreversibility is agreed in advance | 14, 17, 21, 22, 23 |
| [P24](#p24) | **Governed dependencies** | Reuse must reduce total risk and cost | 20, 22, 24, 26 |
| [P25](#p25) | **Publication requires separate authority** | Creating material does not grant the right to disclose it | 14, 17, 23, 24, 25 |
| [P26](#p26) | **Verifiable readiness** | Readiness is demonstrated by sufficient evidence | 6, 14, 21, 23, 24, 31 |
| [P27](#p27) | **Verifiability of the methodology itself** | CHLOYA is demonstrated in practice and revised from results | 6, 30, 31, 32, 33 |

## 3.3. Logic of the principle order

The principles are ordered not by when they appeared during work on CHLOYA, but by the movement from human intent to a verifiable project state. First come the people who set goals, make decisions, and accept responsibility. Next come the ways a project retains comprehensibility and continuity when executors and tools change. The principles then address context formation, data provenance, confidentiality, and interaction with external AI; draw a boundary between probabilistic reasoning and deterministic policy; set the order of transferring and executing actions; and finally state requirements for evidence.

The sequence is:

> human intent → assigned responsibility → project knowledge → permitted context → architectural constraints → governed action → evidence → accepted state.

This does not mean each transition needs a separate document or approval body. In a small reversible task, several stages may be combined. Their semantic difference remains: intent is not implementation, implementation is not permission to apply it, and application is not evidence that the goal was met.

When requirements conflict, legal, contractual, and mandatory organizational constraints come first. They are followed by security, confidentiality, intellectual property, and permissibility of disclosure; then established authority and a meaningfully made human decision; then correctness and verifiability of the result, maintainability and portability of project knowledge; and only then speed, cost, and convenience. This order prohibits the reverse logic in which token savings justify insufficient context, release speed justifies skipping verification, or technical ability to publish substitutes for the copyright holder’s authority.

## 3.4. Governance and responsibility

<a id="p1"></a>

### P1. Human governance · [back to summary](#compact-summary)

> A human sets the purpose, acceptable boundaries, and material decisions; AI may prepare, analyze, and execute only within those boundaries.

Human governance is not a requirement to manually perform every operation. It is the retention of control over the purpose of work, the permissible risk, and decisions whose consequences cannot be delegated to a temporary executor. The project must make visible which decisions are human decisions and which actions are delegated.

<a id="p2"></a>

### P2. Meaningful human governance · [back to summary](#compact-summary)

> Confirmation is valid only when its holder can understand the decision’s relevant consequences and risk.

A click, generic approval, or statement that a person “takes responsibility” does not make a decision meaningful. The person who accepts an action must receive enough context to understand what changes, what is not checked, which alternatives exist, and what residual risk is being accepted.

<a id="p3"></a>

### P3. Assigned responsibility · [back to summary](#compact-summary)

> Every task, change, integration, and publication-relevant transition has an identifiable accountable owner.

Responsibility cannot be distributed so broadly that no one is able to decide. An AI executor may contribute evidence and alternatives, but must not become a substitute owner. The owner need not perform all work; the owner must be able to make or escalate the required decision.

<a id="p4"></a>

### P4. Temporary and replaceable executor · [back to summary](#compact-summary)

> Material project knowledge and capability must survive replacement of a person, agent, model, or session.

An executor is a participant in the process, not the sole holder of its meaning. Goals, contracts, decisions, evidence, and unresolved risks are retained in portable project artifacts so another participant can continue with bounded recovery cost.

<a id="p5"></a>

### P5. Proportionality · [back to summary](#compact-summary)

> The depth of context, authority, documentation, and checking is proportionate to risk, uncertainty, and potential harm.

Small, reversible, locally verifiable work can use a lightweight contour. Protected data, public contracts, irreversible actions, production changes, and uncertain dependencies require stronger boundaries and evidence. The size of a diff alone is not a risk measure.

<a id="p6"></a>

### P6. Evolutionary adoption · [back to summary](#compact-summary)

> CHLOYA is introduced from a minimum useful contour and expanded only where a narrower contour no longer covers real consequences.

The methodology must not require a small project to imitate a large organization. A team can begin with clear task framing and acceptance, then add memory, contracts, policies, and orchestration as stable boundaries and risks make them necessary.

## 3.5. Project knowledge, artifacts, and portability

<a id="p7"></a>

### P7. Human- and machine-readability of artifacts · [back to summary](#compact-summary)

> Project artifacts must be understandable to people and structured enough for machine processing and verification.

Readable prose, diagrams, code, tables, and structured records serve different roles. Visual convenience must not hide source data or make important project knowledge recoverable only through one proprietary tool. Formats should permit review, comparison, validation, and reuse.

<a id="p8"></a>

### P8. Project memory belongs to the project · [back to summary](#compact-summary)

> Canonical project knowledge is retained by the project, not only by chats, vendor memory, or a particular executor.

Indexes, embeddings, caches, and agent memory may accelerate work, but cannot be the only source of goals, decisions, contracts, risks, and evidence. The canonical state must remain human-readable, versioned, and recoverable.

<a id="p9"></a>

### P9. Tool neutrality and portability · [back to summary](#compact-summary)

> CHLOYA must preserve its core meaning when models, tools, providers, and execution environments change.

Provider-specific instructions, skills, adapters, and servers may improve execution, but they must be derived from or linked to a portable core rather than become a competing source of truth. Portability means recoverable continuation with measurable cost, not identical behavior across models.

## 3.6. Context, trust, and machine interaction

<a id="p10"></a>

### P10. Local sufficiency · [back to summary](#compact-summary)

> An executor receives context sufficient for correct work inside its authorized area, not all available information.

Too little context forces unsupported assumptions; unlimited context hides constraints among noise, stale decisions, and untrusted material. A context package should explain its goal, scope, contracts, criteria, risks, and the reason each material item is included.

<a id="p11"></a>

### P11. Known provenance and trust · [back to summary](#compact-summary)

> Context has a known source, status, and trust level.

An agent must be able to distinguish an approved project decision from an unverified note, external issue, retrieved web page, or instruction embedded in untrusted content. Provenance and trust determine how material may be used, not merely whether it can be read.

<a id="p12"></a>

### P12. Data are not instructions · [back to summary](#compact-summary)

> Text, code, configuration, and tool output being analyzed do not gain authority to direct the executor.

This boundary is necessary against indirect prompt injection. An executor may analyze untrusted material as data, but it must not run commands, alter policy, disclose information, or expand authority because that material asks it to do so.

<a id="p13"></a>

### P13. Transformation does not automatically raise trust · [back to summary](#compact-summary)

> Summarizing, translating, indexing, or reformatting untrusted material does not remove its provenance or make it trustworthy.

Derived material can be useful, but it retains the limitations of its source unless a separate, accountable verification changes its status. A compact summary is not automatically safer than the original prompt-injection payload.

<a id="p14"></a>

### P14. Uncertainty requires marking and escalation · [back to summary](#compact-summary)

> Critical uncertainty must be named, bounded, and escalated rather than silently filled with assumptions.

When a task lacks a controlling requirement, needed authority, evidence, or a clear consequence boundary, the executor preserves safe work, pauses the affected action, and asks for the smallest decision or context extension that resolves the gap.

<a id="p15"></a>

### P15. Confidentiality by default · [back to summary](#compact-summary)

> Data transfer is limited by purpose, classification, and trust boundary.

Access to a file or system does not establish authority to send its content to an external model, service, or tool. Secrets, personal data, confidential source code, and derived project knowledge require minimization, permitted processing environments, and controls proportionate to disclosure consequences.

<a id="p16"></a>

### P16. Explicit policy for machine access and use · [back to summary](#compact-summary)

> Technical availability does not imply permission for a machine or external AI to read, use, retain, or transfer information.

Policy must define permitted data classes, models, services, tools, and actions. It should be enforceable where possible and preserve an audit trail of material decisions. A human request cannot override third-party rights or organizational limits that the requester does not own.

## 3.7. Architectural boundaries

<a id="p17"></a>

### P17. Deterministic core and constrained AI role · [back to summary](#compact-summary)

> Critical rules, policies, and authorization decisions do not belong solely to a probabilistic LLM.

AI may propose, classify, explain, and prepare changes, but deterministic controls should enforce authority boundaries, data policy, validation, and activation rules. This separation reduces the chance that a persuasive or injected instruction becomes an executable decision [83]–[90].

<a id="p18"></a>

### P18. Explicit contracts and semantic transfer · [back to summary](#compact-summary)

> The effects of changes are transferred through stated obligations, guarantees, and consequences, not only through files or diffs.

Contracts make interfaces, data formats, compatibility promises, and responsibility boundaries inspectable. A handoff records why a decision was made, what it affects, what was checked, and what remains uncertain so another executor does not need to reconstruct intent from implementation alone.

<a id="p19"></a>

### P19. Local execution does not mean local consequences · [back to summary](#compact-summary)

> The area in which work is performed and the area in which it creates obligations may differ.

A local edit can alter a public interface, release path, shared format, security policy, or another product’s assumptions. CHLOYA identifies the broader consequence boundary and transfers only the relevant impact to its owners instead of widening every executor’s context to the whole system.

## 3.8. Authority, actions, and integration

<a id="p20"></a>

### P20. Separation of analysis, authorization, and execution · [back to summary](#compact-summary)

> The ability to suggest or technically perform an action does not grant authority to execute it.

Reading, analysis, planning, proposal, authorization, execution, and activation are distinct transitions. Their combination may be safe for a low-risk local task only when the project explicitly defines that contour; it must not be assumed for destructive, external, or irreversible actions.

<a id="p21"></a>

### P21. Governed orchestration · [back to summary](#compact-summary)

> Delegation is constrained, observable, and verifiable.

Multiple agents can improve throughput only when their scopes, dependencies, authority, and integration conditions are explicit. Orchestration does not mean unlimited autonomous multiplication of executors; it manages handoffs, conflict resolution, and evidence across tasks.

<a id="p22"></a>

### P22. Readiness is not activation · [back to summary](#compact-summary)

> A technically prepared result is not enabled, deployed, published, or propagated automatically.

Activation is a separate decision that considers evidence, affected consumers, rollback or recovery, environment, timing, and accountable authority. A green local test or a completed pull request is not by itself permission to change production or disclose material.

<a id="p23"></a>

### P23. Reversibility and limitation of consequences · [back to summary](#compact-summary)

> Recovery is planned, while irreversible consequences are identified and agreed before action.

Git rollback does not undo a payment, public disclosure, external data transfer, or physical impact. Safe operation requires a limited first application, restore points, tested recovery, observability, and a decision appropriate to the actual consequence boundary.

<a id="p24"></a>

### P24. Governed dependencies · [back to summary](#compact-summary)

> External code, libraries, services, models, and agent tools are connected only after their necessity, provenance, risks, and lifecycle cost are assessed.

Reuse lowers development cost only when a component replaces material work and has an acceptable maintenance profile. The decision considers the share of functionality used, maturity, transitive dependencies, license, installation scenarios, replaceability, and compromise consequences. SLSA, NIST SSDF, and OpenSSF provide mechanisms for evaluating provenance and supply-chain integrity [12]–[14]. LiteLLM/Telnyx and SANDWORM_MODE further show that AI tools, agent configurations, and MCP servers are part of the same chain [10], [81], [82]. Waiting periods, version pinning, and quarantine execution are mechanisms for this principle, not substitutes for assessing a specific component.

<a id="p25"></a>

### P25. Publication requires separate authority · [back to summary](#compact-summary)

> Creating, changing, analyzing, or technically preparing material does not grant the right to disclose it outside the authorized area.

A public repository, article, issue, pull request, presentation, or transfer of code to an external executor can disclose secrets, trade secrets, internal architecture, working code, third-party material, or information relevant to patentability. A publication or IP gate is therefore a separate state transition, not the final technical step of development. Deleting material later does not guarantee removal from forks, indexes, caches, or local copies.

## 3.9. Evidence and methodology evolution

<a id="p26"></a>

### P26. Verifiable readiness · [back to summary](#compact-summary)

> A result is ready not because an executor says so or because code was generated, but because sufficient verifiable evidence supports the claimed property.

Evidence must be connected to the property claimed. Passing a general unit-test suite does not prove a specific data leak was fixed; a successful build does not prove backward compatibility. Property-based testing expresses this logic well: AI may propose a property or invariant, while a deterministic test tool searches for a counterexample. Agentic Property-Based Testing found that an agent can derive properties from code and documentation and create tests for large Python projects; after human review, 56% of generated reports matched real bugs and 32% were considered significant enough to report to maintainers [91]. The generated property itself still needs review: a failed test may expose a mistaken invariant, and a green test may be trivial or unrelated to the required behavior. Anthropic’s published process therefore combines property inference, automated counterexample search, agent reflection, and careful expert review of the bug report [92].

The amount of evidence is proportionate to risk. A small function may require local tests and diff review; a public contract, security, or production-state change needs a broader package covering consumer effects, recoverability, unverified areas, and explicitly accepted residual risk. Project claims, including future CHLOYA badges or labels such as `AI-friendly`, are also verifiable claims: they need a defined scope, version, verification date, and available basis.

<a id="p27"></a>

### P27. Verifiability of the methodology itself · [back to summary](#compact-summary)

> CHLOYA’s usefulness must be demonstrated by practical use, observable outcomes, and the ability to revise it.

Logical coherence does not demonstrate that applying the principles improves development. The methodology may reduce unnecessary context while increasing the cost of maintaining project memory; it may improve security while making a small task too heavy. These effects must be measured rather than concealed by a general statement about correct architecture.

Studies of AI’s effect on developer productivity already produce differing results: in some conditions tools speed up work, while in others experienced developers spend more time than they themselves expected [15], [16]. CHLOYA must therefore examine not only outcome quality but also the cost of applying the methodology. Pilot validation should show whether context localization lowers costs, portability between executors improves, integration becomes clearer, and evidence becomes more useful to people. Rules that offer no observable benefit, are not confirmed in practice, or create disproportionate overhead must be revised in later iterations.

## 3.10. Boundary between principles and mechanisms

A core principle must retain its meaning when tools, programming languages, and organizational scale change. A particular memory format, number of mandatory reviews, branching strategy, waiting period before a library update, use of Mermaid, skill set, or a custom MCP server are mechanisms for applying a principle, not necessarily independent principles.

For example, Mermaid can implement human- and machine-readable architectural diagrams, but P7 does not require Mermaid alone. CSV can preserve chart source data, while another domain may need a specialized format. A feature flag can help provide reversibility, but reversibility can be achieved in other ways. An MCP server can automate policy enforcement, but must not become the only carrier of the policies themselves.

This distinction makes it possible to develop the practical part of CHLOYA without constantly rewriting the normative core. The number of principles is not considered finally closed: before revision `0.3.1` is complete, new research and practical discussion may reveal propositions that cannot be fully derived from the existing rules.
