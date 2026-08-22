# CHLOYA Glossary

> **Status:** public terminology reference  
> **Methodology revision:** `0.3.1`  
> **Language:** English

## Purpose

This glossary records the CHLOYA methodology's agreed English terminology. It is the source for links and wording in English-language chapters.

CHLOYA applies established engineering, risk-management, contract, least-privilege, human-control, and knowledge-management approaches to development involving temporary AI executors. A term's presence does not claim that CHLOYA first proposed the underlying idea.


<a id="alphabetical-contents"></a>

## Alphabetical contents

[A](#a) · [B](#b) · [C](#c) · [D](#d) · [E](#e) · [F](#f) · [G](#g) · [H](#h) · [I](#i) · [J](#j) · [K](#k) · [L](#l) · [M](#m) · [N](#n) · [O](#o) · [P](#p) · [Q](#q) · [R](#r) · [S](#s) · [T](#t) · [U](#u) · [V](#v) · [W](#w) · [X](#x) · [Y](#y) · [Z](#z)


<a id="a"></a>

## A

<a id="acceptable-risk"></a>

### Acceptable Risk

The level of risk that the owner of the relevant decision is willing to accept after considering the expected benefit, the cost of controls, and possible consequences. It is context-dependent: no single threshold is suitable for every task, resource, or environment.

An acceptable risk decision names both the decision owner and the assumptions on which it relies. It does not turn an unassessed or irreversible action into an acceptable one.

<a id="accepted-result"></a>

### Accepted Result

A result for which an authorized person, or a policy-permitted control plane, has decided to include a change in the project under stated conditions. The decision records what was accepted, on what evidence, and with which remaining restrictions.

Acceptance does not itself integrate, activate, deploy, or publish the result. Those are separate transitions and may require different authority.

<a id="acting-executor"></a>

### Acting Executor

The agent, workload, or execution component that directly initiates a technical operation. It can differ from the human or organizational function that owns the goal and the authority on whose behalf the action occurs.

Identifying the acting executor makes technical attribution possible without confusing it with accountability for the decision.

<a id="action-contract"></a>

### Action Contract

An explicit agreement defining a proposed action's allowed operation, target resource, parameters, preconditions, expected effect, and required evidence. It also states stopping and escalation conditions.

An action contract turns a broad request into a checkable operation. It is useful when an executor may be able to perform many operations but has been authorized for only one narrowly described change.

<a id="activated-change"></a>

### Activated Change

An accepted and integrated change that has begun to affect a running system, users, data, or the external world.

Activation is distinct from acceptance and integration. A change can be included in the project yet wait for deployment, migration, a release window, or separate authorization before it is activated.

<a id="active-context"></a>

### Active Context

Information directly transferred to an executor for the current task. It must be sufficient for the work, but need not contain every available project material.

Active context is a deliberately selected working set, not a copy of repository history, chat history, or every document the project owns.

<a id="acceptance-responsibility"></a>

### Acceptance Responsibility

The accountability of an authorized person or role for accepting a specific versioned result or effect within stated scope and conditions. It does not create a standing authorization for later changes.

<a id="action-proposal"></a>

### Action Proposal

A formal request produced by a reasoning component that identifies an intended operation, initiator, target resource, material parameters, environment, and expected effect. It is input to authorization, not evidence of permission.

<a id="actor"></a>

### Actor

The actual agent, workload, or execution component that performs a technical operation. The actor is recorded separately from the holder of the authority used.

<a id="agent-execution-trajectory"></a>

### Agent Execution Trajectory

The observed sequence of policy-material states, proposals, decisions, operations, and outcomes within one task or related tasks.

<a id="agent-trajectory"></a>

### Agent Trajectory

See [Agent Execution Trajectory](#agent-execution-trajectory).

<a id="ai-control-cost"></a>

### AI Control Cost

The total cost of governing AI use, including integration, verification, policy enforcement, monitoring, human review, incident response, and maintenance—not only the price of a model call.

<a id="attenuation"></a>

### Attenuation

The rule that a derived delegation may preserve or narrow its parent authority but must not expand it.

<a id="automation-bias"></a>

### Automation Bias

The tendency to over-rely on an automated recommendation or fail to detect its error, especially under time pressure, repetition, or weak understanding of its basis.

<a id="automation-profile"></a>

### Automation Profile

An explicit allocation of a workflow function’s stages among people, probabilistic components, and deterministic mechanisms, including authority and required checking points.

<a id="agent-execution-identity"></a>

### Agent Execution Identity

The identity under which an agent or its runtime performs a technical action. It must be distinguishable from the human or service that owns the goal or authority.

This distinction supports auditability: a record can say both who decided that work was appropriate and which workload actually made the call.

<a id="agent-modular-approach"></a>

### Agent-Modular Approach

An organization of development in which people, temporary AI executors, and tools divide work while context, responsibility, authority, and consequences are localized within semantic project areas.

In CHLOYA, modularity applies not only to source code, but also to project knowledge, tasks, decisions, risks, contracts, evidence, and areas of responsibility. This makes work transferable and limits the amount of unrelated material an executor needs.

<a id="ai-executor"></a>

### AI Executor

An AI model, agent system, or AI-based software tool assigned limited project work. Its ability to propose or technically perform an action does not itself authorize that action.

An AI executor is treated as a temporary executor: its session, budget, task, and authority can end without making the project dependent on its private interaction history.

<a id="api"></a>

### API

*Application Programming Interface* — a defined interface and set of rules through which one program or service accesses another program's functions or data.

For CHLOYA, an API is often an external contract and therefore may create a consequence boundary beyond the module that implements it.

<a id="architecture-as-an-attention-distribution-structure"></a>

### Architecture as an Attention-Distribution Structure

A view of architectural boundaries as a way to determine which knowledge an executor needs for particular work.

Architecture should help determine which context must be supplied, which internal details of neighboring areas may remain undisclosed, which contracts are mandatory, when a change stops being local, and when context must expand.

<a id="assigned-accountability"></a>

### Assigned Accountability

An explicit assignment of responsibility for a consequential decision, action, integration, or outcome to a named human role or policy-governed organizational function.

The assignment must remain understandable after the specific agent session or tool has ended. It is not satisfied merely by recording the name of the model that made a proposal.

<a id="authoritative-data"></a>

### Authoritative Data

Information from a controlled source on which a binding decision is made, such as an active policy version, resource state, role, delegation, or subject attribute.

Unlike a model's retelling, authoritative data has a system-defined provenance, freshness expectation, and retrieval method.

<a id="authority"></a>

### Authority

An explicitly granted right to perform a particular action within a defined area and under stated conditions. Technical capability is not authority.

Authority answers who may cause a particular effect; it must be bounded by operation, resource, parameters, time, and consequences where those distinctions matter.

<a id="authority-boundary"></a>

### Authority Boundary

The limit beyond which an executor must stop, request expanded authority, or hand the question to another decision owner.

An authority boundary need not match a context boundary or a code-module boundary. An executor can understand an area without being allowed to change it.

<a id="authority-scope"></a>

### Authority Scope

The set of operation classes permitted by issued authority or a token. In OAuth, this is commonly called a *scope*.

Scope alone is often insufficient: a safe authorization decision may additionally constrain the target resource, parameters, amount of change, time, environment, and allowed consequences.

<a id="authorization-control-plane"></a>

### Authorization Control Plane

The trusted part of an architecture that determines whether a proposed action is allowed from identity, delegation, active policies, authoritative data, and current system state. It does not originate the goal and must not independently execute the permitted operation.

**See also:** [Execution Plane](#execution-plane), [Policy](#policy), [Proposed Action](#proposed-action), [Reasoning Plane](#reasoning-plane).
[Back to top](#alphabetical-contents)


<a id="adapter-layer"></a>

### Adapter Layer

The means of presenting CHLOYA's canonical state and functions through specific protocols, formats, or agent environments. An adapter is replaceable and must not define the methodology's internal semantics.

<a id="alert-fatigue"></a>

### Alert Fatigue

A decline in human attention and response quality caused by a high volume of frequent, insufficiently material, or poorly prioritized warnings. In CHLOYA, its relevance to repeated requests for confirmation of agent actions remains a research hypothesis rather than an established fact.

<a id="adequate-attention-capacity"></a>

### Adequate Attention Capacity

The time and cognitive capacity a person has to assess a submitted decision, warning, or approval request substantively. Formal human participation does not provide meaningful control when volume, frequency, or complexity prevents the necessary attention from being given to each item.

<a id="adjustable-autonomy"></a>

### Adjustable Autonomy

An approach in which an executor's degree of independence varies with the type of decision, context, risk, available authority, and uncertainty instead of being fixed at one level for every action.

<a id="assumption-of-implementation"></a>

### Assumption of Implementation

A proposed but not yet accepted means of achieving a goal. Unlike an invariant, it may be replaced by another technical solution without violating the task's original goal.

<a id="artifact-trust-domain"></a>

### Artifact Trust Domain

The project, environment, platform, or other purpose for which a particular external artifact has been verified and permitted. Admission in one domain does not imply automatic admission in another.

<a id="authority-profile"></a>

### Authority Profile

A structured description of the independence delegated to a particular executor for a task. It states the permitted work scope, actions, resources, tools, environment, permissible impact limit, duration, and handoff conditions.

<a id="b"></a>

## B

<a id="bearer-token"></a>

### Bearer Token

A token usable by any party that possesses its value, without proving possession of a separate key. Leakage can enable reuse until expiry or revocation.

Bearer tokens are convenient but increase the significance of storage, transport, lifetime, audience, and logging controls. Where the threat model requires it, sender-constrained tokens reduce this replay risk.
[Back to top](#alphabetical-contents)


<a id="bureaucratic-control"></a>

### Bureaucratic Control

A check, approval, handoff, administrative artifact, or other control whose proportionate contribution to risk reduction, verifiability, or necessary authority has not been established in practice. It is defined by the absence of sufficient justification in the given context, not by the number of controls.

<a id="c"></a>

## C

<a id="canonical-project-state"></a>

### Canonical Project State

The coherent, project-recognized version of code, documentation, contracts, decisions, and other consequential artifacts on which subsequent work relies.

A local agent result does not become canonical project state automatically. It first has to pass the relevant verification, acceptance, and integration path.

<a id="canonical-source"></a>

### Canonical Source

An officially accepted source of project knowledge used as the basis for subsequent work. A conversation history, tool output, or individual agent response is not canonical automatically.

Canonical sources make it possible to replace an executor without losing the reason for an earlier decision or forcing the replacement to infer it from incidental traces.

<a id="capability"></a>

### Capability

A protected object, reference, or token whose possession grants a narrowly defined right over a resource. A capability may be delegated and attenuated.

Its use should remain subject to the constraints encoded with it or checked by the surrounding authorization system; possession is not a blanket right over the project.

<a id="caveat"></a>

### Caveat

An additional, verifiable condition on use of a delegated capability, such as a time limit, target resource, operation, location, environment, or other constraint.

Caveats make delegation narrower and inspectable. They should be enforceable by a trusted component rather than left to an executor's interpretation alone.

<a id="chloya"></a>

### CHLOYA

An open agent-modular methodology for governing software development involving people, AI executors, and engineering tools. It is not a model, a model aggregator, or a mandatory orchestration platform.

CHLOYA places human control over goals, architecture, risk, and acceptance alongside constrained authority for temporary executors, portable project memory, and evidence-based readiness.

<a id="ci-cd"></a>

### CI/CD

*Continuous Integration / Continuous Delivery (or Deployment)* — practices for regularly integrating changes and automatically delivering or deploying them.

Automation of integration or deployment does not replace authority checks, consequence assessment, or a decision about whether an AI-proposed change should be accepted.

<a id="cli"></a>

### CLI

*Command-Line Interface* — a text-based interface for operating a program or service.

In an agentic workflow, CLI access is a technical capability. It must still be bounded by the executor's authority and the environment's controls.

<a id="confirmed-state"></a>

### Confirmed State

A state that has passed the system's prescribed admission path and is recognized as authoritative for subsequent operations.

Before this transition, a model-generated artifact remains a proposal or draft even if it appears complete. Confirmation gives later work a defined object to rely on and preserves the distinction between suggestion and project decision.

<a id="consequence-boundary"></a>

### Consequence Boundary

The area of a system, product, or organization in which a change's effects must be assessed. The size of a code change does not determine the size of its consequences.

One small function can affect an external contract, several modules, users, security controls, stored data, or legal and operational obligations.

<a id="constrained-handoff"></a>

### Constrained Handoff

Transfer to an executor of only the task, information, responsibility area, and authority required for particular work.

Constrained handoff does not equate context transfer with authority transfer. Receiving a document, secret, or implementation detail is not permission to modify the associated resource or make its owner’s decision.

<a id="context"></a>

### Context

Information used by an executor to understand a task and make decisions: for example code, documentation, contracts, constraints, decisions, verification results, and risk information.

Context is not synonymous with instruction. Its parts can have different provenance and trust levels, and data must not silently become an instruction merely because it was placed in the same prompt or workspace.

<a id="context-engineering"></a>

### Context Engineering

The deliberate selection, structuring, and updating of information available to an executor for a particular task. Its aim is to provide sufficient, current, and attributable material without treating the whole project as active context.

Context engineering considers relevance, provenance, authority, freshness, and the conditions under which additional information may be requested.

<a id="context-layers"></a>

### Context Layers

Separated classes of task information that differ in purpose, authority, provenance, and trust level.

Typical layers include goal and constraints, approved project knowledge, task-specific materials, external data, and generated intermediate results. Separation prevents an untrusted data layer from silently becoming an instruction layer.

<a id="context-module"></a>

### Context Module

A stable semantic area of a system that can be understood, analyzed, or changed with limited knowledge of the rest of the project.

It need not correspond to a directory, package, service, or repository. A context module is defined by the coherence of its knowledge, contracts, responsibility, and consequence boundaries.

<a id="context-on-demand"></a>

### Context on Demand

Information not initially transferred to an executor but obtainable after discovering a dependency, contradiction, or lack of information.

Context on demand limits unnecessary disclosure while allowing work to proceed when a real dependency appears. Obtaining more information does not automatically expand authority.

<a id="context-provenance"></a>

### Context Provenance

Information about where a context item came from and how it entered a project or task. It can include the source, author, date, version, acquisition method, integrity, and applicability.

Provenance helps a reviewer distinguish an approved contract from an unverified web page, a current state record from stale output, and evidence from an unsupported assertion.

<a id="context-window"></a>

### Context Window

The bounded portion of input and prior interaction that a model can process in one invocation.

A larger context window does not guarantee equal attention to all included material, correct prioritization, or reliable recall. Context engineering therefore remains necessary even when the technical window is large.

<a id="contract"></a>

### Contract

An explicitly described obligation between system areas, participants, or process stages. It can define data format, behavior, compatibility, authority, transition conditions, and readiness criteria.

Contracts make a boundary explicit. They allow a local change to be assessed against the expectations of other modules, systems, users, and organizational processes.

<a id="controlled-context-expansion"></a>

### Controlled Context Expansion

Obtaining additional information after the initial context proves insufficient, while stating the uncertainty, requested material, its relation to the task, and any changed boundaries or risk.

The request is itself a governed transition: it should make clear whether more context resolves an information gap only or also requires a new authority decision.

<a id="credential-broker"></a>

### Credential Broker

A trusted component or logical role that, after authorizing a specific action, issues an executor a short-lived and limited technical authority instead of exposing persistent secrets to a model's free context.

**See also:** [Service for Issuing Temporary Tokens](#service-for-issuing-temporary-tokens), [Workload Identity Federation](#workload-identity-federation).

<a id="credentials"></a>

### Credentials

A secret or other identifier proving a subject, program, or workload's right to access a protected resource, such as a password, key, token, or certificate.

Credentials are not ordinary context. Their exposure, lifetime, storage, audience, and ability to be replayed must be considered separately from whether an executor understands the task.

<a id="current-project-state"></a>

### Current Project State

The officially accepted set of code, documentation, contracts, decisions, and other artifacts on which subsequent participants must rely.

An executor's local result is not included automatically. The project must preserve a visible transition from proposal or local output to an accepted, canonical state.
[Back to top](#alphabetical-contents)


<a id="compensating-action"></a>

### Compensating Action

A new controlled effect intended to reduce or correct the consequence of an earlier external effect that cannot be genuinely rolled back.

<a id="confirmed-baseline"></a>

### Confirmed Baseline

The latest state whose provenance, effects, and applicable constraints are known sufficiently to serve as a safe point for comparison, recovery, or new work.

<a id="confused-deputy"></a>

### Confused Deputy

A vulnerability in which a component with broad authority is induced by a less-privileged party to exercise that authority on the party’s behalf.

<a id="control-competence"></a>

### Control Competence

The knowledge, authority, and practical ability required for a person or role to make a substantive decision about a controlled proposal or effect.

<a id="controlled-declassification"></a>

### Controlled Declassification

A policy-defined, verifiable procedure that changes or removes a data restriction after an appropriate transformation or confirmation; it is not a model’s informal claim that data are safe.

<a id="control-plane"></a>

### Control Plane

The logical plane containing policies, permissions, action contracts, confirmed control parameters, and binding execution rules.

<a id="canonical-layer"></a>

### Canonical Layer

The primary, versioned, and documented representation of essential project state. It is independent of any particular server or execution tool and is sufficient to recover meaning and continue work.

<a id="capability-profile"></a>

### Capability Profile

A verifiable description of the task classes and conditions in which a particular model or execution class can achieve the required result. It is established through controlled and real tasks rather than inferred directly from price, model size, or product position.

<a id="central-coordinator"></a>

### Central Coordinator

A participant in a multi-agent system responsible for coordinating local executors or domains, including dependencies, cross-domain work, conflicts, and integration where required. It does not automatically own all local decisions or receive every executor's complete working context.

<a id="component-ablation-study"></a>

### Component Ablation Study

An experimental evaluation in which individual mechanisms of the process being studied are successively removed or replaced to determine their independent contribution to the observed result.

<a id="context-contamination"></a>

### Context Contamination

The entry of content that can undesirably alter an executor's understanding of a task, goal, proposed action, or later state. Context contamination does not by itself imply a successful authority violation.

<a id="context-expansion-for-an-identified-knowledge-gap"></a>

### Context Expansion for an Identified Knowledge Gap

A mechanism that adds information after a specific material question has been identified that the current context cannot answer sufficiently. It expands context as needed rather than attempting to read the entire project memory exhaustively.

<a id="context-projection"></a>

### Context Projection

A task-dependent representation of project memory containing information selected for a particular executor and current work. It may be reduced or derived, but does not replace the canonical knowledge source.

<a id="contract-challenge"></a>

### Contract Challenge

A formal notification by an executor of a fact, constraint, or consequence that calls the practicality or feasibility of the current contract into question. It can propose a revision, but does not authorize the executor to change the contract or exceed its authority.

<a id="contract-implementation-misalignment"></a>

### Contract–Implementation Misalignment

A state in which the operative or supplied contract and the actual implementation describe incompatible states of the same boundary, obligation, or system behavior. The discrepancy must be resolved by establishing which state was intentionally accepted.

<a id="control-proportionality-to-risk"></a>

### Control Proportionality to Risk

A principle that selects review depth, advance approval, human involvement, independent checks, and other controls according to the risk and consequences of a particular action.

<a id="controlled-degradation"></a>

### Controlled Degradation

A predictable reduction in convenience, speed, or automation after supporting tools become unavailable, without losing essential project state or the ability to continue work.

<a id="coordination-context"></a>

### Coordination Context

A minimally sufficient set of information about local work needed to coordinate dependencies among domains without transferring an executor's complete working context.

<a id="coordination-overhead"></a>

### Coordination Overhead

Additional time, computing, context-transfer, synchronization, approval, and conflict-resolution costs arising from the interaction of multiple participants or components rather than the original useful work itself.

<a id="cost-of-routing-error"></a>

### Cost of Routing Error

The additional computing, time, human, and other costs arising from an incorrect choice of execution class.

<a id="cumulative-task-cost"></a>

### Cumulative Task Cost

The total cost of obtaining an accepted result, including direct execution, routing, verification, human work, rework, and execution-class escalation.

<a id="d"></a>

## D

<a id="data-is-not-instruction"></a>

### Data Is Not Instruction

The principle that files, documents, web pages, issue-tracker items, comments, and tool results are objects of analysis. They do not automatically gain the right to change an executor's behavior.

This is especially important for prompt injection: untrusted material can ask for actions, but an executor must continue to follow the task, applicable contracts, and authorization boundaries.

<a id="decision-point"></a>

### Decision Point

A point in the operational cycle at which an authorized person or policy-permitted control plane chooses the next disposition of a result, task, or proposal from known authority, evidence, and consequences.

Possible dispositions include accepting, rejecting, integrating, activating, suspending, requesting more evidence, or escalating the question. A decision point makes that transition attributable rather than implicit.

<a id="delegation"></a>

### Delegation

The deliberate transfer of limited authority or a task to another participant while retaining a traceable connection to the authority owner, scope, constraints, and consequences.

Delegation is not abandonment of accountability. It must say what is delegated, to whom, for how long, under which constraints, and whether further delegation is allowed.

<a id="delegation-attenuation"></a>

### Delegation Attenuation

The principle that derived authority may preserve or narrow its parent authority but may not expand it.

Attenuation protects against a chain of agents gradually acquiring broader rights than the original decision owner granted. Each subsequent delegation remains bounded by its parent envelope.

<a id="delegation-envelope"></a>

### Delegation Envelope

A CHLOYA entity describing the boundaries of authority transferred to a particular agent execution: its owner, actual executor, task, operations, resources, environment, duration, scale, and onward-delegation rules.

The envelope makes the delegation inspectable and supplies a stopping point when a proposed operation does not fit the original grant.

<a id="deterministic-core"></a>

### Deterministic Core

The part of a system whose required behavior is defined by explicit rules, checks, and state transitions rather than by probabilistic model output.

Authorization, invariant checks, admission transitions, and irreversible-effect controls belong in a deterministic core whenever possible. A strong model output does not replace these independent checks.

<a id="devops"></a>

### DevOps

An approach that joins software development and operation through shared processes, tools, and responsibility for delivering and running a system.

CHLOYA can use DevOps practices, but automated delivery does not by itself decide authority, risk acceptance, or the readiness of an AI-produced result.

<a id="domain-model"></a>

### Domain Model

A formal description of subjects, actions, resources, their types, attributes, and relations against which the admissibility of an operation is computed.

A domain model prevents a policy engine from deciding only on vague labels. It gives authorization a shared vocabulary for the operation, its target, and the relevant context.

<a id="double-action-attribution"></a>

### Double Action Attribution

Recording both the authority owner and the actual technical executor for an action, so that delegation does not erase responsibility or accountability.

This attribution distinguishes “who was permitted to decide” from “which agent, workload, or tool initiated the technical call.”

<a id="dpop"></a>

### DPoP

*Demonstrating Proof of Possession* — an OAuth mechanism that binds a token to a client's public key and requires proof of possession of the corresponding private key [133].

DPoP is one way to make a token sender-constrained, reducing the usefulness of a copied token value to a party that lacks the associated private key.
[Back to top](#alphabetical-contents)


<a id="data-confirmation-status"></a>

### Data Confirmation Status

The explicit status showing whether data are proposed, derived, independently confirmed, disputed, stale, or otherwise limited for a stated use.

<a id="data-constraint-inheritance"></a>

### Data-Constraint Inheritance

The rule that restrictions of material input data remain associated with a derived object until a controlled procedure changes or removes them.

<a id="data-not-instructions"></a>

### Data-Are-Not-Instructions Principle

The rule that untrusted content does not acquire control authority merely because a model can parse it as an instruction.

<a id="data-plane"></a>

### Data Plane

The logical plane carrying documents, messages, source code, tool responses, and other processed content rather than binding control rules.

<a id="data-profile"></a>

### Data Provenance, Trust, and Use Profile

A set of independently retained characteristics that records data source, confirmed properties, currency, sensitivity, transformations, restrictions, and permitted recipients or uses.

<a id="data-provenance"></a>

### Data Provenance

The recorded history of data creation, acquisition, transformation, and responsible agents or systems.

<a id="degradation-profile"></a>

### Degradation Profile

The specified capabilities, retained guarantees, prohibited effects, evidence requirements, and restoration conditions of a degraded operating mode.

<a id="derived-data"></a>

### Derived Data

A new data object formed by transformation, combination, extraction, translation, classification, or generation from one or more inputs; it retains material provenance and applicable restrictions.

<a id="dual-attribution"></a>

### Dual Attribution

Recording both the holder of the authority used and the actual executor that performed a material operation.

<a id="data-portability"></a>

### Data Portability

The ability to export project data from one implementation and transfer it to another in an open or documented representation. It does not by itself guarantee semantic or process portability.

<a id="decision-owner"></a>

### Decision Owner

A defined human or organizational role accountable for a particular class of decisions or system domain. It may delegate work and limited local decisions without transferring accountability for the whole domain.

<a id="defect-escaping-initial-control"></a>

### Defect Escaping Initial Control

A defect in a result that was not detected by the controls provided for the task and is found at a later stage of development or operation.

<a id="delayed-verification"></a>

### Delayed Verification

A repeated assessment of a result or project state after a specified period or later changes, intended to reveal effects that cannot be determined reliably immediately after the original task is completed.

<a id="derived-layer"></a>

### Derived Layer

Indexes, databases, caches, graphs, vector representations, and other data derived from canonical state to make work more efficient. Losing a derived layer must not mean losing essential project knowledge.

<a id="development-state-portability"></a>

### Development-State Portability

The ability to transfer recorded project state to another tool or agent environment so that a new executor can recover essential decisions, constraints, tasks, and evidence and continue development without access to the prior implementation.

<a id="disagreement-between-representations"></a>

### Disagreement Between Representations

A material difference between visual, structural, extracted, transformed, or model-provided representations of the same source. In CHLOYA, it is grounds for additional verification, not evidence of an attack on its own.

<a id="disclosure-policy"></a>

### Disclosure Policy

A rule determining whether information may be transmitted to a particular recipient, considering the content and provenance of the data, the purpose, task domain, delegated authority, and applicable handling regime.

<a id="e"></a>

## E

<a id="effective-irreversibility"></a>

### Effective Irreversibility

A state in which a technical change can be reversed but its external consequences can no longer be fully eliminated, such as publication of a secret or data transfer outside the controlled environment.

Risk decisions must consider this practical, external irreversibility rather than only whether a repository commit or configuration file can be rolled back.

<a id="enterprise-ai-gateway"></a>

### Enterprise AI Gateway

An organization-managed layer for access to models and agent tools that can provide routing, access control, logging, model selection, data restrictions, and policy application.

It may make model use more governable, but it is not a substitute for task-specific authority, a trustworthy project memory, or verification of the resulting change.

<a id="escalation"></a>

### Escalation

Handing an unresolved question or decision to a participant with the required authority, competence, or accountability because the current executor lacks grounds to continue independently.

Escalation is a normal controlled outcome, not necessarily a failure. It prevents a temporary executor from filling a material uncertainty by guessing or extending its own authority.

<a id="escalation-condition"></a>

### Escalation Condition

A circumstance in which a decision must be handed to a participant with broader authority or necessary competence.

Examples include an external-contract change, an exceeded consequence boundary, missing evidence, an uncertain security impact, or a request beyond the delegation envelope. The recipient receives a minimally sufficient decision package, not necessarily all context.

<a id="escalation-package"></a>

### Escalation Package

A structured description of an unresolved question for the next decision-maker, including the goal, completed work, constraint, unperformed action, possible consequences, options, and authority required.

It should preserve the decision context rather than force the recipient to reconstruct it from an opaque interaction history.

<a id="evidence"></a>

### Evidence

A verifiable artifact confirming a particular property of a result, such as a test result, execution record, static-analysis report, contract check, migration verification, or review.

Evidence answers a defined question; it is not a generic claim that the work “looks correct.” Its provenance and relation to the stated readiness criterion must be inspectable.

<a id="evidence-package"></a>

### Evidence Package

The verification results and explanations sufficient to decide whether a change is ready. Its composition depends on task type, risk, consequence boundary, and verification difficulty.

The package can combine automated checks, review, records of performed operations, and an explicit account of residual risk. It supports a decision; it does not replace the decision owner.

<a id="execution-plane"></a>

### Execution Plane

The part of an architecture that performs a strictly authorized operation within issued technical authority.

It must not expand the operation's meaning, resources, or scope on its own. The execution plane enforces the distinction between an allowed, typed action and a more general tool capability.

<a id="executor-adapter"></a>

### Executor Adapter

A component or configuration that derives CHLOYA instructions, contracts, permissions, and tool connections from the portable core for a particular executor or agent environment.

An adapter accounts for provider-specific behavior, but must not become a competing source of truth about the project, its decisions, or its policies.

<a id="external-contract"></a>

### External Contract

An obligation relied on by other modules, systems, users, integrations, or processes.

Changing an external contract requires consequence assessment beyond the internal implementation of the changed area. It may trigger broader review, compatibility work, or escalation.

<a id="external-control-plane"></a>

### External Control Plane

Mechanisms outside a model's free reasoning that enforce system boundaries, including authorization, validation, isolation, environment restrictions, and state recording.

This plane keeps constraints effective when a model makes an error, receives unreliable context, or proposes an impermissible operation.

<a id="external-model"></a>

### External Model

An AI model or service that processes information outside the environment controlled by the project or organization. Its use requires separate assessment of data route, processing, storage, connected tools, and the permissibility of disclosing particular information.

External hosting alone does not determine either the risk level or the model's quality.
[Back to top](#alphabetical-contents)


<a id="effect-commit-boundary"></a>

### Effect Commitment Boundary

The controlled transition at which a prepared effect is allowed to alter authoritative or external state.

<a id="effect-representation"></a>

### Effect Representation

A checkable form of a prepared external effect, such as a diff, plan, manifest, recipient/content pair, amount, or change set.

<a id="escalation-routing"></a>

### Escalation Routing

Directing a bounded decision and its evidence to the role that has the appropriate authority and competence to resolve it.

<a id="external-control-loop"></a>

### External Control Loop

A mechanism outside the probabilistic component that observes, constrains, or authorizes actions and effects before they occur.

<a id="external-effect"></a>

### External Effect

An observable change to authoritative project state, an information system, or the external world that leaves an agent’s draft computation.

<a id="evidence-scope"></a>

### Evidence Scope

The declared claim, object version, environment, configuration, time, and conditions for which an item of evidence supports a conclusion; evidence outside that scope requires reassessment.

<a id="economic-profile"></a>

### Economic Profile

A versioned description of the current cost of using a model or execution class, taking account of access method, pricing, compute mode, caching, and other material costs. It refers to a particular environment state and can change independently of a capability profile.

<a id="error-back-escalation"></a>

### Error Back-Escalation

The transfer of evidence that a shared assumption is wrong, discovered by a local executor, to the owner of the parent decision so that decomposition can be reconsidered and genuinely dependent work can be stopped.

<a id="error-cascading"></a>

### Error Cascading

The spread of an erroneous assumption or result through dependencies among tasks, executors, and artifacts, causing later participants to use it as a basis for their own work.

<a id="error-propagation-radius"></a>

### Error Propagation Radius

The set of dependent tasks, decisions, and artifacts that have adopted an erroneous basis and may need reconsideration after it is disproved.

<a id="execution-class"></a>

### Execution Class

A set of task-execution environment characteristics, including the model, compute budget, available context, tools, data constraints, and other parameters that affect the ability and cost of achieving a result.

<a id="execution-class-escalation"></a>

### Execution-Class Escalation

A controlled transfer of a task, stage, or local question to another execution class after evidence shows that the current executor's capabilities are insufficient. It transfers sufficient continuation context, not necessarily the entire execution history.

<a id="execution-layer"></a>

### Execution Layer

The specific programs and services that use CHLOYA to perform work: agents, servers, IDEs, user interfaces, plugins, and coordinators.

<a id="external-artifact-identity"></a>

### External Artifact Identity

The set of characteristics that uniquely identify an admitted software object: component, version, source, exact file or image, checksum, and, where available, provenance information.

<a id="external-artifact-promotion"></a>

### External Artifact Promotion

The controlled transition of a particular version and artifact from an external candidate to one permitted for a specified project, environment, or use class.

<a id="f"></a>

## F

<a id="functional-contour"></a>

### Functional Contour

A semantic area of an operating model that groups related functions, decisions, and artifacts without having to coincide with one program, role, or organizational unit.

Functional contours help allocate ownership and evidence without pretending that a real operational responsibility always maps one-to-one to an application component.
[Back to top](#alphabetical-contents)


<a id="field-trial"></a>

### Field Trial

An evaluation of the methodology in a real or near-real development process that preserves natural work conditions, including incomplete task definitions, changing requirements, human decisions, accumulated context, and operational constraints.

<a id="g"></a>

## G

<a id="git"></a>

### Git

A distributed version-control system used to retain change history, collaborate, and recover project states.

Git may preserve a technical history, but its presence alone does not make a change reversible: external publication, data transfer, deployment, or a security incident can have consequences outside the repository.

<a id="governance-gap"></a>

### Governance Gap

A divergence between human intent and a system's actual evolution when the meaning of a goal, decision grounds, authority, or verification results is lost between participants or project states.

The gap grows when work is handed over as opaque chat history or unexplained patches rather than as a task capsule, decision record, contract, and evidence package.

<a id="governed-orchestration"></a>

### Governed Orchestration

Coordination of several executors, tools, and work stages with explicit allocation of task, context, authority, integration order, and accountable owner.

It does not require a single orchestration product. What matters is that coordination preserves boundaries and makes cross-executor transitions reviewable.
[Back to top](#alphabetical-contents)


<a id="h"></a>

## H

<a id="handoff"></a>

### Handoff

Transfer of work to another participant with enough information about the goal, completed work, decisions, constraints, and open questions to continue without the prior conversation.

A useful handoff carries the current decision context and evidence, rather than relying on the next participant to reconstruct intent from a long interaction history.

<a id="human-and-machine-readability"></a>

### Human- and Machine-Readability

The property of a project artifact that it can be understood by people and reliably processed by tools without making either audience dependent on an opaque representation.

Portable project memory should remain inspectable by a human while being structured enough for a tool to locate, validate, and transfer relevant parts.

<a id="human-control"></a>

### Human Control

The ability of a competent human to set goals, boundaries, and consequential decisions, and to understand enough of a system's state and evidence to exercise that authority.

Human control is not constant manual execution. It is retained when a human can define the authority boundary, review material changes, and stop or redirect a governed process.

<a id="human-goal-owner"></a>

### Human Goal Owner

The participant who determines a work's purpose, acceptable risk, consequential constraints, and criteria for an acceptable result.

The goal owner is distinct from the acting executor and may be distinct from a reviewer or policy enforcement component.
[Back to top](#alphabetical-contents)


<a id="human-decision-object"></a>

### Human Decision Object

A bounded, versioned representation of a proposal or effect that supplies an authorized person with the information needed to accept, deny, constrain, or redirect it.

<a id="implementation-extension"></a>

### Implementation Extension

Additional data or behavior used by a particular tool beyond the mandatory CHLOYA core. Failure to understand an optional extension must not prevent interpretation of essential project state.

<a id="independent-action-verification"></a>

### Independent Action Verification

A check of the permissibility of a proposed operation by a mechanism that does not depend solely on the same unconstrained model reasoning that produced the action proposal. It may consider the contract, authority, parameters, data provenance, and risk level.

<a id="independent-implementation"></a>

### Independent Implementation

An implementation of CHLOYA built from published specifications and formats without depending on the internal logic or undocumented semantics of the main reference implementation.

<a id="information-influence"></a>

### Information Influence

The permitted effect of context on an executor's knowledge, inferences, and task understanding without automatically changing its authority.

<a id="instrument-layer"></a>

### Instrument Layer

The set of local and external tools, adapters, connectors, protocols, and intermediaries through which an AI executor obtains external information or initiates actions outside its own reasoning process. Its components are not automatically trusted extensions of the executor.

<a id="insufficient-routing"></a>

### Insufficient Routing

The assignment of work to an executor whose capabilities prove insufficient to achieve the required result reliably under the specified quality and risk criteria.

<a id="i"></a>

## I

<a id="ide"></a>

### IDE

*Integrated Development Environment* — a software environment that combines code editing, execution, debugging, and other engineering tools.

An IDE can be one executor environment or one source of evidence; its convenience does not define the authority of an attached agent or plugin.

<a id="impersonation"></a>

### Impersonation

A mode in which an automated executor acts under another subject's identity and an external system may not distinguish the actual executor from the account owner.

Explicit delegation is preferred where possible, because it preserves double action attribution and can give the execution identity a narrower, revocable technical authority.

<a id="integrated-change"></a>

### Integrated Change

An accepted result included in the canonical project state and reconciled with current contracts, constraints, and project memory.

Integration does not automatically activate or publish it. The distinction lets a project accept and reconcile a result while retaining control over when it affects users, data, or external systems.

<a id="interaction-history"></a>

### Interaction History

The sequence of requests, responses, actions, checks, and corrections produced while working with AI.

It can be useful evidence, diagnostics, or an audit trace, but it is not canonical project memory automatically. Important decisions and accepted outcomes must be recorded in durable project-owned artifacts.

<a id="internal-contract"></a>

### Internal Contract

An obligation applying inside a context module or a limited project area.

Its change can remain local if it does not affect external consumers, cross-module contracts, or system requirements. The classification must be reassessed when new dependencies are found.

<a id="invariant"></a>

### Invariant

A property of a process or system that must remain true under permitted changes of tools, executors, scale, or execution order.

CHLOYA invariants constrain meaning rather than prescribe one implementation. For example, replacing a model or platform must not remove human authority over consequential decisions or turn a proposal into accepted state without the required transition.
[Back to top](#alphabetical-contents)


<a id="information-flow"></a>

### Information Flow

The directed movement of data or derived data among objects, components, environments, or recipients, assessed by source, transformation, destination, purpose, and active authority.

<a id="j"></a>

## J

<a id="json"></a>

### JSON

*JavaScript Object Notation* — a text format for structured data, commonly used for message exchange and configuration.

JSON can carry structured contracts or authorization requests, but a syntactically valid JSON object is not automatically a valid, authorized, or trusted instruction.
[Back to top](#alphabetical-contents)


<a id="k"></a>

## K

[Back to top](#alphabetical-contents)


<a id="knowledge-regression"></a>

### Knowledge Regression

The loss of material rationales, constraints, exceptions, or applicability conditions when project knowledge is edited, condensed, or transformed, even where the new representation appears more compact or formally polished.

<a id="l"></a>

## L

<a id="lethal-triad-of-agent-systems"></a>

### Lethal Triad of Agent Systems

The combination of access to private data, exposure to untrusted content, and the ability to communicate or act externally. Together these capabilities make prompt injection especially consequential.

The combination calls for architectural controls: data must not become instruction, external effects need authorization, and secrets should not be placed in a model's unrestricted context.

<a id="level-of-chloya-application"></a>

### Level of CHLOYA Application

The scale at which CHLOYA rules are used: a local change, context module, product, system or platform, or organization.

The levels do not form a required maturity ladder. A project can apply strict controls to one high-consequence change without first adopting every organizational-scale practice.

<a id="lightweight-mode"></a>

### Lightweight Mode

A mode for a low-risk, reversible, verifiable task that reduces procedural volume while preserving the goal, authority boundaries, result criteria, and stopping conditions.

Lightweight mode is not an exemption from governance. It is appropriate only while its assumptions remain true; discovering a broader consequence boundary or sensitive data requires mode escalation.

<a id="llm"></a>

### LLM

*Large Language Model* — a language model that processes and generates text, code, and other data sequences.

Plausible output is neither authority nor a system guarantee. An LLM may interpret a task and propose work, while deterministic components enforce the policy and state transitions that have consequences.

<a id="local-change"></a>

### Local Change

A change whose consequences stay within an explicitly defined area and do not violate external contracts.

A small change is not necessarily local. Locality follows from the assessed consequence boundary and contracts, not from line count or an executor's confidence.

<a id="local-model"></a>

### Local Model

An AI model operated in an environment controlled by the project or organization.

Local deployment does not itself guarantee adequate security, privacy, reliable isolation, or appropriate authority controls. The model still needs a bounded context and governed access to tools and resources.

<a id="locally-defined-accountability"></a>

### Locally Defined Accountability

An explicit assignment of responsibility for a module, contract, decision, change, or integration within a defined project area.

Local definition makes responsibility usable at the point of work, while preserving escalation paths when the decision exceeds the area’s authority boundary.
[Back to top](#alphabetical-contents)


<a id="lethal-trifecta"></a>

### Lethal Trifecta

The combination of access to private data, exposure to untrusted content, and the ability to communicate externally, which enables prompt-injection-driven data exfiltration.

<a id="localized-degradation"></a>

### Localized Degradation

Restriction of only the affected functions and dependencies when normal grounds are lost, while preserving unaffected confirmed operation and its guarantees.

<a id="local-ownership"></a>

### Local Ownership

A CHLOYA principle under which each stable system domain, material decision, contract, or change has a clear responsibility boundary and an owner accountable for the relevant class of decisions.

<a id="longitudinal-field-use"></a>

### Longitudinal Field Use

An evaluation of the methodology across a sequence of related changes over a sufficiently long period to assess cumulative and delayed effects that do not appear in a single local task.

<a id="m"></a>

## M

<a id="managed-autonomy"></a>

### Managed Autonomy

An executor's ability to act independently inside a predefined and technically enforced authority boundary.

It depends on reliable constraints, not on the absence of constraints. Autonomy increases when the permitted operation, evidence, and stop conditions are clear enough to make independent execution safe.

<a id="markdown"></a>

### Markdown

A lightweight text markup language that stores document structure and formatting in a human-readable form.

Markdown is suitable for portable project memory when conventions, explicit anchors, and version control make the intended structure stable for both people and tools.

<a id="mcp"></a>

### MCP

*Model Context Protocol* — an open protocol for connecting agent applications to tools, resources, and other context providers through structured interfaces [5].

MCP can make connections more structured, but the protocol itself does not grant authority to use every connected resource or tool.

<a id="mediation-layer"></a>

### Mediation Layer

An infrastructure layer between a user or project and a model that may route requests, filter data, connect tools, keep logs, or provide access to several providers.

The layer can centralize controls, but should not silently redefine the project’s canonical state, task authority, or accountability.

<a id="meta-policy"></a>

### Meta-Policy

A policy governing the creation, versioning, approval, activation, observation, and retirement of other policies.

Meta-policy makes policy administration itself governed: it identifies who may change a rule, what evidence or review is needed, and how an active version is recognized.

<a id="methodological-tool-neutrality"></a>

### Methodological Tool Neutrality

The principle that CHLOYA's required governance properties do not depend on one agent platform, model provider, file format, interface, or orchestration tool.

Implementations can vary, provided they preserve the methodological invariants: explicit authority, portable project memory, human control, and verifiable readiness.

<a id="minimally-sufficient-context"></a>

### Minimally Sufficient Context

The smallest justified body of information that enables a task while accounting for applicable contracts, constraints, and risks.

It is not simply the least data possible. Omitting a decisive contract or prior decision can make a context smaller but insufficient, causing unsafe inference or unnecessary escalation later.

<a id="mode-escalation"></a>

### Mode Escalation

A transition to stricter requirements after new risks, dependencies, or constraints are discovered.

Typical triggers include sensitive data, an external-contract change, an irreversible action, a broader consequence boundary, or contradictory context. Escalation adjusts the operating mode instead of pretending that the original low-risk assumptions still hold.

<a id="model-aggregator"></a>

### Model Aggregator

A service or platform that provides access to several models or providers through one interface.

CHLOYA does not aim to replace aggregators or create a universal one. An aggregator may be suitable for an acceptable-risk task only when routing, data retention, actual execution provider, cost, confidentiality constraints, and terms of use are understood.

<a id="model-token"></a>

### Model Token

A unit into which a particular model divides input and output data for processing and often cost calculation.

It differs from an access token, a bearer token, or a payment unit. A larger token budget is a resource constraint, not an expansion of the executor's authority.

<a id="mtls"></a>

### mTLS

*mutual Transport Layer Security* — TLS authentication in which both connection parties present and verify certificates.

It can bind a connection to a client or workload identity and is useful for protecting service-to-service calls. It does not independently determine whether the identified workload is authorized for a particular action.

<a id="multi-agent-work"></a>

### Multi-Agent Work

Work divided among several AI executors or agents whose tasks, context, authority, and result integration must be coordinated explicitly.

Adding agents does not distribute accountability away. Each handoff must preserve decision context, the delegation envelope, and the integration conditions for the resulting artifacts.
[Back to top](#alphabetical-contents)


<a id="meaningful-human-control"></a>

### Meaningful Human Control

Control in which a competent, authorized person can understand, change, or refuse a concrete decision before the corresponding accountable effect occurs.

<a id="methodological-overhead"></a>

### Methodological Overhead

The additional human, computing, time, and organizational costs arising from applying and maintaining methodological mechanisms rather than directly implementing the product's intended function.

<a id="minimum-useful-chloya-profile"></a>

### Minimum Useful CHLOYA Profile

The smallest set of CHLOYA mechanisms that provides practically material benefit for a specified class of projects or tasks relative to a simpler process. Additional mechanisms are included only where a corresponding risk or verifiable effect exists.

<a id="minimally-sufficient-control"></a>

### Minimally Sufficient Control

The amount and depth of control sufficient to keep risk within acceptable bounds and obtain the required evidence without adding checks, approvals, or restrictions that have no proportionate effect.

<a id="minimally-sufficient-execution-class"></a>

### Minimally Sufficient Execution Class

The least resource-intensive available execution class that can achieve the required result with acceptable risk under the specified conditions. Using it does not lower acceptance criteria.

<a id="model-economic-environment-snapshot"></a>

### Model-Economic Environment Snapshot

A recorded state at a given time of the available models, their versions, capability profiles, economic parameters, compute modes, and other conditions against which routing policy was determined or tested.

<a id="model-routing"></a>

### Model Routing

The selection of a model or execution class for a task, stage, or call based on required capabilities, risk, available context, economic parameters, and observed work state.

<a id="n"></a>

## N

<a id="nist-ai-rmf"></a>

### NIST AI RMF

*NIST Artificial Intelligence Risk Management Framework* — a framework for managing risks associated with AI systems [25].

CHLOYA uses such risk-management guidance as an external reference, not as a claim that a framework alone supplies task-level authorization or project-memory practices.

<a id="nist-ssdf"></a>

### NIST SSDF

*NIST Secure Software Development Framework* — a set of secure software-development practices [13].

Its practices can inform evidence, controls, and lifecycle work, while CHLOYA defines how temporary AI executors participate within explicit authority boundaries.
[Back to top](#alphabetical-contents)


<a id="necessary-control"></a>

### Necessary Control

A control that performs a defined and justified function: reducing a specific risk, constraining dangerous authority, preventing an irreversible action, independently checking a material assumption, obtaining required evidence, or transferring a decision to a sufficiently competent and authorized owner.

<a id="normative-influence"></a>

### Normative Influence

The effect of a source on rules, authority, mandatory constraints, or an executor's permitted actions. It is allowed only for sources granted the relevant right by the project's trusted control plane.

<a id="normative-strength-of-a-source"></a>

### Normative Strength of a Source

A property of a source that determines whether its content can establish or change project rules, constraints, decisions, or authority. Information reliability and normative strength are distinct characteristics.

<a id="o"></a>

## O

<a id="oauth-20-token-exchange"></a>

### OAuth 2.0 Token Exchange

A standard for exchanging one set of credentials for another to obtain new, limited authority for an action on behalf of a subject or through a delegation chain [131].

It can support short-lived, task-specific authority rather than exposing a long-lived secret to an executor. The resulting token must remain no broader than the authorized delegation.

<a id="oauth-target-resource"></a>

### OAuth Target Resource

The protected resource or resource server for which an OAuth access token is requested or issued.

Restricting the target resource helps keep authority tied to its intended recipient and limits the harm if a token is misused or a delegation is interpreted too broadly.

<a id="operational-cycle"></a>

### Operational Cycle

A recurring sequence from signal or intent through boundaries, context, preparation, verification, decision, integration, and project-memory update.

The cycle can include return for rework, suspension, and escalation. It describes controlled state transitions, not a mandate to use a particular agent framework or workflow engine.

<a id="operational-model"></a>

### Operational Model

An agreed description of how CHLOYA turns a signal or intent into a bounded, verified, and governably accepted project-state change without prescribing a particular platform or toolset.

It separates reasoning, authorization, and execution; identifies decision points; and records the evidence and project-memory update needed for a result to become usable by later participants.
[Back to top](#alphabetical-contents)


<a id="observation-period"></a>

### Observation Period

A policy-defined minimum age of a new release before its normal admission. Its length depends on the ecosystem, component class, and project risk.

<a id="over-routing"></a>

### Over-Routing

The use of a more resource-intensive execution class where a less costly available class could have produced the same acceptable result at the established risk level.

<a id="p"></a>

## P

<a id="parc"></a>

### PARC

An authorization-request model in which a decision is determined by *principal*, *action*, *resource*, and *context* [115], [124].

The structure makes a proposed operation explicit enough for policy evaluation and for later inspection of why a decision applied to this subject, action, and target.

<a id="pdp"></a>

### PDP

*Policy Decision Point* — see [Policy Decision Point](#policy-decision-point).

<a id="pep"></a>

### PEP

*Policy Enforcement Point* — see [Policy Enforcement Point](#policy-enforcement-point).

<a id="policy"></a>

### Policy

An explicit, versioned rule that connects an organizational requirement to a computable decision about whether a particular action is allowed and to a mechanism that enforces that decision.

A policy needs defined inputs, applicability, lifecycle, and enforcement point. Natural-language guidance alone can inform a decision, but should not be presented as deterministic enforcement.

<a id="policy-decision-point"></a>

### Policy Decision Point

A component that computes an authorization decision from applicable policies and authoritative input data [118], [119].

It determines whether the proposed action is permitted; it does not need to perform the action itself.

<a id="policy-enforcement-point"></a>

### Policy Enforcement Point

A component that requests an authorization decision and technically enforces it when a protected object is accessed [118], [119].

The PEP must apply the decision at the relevant technical boundary; merely logging a denial after the external effect is not enforcement.

<a id="policy-lifecycle"></a>

### Policy Lifecycle

The controlled sequence of drafting, reviewing, approving, activating, observing, changing, and retiring a policy.

Lifecycle controls preserve the ability to identify which policy version was active for a decision and who could authorize a change to that policy.

<a id="policy-management-plane"></a>

### Policy Management Plane

The function or components that create, version, review, approve, activate, and retire policies.

It is distinct from the point that decides or enforces one runtime action. Separating these planes limits the ability of an executor to alter the rule that governs its own request.

<a id="policy-observability"></a>

### Policy Observability

The ability to determine which policy, data, decision, and enforcement result affected an action, and to investigate deviations or failures.

Observability requires more than raw logs: relevant records must be attributable, sufficiently complete, and retained so that a reviewer can reconstruct the governed transition.

<a id="portable-core"></a>

### Portable Core

A human-readable, versioned set of CHLOYA goals, constraints, decisions, contracts, project memory, and rules from which materials for particular executors are derived.

It is portable across models and agent environments. Provider-specific adapters may transform or supplement it, but should not replace it as the project’s durable source of meaning.

<a id="prepared-result"></a>

### Prepared Result

An artifact created by an executor that has not necessarily been accepted, integrated, activated, or published.

Examples include an analysis, patch, migration, test, document, or escalation package. Calling it “prepared” preserves the distinction between a technically available output and a project-approved result.

<a id="privileged-intermediary-problem"></a>

### Privileged Intermediary Problem

A situation in which a component with broader authority is used by another party to perform an action that party could not perform itself [140]. Also known as the *confused deputy problem*.

The defense is to bind authority to the real requester, target resource, operation, and context rather than letting a privileged intermediary apply its own broad permissions without distinction.

<a id="probabilistic-component"></a>

### Probabilistic Component

A part of a system that uses probabilistic computation to interpret a goal, analyze context, make a plan, or propose an action.

Its output does not replace independent authority, invariant, or consequence checks. CHLOYA uses probabilistic components for reasoning while keeping binding transitions in deterministic controls where possible.

<a id="project-memory"></a>

### Project Memory

A portable, versionable representation of consequential project knowledge, including decisions, contracts, risks, verification results, and reasons for important choices.

Project memory must make continuation possible without the same model, provider, or chat history. It is not merely a vector index or an archive of uncurated conversation.

<a id="project-memory-provider-independence"></a>

### Project-Memory Provider Independence

The property that project memory remains usable after changing a model, platform, provider, or agent environment.

Independence reduces lock-in and preserves human reviewability. It requires stable, project-controlled artifacts rather than knowledge held only in a vendor session or proprietary agent state.

<a id="project-owned-memory"></a>

### Project-Owned Memory

Project memory controlled, stored, versioned, and made available by the project rather than by a particular model, provider, or agent platform.

The project can therefore inspect, correct, transfer, and preserve it even when a temporary executor or service is replaced.

<a id="project-state-transition"></a>

### Project-State Transition

The governed inclusion of a prepared result in the current project state.

Its stages can include verification, acceptance, merge, deployment, activation, or publication, but permission for one does not automatically permit the next. Explicit transitions prevent a proposal from acquiring consequences merely because a tool can reach the next stage.

<a id="prompt-injection"></a>

### Prompt Injection

An attempt to influence an executor through instructions embedded in data it processes, such as a document, web page, repository content, comment, or tool output [83]–[89].

The injected text can be persuasive, indirect, or formatted as if it were authoritative. The operational defense is to treat processed material as data, constrain tool authority, and require deterministic authorization before external effects.

<a id="proposed-action"></a>

### Proposed Action

A formal request to perform a specific operation, recording the operation, initiator, resource, parameters, and expected effect.

It is not authorization to execute the operation. A proposal becomes executable only after the applicable policy and authority checks approve this particular request.

<a id="proposed-result"></a>

### Proposed Result

A candidate solution, plan, change, or artifact that lacks sufficient evidence and has not been accepted by the project.

The label makes uncertainty visible. It avoids presenting a fluent model answer or an unreviewed patch as canonical project state.
[Back to top](#alphabetical-contents)


<a id="policy-enforcement-loop"></a>

### Policy Enforcement Loop

The runtime loop that receives a proposal, active policy version, and authoritative inputs; computes or receives a decision; enforces it; and retains material outcome evidence.

<a id="policy-management-loop"></a>

### Policy Management Loop

The governed lifecycle through which a policy requirement is formalized, validated, approved, versioned, distributed, and activated.

<a id="prepared-effect"></a>

### Prepared Effect

A concrete, checkable future state change that has not yet crossed the effect commitment boundary.

<a id="progressive-delegation"></a>

### Progressive Delegation

A controlled expansion of a defined automation scope only after evidence supports it; the scope remains revocable and can also be narrowed.

<a id="provenance-plane"></a>

### Provenance Plane

The logical plane linking data and control objects to their sources, versions, transformations, confirmations, and restrictions.

<a id="persistent-project-memory-contamination"></a>

### Persistent Project-Memory Contamination

The retention of unreliable, malicious, or unverified content in long-lived project memory in a way that can influence later tasks or other executors after the original attacking context has disappeared.

<a id="permissible-impact-limit"></a>

### Permissible Impact Limit

The maximum scale of changes or consequences an executor may cause within a delegated task, independently of the technical means used to achieve the result.

<a id="practical-methodology-usefulness"></a>

### Practical Methodology Usefulness

A measurable improvement in material characteristics of a real development process relative to a comparable simpler process, taking the methodology's own overhead into account.

<a id="practical-usefulness-domain"></a>

### Practical Usefulness Domain

The set of project classes, task classes, risk levels, and conditions for which a particular CHLOYA mechanism or profile demonstrates a practically material advantage over a selected baseline process.

<a id="pre-branch-verification"></a>

### Pre-Branch Verification

An enhanced verification of a material decision or assumption before starting a large number of dependent tasks. Its required depth depends on the potential radius of consequences as well as the decision's own risk.

<a id="principle-of-non-elevation-of-authority-through-context"></a>

### Principle of Non-Elevation of Authority Through Context

A CHLOYA rule that information an executor discovers in working context cannot by itself enlarge the scope of its permitted actions.

<a id="principle-of-non-elevation-of-trust-in-transformation"></a>

### Principle of Non-Elevation of Trust in Transformation

A rule that an agent's retelling, summarization, translation, structuring, or other transformation of information does not automatically raise trust in its provenance or grant it additional normative strength.

<a id="principle-of-provenance-preservation"></a>

### Principle of Provenance Preservation

A requirement to retain material information about the provenance and trust of information when it is transformed, transferred between executors, and written to long-lived state, until a separately verifiable status-changing event occurs.

<a id="process-portability"></a>

### Process Portability

The ability to continue real project work after its state is transferred to another tool or agent environment.

<a id="promotion-boundary"></a>

### Promotion Boundary

An organizational or technical boundary after which an external artifact becomes permitted for a specified trusted domain.

<a id="protective-delay"></a>

### Protective Delay

A deliberate period between the appearance of an external artifact and its normal admission to a trusted domain. It does not prove safety; it allows time for additional external evidence of possible problems to emerge.

<a id="q"></a>

## Q

[Back to top](#alphabetical-contents)


<a id="r"></a>

## R

<a id="reasoning-plane"></a>

### Reasoning Plane

The part of an architecture in which a person or probabilistic component interprets goals, analyzes context, and proposes actions. It does not itself make execution permissible.

<a id="reference-monitor"></a>

### Reference Monitor

A trusted mechanism that mediates each protected access according to policy, remains protected from modification, and is small enough to be analyzed [116], [117].

<a id="residual-risk"></a>

### Residual Risk

Risk remaining after prescribed checks and controls have been applied. Verifiable readiness does not mean that all risk has disappeared.

<a id="reversibility"></a>

### Reversibility

The ability to restore technical and factual state after an action. A backup, Git history, or reverse migration establishes only part of it.

<a id="risk-adaptive-autonomy"></a>

### Risk-Adaptive Autonomy

An approach in which the permissible degree of executor autonomy is chosen from the risk, reversibility, consequence boundary, available evidence, and human-control requirements of the particular task.
[Back to top](#alphabetical-contents)


<a id="rar"></a>

### Rich Authorization Requests (RAR)

The OAuth mechanism for expressing detailed authorization parameters beyond ordinary scope strings, such as a particular action, object, amount, recipient, or condition.

<a id="resource-indicator"></a>

### Resource Indicator

An OAuth parameter that associates a token with a particular protected resource or a narrowly defined audience.

<a id="safe-degradation-mode"></a>

### Safe Degradation Mode

An operating mode that reduces permitted functionality after normal grounds are lost while retaining mandatory guarantees and explicit restoration conditions.

<a id="scope"></a>

### Scope

The bounded set of authority, operations, resources, conditions, or effects to which a permission or delegation applies.

<a id="sts"></a>

### Security Token Service (STS)

A trusted service that issues short-lived credentials or exchanges verified identity and authorization context for constrained technical authority.

<a id="sufficient-deterministic-mechanism"></a>

### Sufficient Deterministic Mechanism

An existing or conventionally implementable non-probabilistic mechanism that provides a required function with acceptable quality, cost, and risk.

<a id="release-freshness-risk"></a>

### Release Freshness Risk

The additional uncertainty of a new version caused by insufficient time for a possible compromise, critical defect, or undesirable change to be discovered.

<a id="requirements-fixation"></a>

### Requirements Fixation

An effect in which the form or content of stated requirements excessively directs later design and reduces the likelihood that alternative solutions will be considered.

<a id="rework-multiplier"></a>

### Rework Multiplier

The ratio of the cost of dependent work that lost value because of an initial error to the cost of the work in which that error first arose. It is an experimental measure of how an early error amplifies later cost.

<a id="risk-of-obsolete-version"></a>

### Risk of an Obsolete Version

The risk of continuing to use an earlier accepted component after known vulnerabilities, end of maintenance, defects, or loss of compatibility have emerged.

<a id="s"></a>

## S

<a id="safe-state-after-suspension"></a>

### Safe State After Suspension

A task or system state in which stopping does not continue unauthorized impact and retained information is sufficient for later analysis and decision by a competent owner.

It does not require completing the task or discarding every earlier result. It does exclude automatic continuation of a potentially harmful operation after the executor has been suspended.

<a id="semantic-change-handoff"></a>

### Semantic Change Handoff

Transfer to another module or executor of the meaning and consequences of a change rather than the full development context.

It identifies the affected contract, compatibility implications, consumers, required checks, and activation conditions. The receiving party gets the information needed to make its own bounded decision without unnecessary disclosure.

<a id="sender-constrained-token"></a>

### Sender-Constrained Token

A token whose use requires proof of possession of a key or other identifier of a particular client or workload, reducing replay of a captured token [132], [133].

Binding the token to a workload or client makes theft of the token value alone less useful, though the associated key and runtime identity must still be protected.

<a id="separation-of-analysis-authorization-and-execution"></a>

### Separation of Analysis, Authorization, and Execution

The structural separation between proposing or analyzing an action, deciding whether it is allowed, and technically performing it.

One participant may serve more than one function only when the distinction remains explicit, attributable, and controlled. The separation prevents a probabilistic suggestion from silently becoming both its own authorization and its own external effect.

<a id="service-for-issuing-temporary-tokens"></a>

### Service for Issuing Temporary Tokens

A trusted service that issues short-lived, limited tokens or other technical authority for an authorized action and can revoke, rotate, or constrain that authority.

It limits the need to give a model persistent credentials. Issuance should follow a specific authorization decision and bind the authority to the intended operation, resource, and workload where feasible.

<a id="skill"></a>

### Skill

A package of instructions, knowledge, scenarios, or tools that extends an agent's capabilities for a defined class of work.

Its format depends on the agent environment. A skill can standardize useful practice, but it is not an independent source of authority and must follow the task’s contracts and policy boundaries.

<a id="slsa"></a>

### SLSA

*Supply-chain Levels for Software Artifacts* — a framework of practices and requirements for improving software supply-chain integrity [12].

Its concepts can support evidence about build provenance and artifact integrity; they do not by themselves determine whether a change is authorized or acceptable to a project.

<a id="spiffe"></a>

### SPIFFE

Specifications for identifying software workloads in dynamic, distributed infrastructure [130]. The name expands to *Secure Production Identity Framework for Everyone*.

SPIFFE supports a distinct workload identity so a runtime need not impersonate a shared human or service account when requesting bounded technical authority.

<a id="spiffe-id"></a>

### SPIFFE ID

A standardized workload identifier in the SPIFFE ecosystem. It identifies a workload within a trust domain and is not itself a secret [130].

The identifier is an input to trust and policy decisions; possession of the string alone is not proof that a workload is the subject it names.

<a id="spire"></a>

### SPIRE

An implementation of SPIFFE specifications that attests nodes and workloads and issues verifiable identity documents [130].

It is one possible implementation for workload identity and short-lived credentials, rather than a required CHLOYA component.

<a id="stopping-condition"></a>

### Stopping Condition

A predefined circumstance in which an executor must not continue an action.

Examples include missing required context, sensitive data outside the approved boundary, an unverified result, a conflict with an invariant, or an irreversible external action. A stopping condition makes suspension or escalation a specified response, not an improvised failure.

<a id="structured-authorization-request"></a>

### Structured Authorization Request

A machine-readable request that expresses an action, resource, parameters, and constraints so authorization can be decided with more precision than broad scopes alone.

It can carry the details needed for typed authorization, such as the actual target, amount, environment, and conditions, while retaining a record of what was requested.

<a id="suspension"></a>

### Suspension

A deliberate stop of an action until sufficient context, authority, evidence, or a competent owner's decision is available.

Suspension can retain and hand over safe prepared results without applying them to project state. It is appropriate when continuing would require the executor to guess, extend its own authority, or create an uncontrolled effect.

<a id="svid"></a>

### SVID

*SPIFFE Verifiable Identity Document* — a verifiable document binding a workload to a SPIFFE ID; it can be an X.509 certificate or JWT token [130].

An SVID supplies proof of workload identity for a trust decision, not unlimited authorization for every action available to that workload.

<a id="swe-bench"></a>

### SWE-bench

A benchmark of tasks for evaluating AI systems' ability to fix real software-repository issues [70].

Benchmark performance may inform an assessment of an executor’s technical capability, but it does not establish its authority, a project’s risk tolerance, or readiness of a particular change.

<a id="system-change"></a>

### System Change

A change whose consequences extend beyond a local implementation and require assessment across modules, contracts, products, or organizational processes.

The change may be small in code terms while still being systemic because it affects an external interface, shared data, security posture, deployment behavior, or an organizational commitment.
[Back to top](#alphabetical-contents)


<a id="semantic-portability"></a>

### Semantic Portability

The ability of an independent implementation to interpret correctly the meaning of CHLOYA's essential entities, states, constraints, and transitions rather than merely read their structural representation.

<a id="solution-exploration"></a>

### Solution Exploration

A bounded stage before the final choice of implementation approach in which an executor may analyze several ways to achieve the goal, identify hidden assumptions, and assess consequences without gaining additional authority to change the system.

<a id="solution-space"></a>

### Solution Space

The set of materially distinct ways to achieve a stated goal that remain permissible under the established invariants, risks, and other mandatory constraints.

<a id="specification-creep"></a>

### Specification Creep

An antipattern in which the volume of documents, descriptions, and derived artifacts grows faster than the project's durable useful knowledge and begins to increase the cost of searching, updating, and verification.

<a id="state-of-project-knowledge"></a>

### State of Project Knowledge

A status that determines an item's role in the current project, for example current, preliminary, superseded, or archived. Historically relevant knowledge must not automatically be treated as current.

<a id="syntactic-openness"></a>

### Syntactic Openness

The ability to read and process data through a publicly described format without dependence on a single specialized tool.

<a id="t"></a>

## T

<a id="task-context-capsule"></a>

### Task Context Capsule

A structured, bounded package of information for a task, including its goal, constraints, applicable contracts, known risks, and required result format.

A capsule can also name the authority boundary, evidence required, expected handoff form, and stopping or escalation conditions. It provides a reproducible starting point without transferring the entire project.

<a id="temporary-ai-executor"></a>

### Temporary AI Executor

An AI executor whose participation is limited by task, stage, session, budget, or time.

It must not become the only holder of project memory, architectural decisions, security rules, reasons for earlier choices, or current project state. The project must remain able to continue after replacing the model, agent, platform, or provider.

<a id="token-introspection"></a>

### Token Introspection

An inquiry to an authorization server to determine whether a token is active and what authority it carries.

Introspection can account for revocation and current state, but it depends on the central server’s availability and on clear semantics for which returned claims the enforcement point trusts.

<a id="trust-metadata"></a>

### Trust Metadata

Recorded information about a material's provenance, source, integrity, classification, review, or permitted use that helps an executor and control plane evaluate its trust status.

Metadata supports differentiated handling of context: for example, an approved contract may be authoritative, while a retrieved web page is analyzed as untrusted data.

<a id="trust-surface"></a>

### Trust Surface

The set of components, interfaces, data, identities, and assumptions whose compromise or failure can affect whether a decision or action remains trustworthy.

Mapping this surface helps decide which controls must be independent of a model and which data flows or intermediaries need special scrutiny.

<a id="trusted-boundary"></a>

### Trusted Boundary

The boundary within which components, identities, data flows, and enforcement mechanisms are trusted to satisfy stated assumptions.

Crossing the boundary requires explicit controls, such as verified identity, limited credentials, data restrictions, or an authorization decision. A network location alone is not necessarily a trusted boundary.

<a id="trusted-computing-base"></a>

### Trusted Computing Base

The minimum set of hardware, software, policies, and procedures that must work correctly for a system's security properties to hold.

The smaller and more analyzable the base, the more credible an enforcement claim can be. A model’s unrestricted reasoning should not be placed inside the trusted computing base for a consequential control when a deterministic alternative exists.

<a id="typed-authorization"></a>

### Typed Authorization

An approach in which action admissibility is computed over formally described and verifiable types of subjects, actions, resources, attributes, and context.

Typed authorization makes it harder to treat a broad natural-language request as sufficient permission. It enables a policy to decide on a specific operation and target rather than a vague class of intent.
[Back to top](#alphabetical-contents)


<a id="test-oracle"></a>

### Test Oracle

The defensible basis used to decide whether a test outcome is correct, such as a specification, invariant, trusted reference, authoritative state, or qualified human judgment.

<a id="token-exchange"></a>

### OAuth 2.0 Token Exchange

The OAuth mechanism for exchanging one set of credentials for another while representing the subject, actual executor, audience, scope, and other delegation constraints where supported.

<a id="trajectory-budget"></a>

### Trajectory Budget

An established limit on an accumulated effect along an execution trajectory, such as cost, operations, changed objects, transferred data, duration, retries, or subagents.

<a id="trajectory-checkpoint"></a>

### Trajectory Checkpoint

A state or transition where risk changes materially and policy, delegation, data currency, or human participation must be reassessed.

<a id="trajectory-policy"></a>

### Trajectory Policy

A policy whose decision depends on the current proposal together with relevant observed history, order of actions, accumulated effects, or preceding states.

<a id="trajectory-segment"></a>

### Trajectory Segment

A bounded sequence of steps permitted between checkpoints within defined resources, tools, data, authority, and cumulative limits.

<a id="trajectory-state"></a>

### Trajectory State

The minimum policy-material set of accumulated facts necessary to evaluate the next execution transition.

<a id="uncertain-effect-outcome"></a>

### Uncertain Effect Outcome

A state in which the system cannot yet establish whether a proposed external operation took effect, so speculative retry or compensation is not justified.

<a id="tooling-contour"></a>

### Tooling Contour

The set of tools, adapters, connectors, gateways, protocols, and supporting components through which an AI executor obtains external information or initiates actions outside its reasoning process. Tool calls are potential external effects, while tool responses are potentially untrusted external inputs.

<a id="tooling-withdrawal-test"></a>

### Tooling Withdrawal Test

An experimental portability test in which specialized servers, indexes, and the previous executor's history are made unavailable and a new executor must reconstruct project state from canonical data and continue a real task.

<a id="trust-boundary"></a>

### Trust Boundary

A boundary between system domains in which data, authority, or operations have different trust statuses. Crossing it must be governed by explicitly defined verification or status-change rules.

<a id="trust-elevation-event"></a>

### Trust Elevation Event

An explicitly recorded verification or decision after which information receives a higher trust status or normative strength, such as owner confirmation, independent reconciliation, or an integrity check.

<a id="trust-laundering"></a>

### Trust Laundering

An antipattern in which information of low or unknown trust comes to be treated as more trusted after retelling, aggregation, transfer between agents, or recording in a new artifact without an independent basis.

<a id="urgent-dependency-admission"></a>

### Urgent Dependency Admission

A controlled shortening of the normal observation period when the expected risk of continuing to use the current version exceeds the risk of immediate update. The reduced wait is offset by enhanced direct verification.

<a id="u"></a>

## U

[Back to top](#alphabetical-contents)


<a id="under-routing"></a>

### Under-Routing

The assignment of work to an executor whose capabilities are insufficient for sustained achievement of the required result under the established quality and risk criteria.

<a id="unverified-work-budget"></a>

### Unverified Work Budget

The permitted volume of dependent tasks or results that may develop at once from shared assumptions that are not yet fully confirmed. It prevents generation speed from persistently outpacing the system's capacity to verify and integrate results.

<a id="v"></a>

## V

<a id="verifiable-readiness"></a>

### Verifiable Readiness

A result state in which conformity with the task, contracts, and constraints is confirmed by sufficient evidence.

Completion of generation or a confident executor statement is not enough. Readiness is judged against the required evidence package, remaining risk, and the decision needed for the next transition.

<a id="verified-result"></a>

### Verified Result

A prepared result that has completed the prescribed checks and whose results are available for decision-making.

Verification reduces uncertainty but does not itself mean acceptance, integration, activation, or publication. Those transitions require the separately assigned authority.
[Back to top](#alphabetical-contents)


<a id="workload-federation"></a>

### Workload Federation

See [Workload Identity Federation](#workload-identity-federation).

<a id="validity-conditions"></a>

### Validity Conditions

The temporal, version-based, or event-based conditions under which project knowledge remains applicable. A change to a related contract, component, or assumption can require reconsideration regardless of the knowledge's calendar age.

<a id="w"></a>

## W

<a id="workload-identity"></a>

### Workload Identity

A verifiable identity of a program, process, container, or other workload used to make access and policy decisions independently of a human user's identity.

It supports least privilege and double attribution by identifying the runtime that acts, while a separate record can identify the human or organizational owner of the goal and authority.

<a id="workload-identity-federation"></a>

### Workload Identity Federation

A mechanism that exchanges a verified external workload identity for short-lived authority on a target platform without storing a permanent service key [136]–[138].

Federation is useful for temporary executors because authority can be issued for the current workload and task rather than copied into a prompt, repository, or long-lived agent configuration.
[Back to top](#alphabetical-contents)


<a id="weighted-cost-of-routing-error"></a>

### Weighted Cost of Routing Error

A metric that considers not only the number of incorrect executor-selection decisions but also the severity of their consequences, including rework, delay, human cost, and newly created risk.

<a id="x"></a>

## X

[Back to top](#alphabetical-contents)


<a id="y"></a>

## Y

<a id="yaml"></a>

### YAML

A text format for serializing structured data, often used for configuration and process descriptions.

Like other project artifacts, YAML can contain untrusted content or operationally consequential configuration. It must be interpreted under the applicable task and authorization boundaries, not treated as self-authorizing instruction.
[Back to top](#alphabetical-contents)


<a id="zero-trust"></a>

### Zero Trust

See [Zero Trust Architecture](#zero-trust-architecture).

<a id="z"></a>

## Z

<a id="zero-trust-architecture"></a>

### Zero Trust Architecture

An architectural approach that does not grant trust merely because a subject is inside a corporate network, uses an organizational device, or has a prior session. Access follows identity, state, and applicable policy checks [127], [128].

Zero trust architecture supports the CHLOYA distinction between an executor's presence in an environment and its authority for a particular operation.
[Back to top](#alphabetical-contents)


## Using the glossary

This is CHLOYA's public English glossary. English chapters keep their literary flow and use links to these definitions rather than repeated translations or long explanations.

Entries are ordered under the English alphabet A–Z. Each term uses an explicit HTML anchor so that links do not depend on automatic anchor generation. Links belong in ordinary chapter text, not headings, diagrams, or reference-definition blocks.

When Russian source material introduces a candidate term, its English equivalent is added here only after the Russian term and meaning are established. A glossary definition may cite the shared bibliography as `[N]` where needed.
