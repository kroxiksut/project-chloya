# CHLOYA Glossary

> **Status:** public terminology reference  
> **Methodology revision:** `0.3.1`  
> **Language:** English

## Purpose

This glossary records the principal terms of the CHLOYA methodology and their agreed meanings.

It is intended to:

* ensure consistent use of terms in documentation;
* distinguish closely related concepts;
* make individual chapters easier to read;
* prepare translations;
* support correct citation and discussion of the methodology.

The presence of a term in this glossary does not claim that the corresponding idea was first proposed in its entirety by CHLOYA. The methodology uses and develops established approaches from software engineering, risk management, contract-driven development, the principle of least privilege, human-in-the-loop practice, and knowledge management.

CHLOYA's distinctive feature is primarily the systematic application of these approaches to software development involving temporary AI executors.

---

## CHLOYA

**CHLOYA** is an open agent-modular methodology for governing software development involving people, AI executors, and engineering tools.

CHLOYA describes:

* dividing a system into semantic areas;
* limiting transferred context;
* allocating authority and responsibility;
* risk management;
* preserving project memory;
* verifying results;
* handing changes between areas;
* transitioning a prepared result into the current project state.

CHLOYA is not a standalone artificial-intelligence model, a model aggregator, or a mandatory agent-orchestration platform.

---

## Agent-Modular Approach

**Agent-modular approach** is an organization of development in which work is divided among people, temporary AI executors, and software tools, while context, responsibility, authority, and the consequences of changes are localized within semantic project areas.

In CHLOYA, modularity applies not only to source code, but also to:

* project knowledge;
* tasks;
* decisions;
* risks;
* contracts;
* evidence;
* areas of responsibility.

---

## AI Executor

**AI executor** is an artificial-intelligence model, agent system, or software tool to which limited project work has been assigned.

An AI executor can:

* analyze;
* propose solutions;
* create or modify artifacts;
* run permitted tools;
* prepare evidence;
* hand a result to the next participant.

The ability to propose or technically perform an action does not mean that the executor is authorized to perform it.

---

## Temporary AI Executor

**Temporary AI executor** is an AI executor whose participation is limited by a task, stage, session, budget, or time limit.

It must not become the sole holder of:

* project memory;
* architectural decisions;
* security rules;
* reasons for previous decisions;
* the current project state.

The project must remain capable of continuing work after replacing the model, agent, platform, or provider.

---

## Human Goal Owner

**Human goal owner** is a participant who determines the purpose of the work, acceptable risk, consequential constraints, and the criteria by which a result is acceptable.

The human need not manually perform every action, but must retain control over decisions whose consequences cannot safely be delegated.

The presence of a human in the process does not itself guarantee safety. The person must have sufficient competence and receive understandable information for decision-making.

---

## Context

**Context** is information used by an executor to understand a task and make decisions.

Context can include:

* source code;
* documentation;
* contracts;
* architectural decisions;
* constraints;
* requirements;
* change history;
* verification results;
* risk information;
* data from external sources.

The presence of information in a project does not mean it must be automatically transferred to every executor.

---

## Active Context

**Active context** is information directly transferred to an executor to perform the current task.

Active context must be sufficient for the work, but need not include all available project materials.

---

## Context on Demand

**Context on demand** is information not initially transferred to an executor but obtainable after discovering a dependency, contradiction, or lack of information.

Obtaining additional context must be purposeful and must not automatically expand an executor's authority.

---

## Minimally Sufficient Context

**Minimally sufficient context** is the smallest justified amount of information that enables a task to be completed with account taken of applicable contracts, constraints, and risks.

It does not mean seeking to give an executor as little data as possible at any cost.

Insufficient context can lead to erroneous assumptions, whereas excessive context can increase cost, analysis time, trust surface, and verification difficulty.

---

## Controlled Context Expansion

**Controlled context expansion** is an executor's obtaining additional information after the initial context proves insufficient.

The executor must:

1. identify the uncertainty discovered;
2. state what information is required;
3. explain its connection to the current task;
4. not perform the affected action until sufficient grounds are obtained;
5. check whether the task boundaries and risk level have changed.

---

## Context Module

**Context module** is a stable semantic area of a system that can be understood, analyzed, or changed with limited knowledge of the internal details of the rest of the project.

A context module can describe:

* purpose;
* boundaries;
* responsibility;
* inputs and outputs;
* external contracts;
* dependencies;
* consequential decisions;
* known risks;
* mandatory checks.

A context module need not correspond to a directory, package, service, repository, or operating-system process.

---

## Task Context Capsule

**Task context capsule** is a package of information, constraints, authority, and result criteria formed for a particular piece of work.

A capsule can include:

* goal;
* expected artifact;
* permitted area of change;
* necessary parts of the code;
* applicable contracts;
* prohibited actions;
* verification requirements;
* budget;
* stopping conditions;
* format of the returned result.

A context module is a relatively stable project area, whereas a context capsule is formed for a particular task.

---

## Constrained Handoff

**Constrained handoff** is the transfer to an executor of only the task, information, area of responsibility, and set of authorities required for particular work.

A constrained handoff can include:

* goal;
* expected result;
* permitted area of change;
* applicable contracts;
* known risks;
* acceptance criteria;
* result format;
* stopping and escalation conditions.

Transferring context does not automatically transfer authority.

---

## Local Ownership

**Local ownership** is the presence of a clear owner and responsibility boundaries for a module, contract, decision, change, or integration.

An AI executor can temporarily work in the relevant area but does not become its permanent owner.

The term does not mean local data storage and is unrelated to the transfer of property rights.

---

## Contract

**Contract** is an explicitly described obligation between system areas, participants, or process stages.

A contract can define:

* data format;
* permitted states;
* external behavior;
* compatibility requirements;
* mandatory checks;
* authority;
* transition conditions;
* readiness criteria.

Changing an internal implementation must not automatically be treated as changing an external contract.

---

## Internal Contract

**Internal contract** is an obligation that applies within a context module or a limited project area.

Its change can remain local if it does not affect external consumers or system requirements.

---

## External Contract

**External contract** is an obligation relied upon by other modules, systems, users, integrations, or processes.

Changing an external contract requires assessing consequences beyond the internal implementation of the area being changed.

---

## Semantic Change Handoff

**Semantic change handoff** is the transfer to a neighboring module or executor of a description of a change's meaning and consequences rather than the full context of its development.

It can contain:

* what changed in external behavior;
* which contract is affected;
* how compatibility is ensured;
* which consumers are affected;
* which checks were performed;
* when the new behavior is activated.

A diff shows implementation changes. A semantic handoff explains what those changes mean for the consumer.

---

## Project Memory

**Project memory** is a portable and versionable representation of consequential knowledge about a project.

Project memory includes:

* architectural decisions;
* contracts;
* history of consequential changes;
* reasons for decisions made;
* known risks;
* verification results;
* completed tasks;
* information about unresolved constraints.

Project memory must not exist only in chat history, a provider's internal memory, or the closed format of a particular agent platform.

---

## Project-Owned Memory

**Project-owned memory** is the principle that canonical knowledge must be stored in formats controlled by the project and remain available after replacing a model, agent, or provider.

Vector databases, indexes, caches, and internal storage of agent systems can be used as supporting means, but must not be the sole source of truth.

---

## Interaction History

**Interaction history** is the sequence of requests, responses, actions, checks, and corrections produced while working with AI.

It can contain:

* requirements;
* reasoning;
* errors;
* rejected options;
* test results;
* reasons for changes to decisions.

Interaction history can be a useful project asset, but must not automatically be considered canonical project memory.

---

## Context Provenance

**Context provenance** is information about where an information fragment came from and how it entered a project or task.

The following can be recorded:

* source;
* author;
* originating system;
* date;
* version;
* method of acquisition;
* scope of applicability;
* relationship to the current task.

---

## Trust Metadata

**Trust metadata** is a characteristic of context reflecting the degree to which it has been verified, is current, and is permissible to use.

Trust metadata must not be based only on the confident style of a text or the authority of the model that produced it.

---

## Data Is Not Instruction

**Data Is Not Instruction** is the principle that the contents of files, documents, web pages, issues, comments, and tool results are objects of analysis, but do not automatically gain the right to change an executor's behavior.

Text inside analyzed material may contain commands or prompt-injection attempts, but their presence does not create authorization to execute them.

---

## Separation of Analysis, Authorization, and Execution

**Separation of analysis, authorization, and execution** is the principle that the following must be distinguished:

1. identifying a possible action;
2. assessing whether it is permissible;
3. granting authority;
4. actually performing it.

An executor's ability to analyze or propose an action does not create authority to perform it.

---

## Authority

**Authority** is an explicitly granted right to perform a particular action within a defined area and under stated conditions.

Authority can be limited by:

* action type;
* module;
* environment;
* data;
* time limit;
* budget;
* risk level;
* need for additional confirmation.

The technical ability to perform an action is not authority.

---

## Authority Boundary

**Authority boundary** is the limit beyond which an executor must stop, request expanded permissions, or hand the question to another decision owner.

An authority boundary need not coincide with a context boundary or a software-module boundary.

---

## Risk-Adaptive Autonomy

**Risk-adaptive autonomy** is changing an executor's level of independence according to the risk of a particular task and action.

The assessment can consider:

* cost of error;
* scope of consequences;
* data sensitivity;
* reversibility;
* difficulty of verification;
* context uncertainty;
* provenance of tools;
* competence of the person making the decision.

CHLOYA does not seek maximum autonomy. Its goal is the maximum useful autonomy within justified boundaries.

---

## Escalating the Mode

**Escalating the mode** is a transition to stricter requirements after new risks, dependencies, or constraints are discovered.

Grounds can include:

* sensitive data;
* a change to a public contract;
* an irreversible action;
* going beyond the task area;
* a new external integration;
* contradictory context;
* absence of a competent decision owner.

The mode can be escalated after a task has already begun.

---

## Suspension

**Suspension** is a deliberate halt of a particular action until sufficient context, authority, evidence, or a competent owner's decision is obtained.

Suspension does not necessarily terminate the whole task. An executor can preserve and hand over safely prepared results without applying them to the current project state.

---

## Escalation Package

**Escalation package** is a structured description of an unresolved question handed to the next participant for decision-making.

It can include:

* original goal;
* completed part;
* constraint discovered;
* action not performed;
* possible consequences;
* solution options;
* authority or confirmation required.

An escalation package must enable a decision without fully repeating all previous work.

---

## Reversibility

**Reversibility** is the ability to restore the technical and actual state after an action has been performed.

The existence of Git, a backup, or a reverse migration confirms only part of reversibility.

---

## Effective Irreversibility

**Effective irreversibility** is a state in which a technical change can be reversed, but its external consequences can no longer be fully eliminated.

Examples include:

* a published secret;
* personal data transferred to an external system;
* a sent message;
* a payment made;
* a released public package.

Even a read operation can have irreversible consequences if the data obtained is transferred outside the controlled environment.

---

## Consequence Boundary

**Consequence boundary** is the area of a system, product, or organization in which the effect of a change must be assessed.

The size of a change does not determine the size of its consequences.

Changing one function can affect:

* an external contract;
* several modules;
* users;
* security;
* publication;
* legal obligations;
* organizational processes.

---

## Level of CHLOYA Application

**Level of CHLOYA application** is the scale at which the methodology's rules are used.

Possible levels are:

* local change;
* context module;
* product;
* system or platform;
* organization.

The levels do not form a mandatory maturity ladder and can be applied simultaneously.

---

## Verifiable Readiness

**Verifiable readiness** is a result state in which conformity with the task, contracts, and constraints is confirmed by sufficient evidence.

Completion of generation, the absence of obvious errors, or a confident executor message does not confirm a result's readiness.

---

## Evidence

**Evidence** is a verifiable artifact confirming a specific property of a result.

Evidence can include:

* a test;
* an execution result;
* a static-analysis report;
* a contract check;
* a verified migration;
* manual review;
* a description of affected areas;
* confirmation of compatibility.

Evidence must be connected to a specific requirement, risk, contract, or result version.

---

## Evidence Package

**Evidence package** is the set of verification results and explanations sufficient to decide whether a change is ready.

Its composition depends on:

* task type;
* risk level;
* consequence boundary;
* project requirements;
* difficulty of independent verification.

---

## Prepared Result

**Prepared result** is an artifact created by an executor that has not necessarily been accepted, applied, or published.

A prepared result can be:

* analysis;
* a patch;
* a diagram;
* documentation;
* a migration;
* tests;
* a solution design;
* an escalation package.

---

## Current Project State

**Current project state** is the officially accepted set of code, documentation, contracts, decisions, and other artifacts on which subsequent participants must rely.

An agent's local result does not automatically become part of the current state.

---

## Transition to the Current Project State

**Transition to the current project state** is the governed inclusion of a prepared result in the project's canonical state.

The transition can include:

* verification;
* acceptance;
* merging;
* publication;
* deployment;
* activation.

Authorization for a previous stage does not automatically grant authorization for the next one.

---

## Tool-Neutral Governance

**Tool-neutral governance** is the absence of a requirement to use a single model, platform, IDE, agent system, aggregator, or provider.

CHLOYA permits the use of:

* direct APIs;
* aggregators;
* local models;
* enterprise gateways;
* agent platforms;
* specialized tools.

The choice must take account of goal, cost, quality, confidentiality, and acceptable risk.

---

## Provider-Independent Project Memory

**Provider-independent project memory** is the ability to change the model, agent, platform, or means of accessing AI without losing a project's canonical knowledge.

This does not mean that all models are interchangeable in quality, cost, or capabilities.

---

## Enterprise AI Gateway

**Enterprise AI gateway** is an organization-managed layer for access to models and agent tools.

It can provide:

* routing;
* access control;
* logging;
* restrictions on data transferred;
* selection of permitted models;
* application of enterprise policies.

An enterprise gateway must not be considered automatically safe solely because it is hosted internally. Its architecture and rules require separate evaluation.

---

## Model Aggregator

**Model aggregator** is a service or platform that provides access to several models or providers through a single interface.

CHLOYA does not aim to replace aggregators or create its own universal aggregator.

Aggregators can be useful for tasks with an acceptable risk level if the following are understood:

* request routing;
* data-storage rules;
* the provider performing the work in fact;
* cost;
* confidentiality constraints;
* data-use conditions.

---

## Architecture as an Attention-Distribution Structure

**Architecture as an attention-distribution structure** is a view of architectural boundaries as a means of determining what knowledge an executor needs for particular work.

Architecture must help establish:

* which context must be transferred;
* which internal details of neighboring areas need not be disclosed;
* which contracts are mandatory;
* when a change ceases to be local;
* when context expansion is required.

---

## System Change

**System change** is a change whose consequences go beyond local implementation and require assessment across several modules, contracts, products, or organizational processes.

Systemic character is determined by consequences, not the number of files changed.

---

## Local Change

**Local change** is a change whose consequences remain within an explicitly defined area and do not violate external contracts.

A small change size does not guarantee locality.

---

## Canonical Source

**Canonical source** is an officially accepted source of project knowledge that must be used as a basis for subsequent work.

A canonical source can be:

* a document version;
* a contract;
* an architectural decision;
* a risk register;
* the current branch or a release;
* an approved project-memory entry.

Conversation history or an individual agent's response is not automatically canonical.

---

## Residual Risk

**Residual risk** is risk that remains after prescribed checks and controls have been performed.

Verifiable readiness does not mean that risk is entirely absent. A result must honestly identify known constraints and unverified assumptions.

---

## Acceptable Risk

**Acceptable risk** is the level of risk that the owner of the relevant decision is willing to accept, given the expected benefit, cost of control, and possible consequences.

Risk acceptability depends on context and cannot be determined universally for all tasks.

---

## Stopping Condition

**Stopping condition** is a predefined circumstance in which an executor must not continue the relevant action.

Examples include:

* discovery of sensitive data;
* absence of a required contract;
* going beyond the permitted area;
* inability to verify the result;
* emergence of an irreversible external action;
* contradiction between sources;
* absence of the necessary competence.

---

## Escalation Condition

**Escalation condition** is a circumstance in which a decision must be handed to a participant with broader authority or the necessary competence.

Escalation does not necessarily mean transferring all context. The next participant must receive the minimally sufficient package for making a decision.

---

## Using the Glossary

When adding a new term, check:

1. whether it is used in the published part of the methodology;
2. whether it differs from an existing concept;
3. whether its definition reveals a closed research roadmap;
4. whether the Russian and English names are consistent;
5. whether the term is used consistently across chapters.

Hypotheses, metrics, experimental plans, and preliminary claims of scientific novelty are not included in the public glossary.
