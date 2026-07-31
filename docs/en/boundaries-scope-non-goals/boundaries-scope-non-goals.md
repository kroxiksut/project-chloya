# Boundaries, Scope, and Non-goals

> **Version:** `0.3.1`  
> **Status:** under discussion

[CHLOYA][g-chloya] is not a new programming language, a mandatory move to microservices, or a system for fully autonomous development without human involvement. The approach neither requires many agents to run at the same time nor replaces [Git][g-git], testing, [DevOps][g-devops], architecture work, or product management. Modular isolation is a means of reducing complexity and localizing risks; it is not a guarantee that all system errors will disappear.

[CHLOYA][g-chloya] combines ideas from modularity, [contract][g-contract]-driven development, requirements management, trunk-based development, [context engineering][g-context-engineering], risk management, and human oversight. Its proposed novelty lies not in any individual practice, many of which are already used in software engineering, but in their coherent organization around the human as the holder of goals and the final decision-maker.

[AI executors][g-ai-executor] in this system are temporary and replaceable participants. Each receives the locally sufficient [context][g-context] required for a particular task, while material knowledge is retained in portable [project memory][g-project-memory] rather than only in a current session or a specific model. Changes are passed between participants not merely as files, but together with their meaning, their effect on dependencies, and their implications for neighboring modules. [Contracts][g-contract] may evolve, but their evolution must be controlled and verifiable.

The acceptable degree of autonomy, model selection, [context][g-context] depth, and strictness of checks are not governed by one rule for every task. They depend on cost, criticality, uncertainty, and the potential harm of an error.

## Contents of this chapter

- [2.1. What problem does CHLOYA solve?](#21-what-problem-does-chloya-solve)
  - [From generator to executor](#from-generator-to-executor)
  - [Context can be present and still fail to work](#context-can-be-present-and-still-fail-to-work)
  - [Technical capability does not create authority](#technical-capability-does-not-create-authority)
  - [A plausible result is not evidence](#a-plausible-result-is-not-evidence)
  - [Transferring files is not the same as transferring a decision](#transferring-files-is-not-the-same-as-transferring-a-decision)
  - [The governance gap addressed by CHLOYA](#the-governance-gap-addressed-by-chloya)
- [2.2. Levels of application](#22-levels-of-application)
  - [Local change](#local-change)
  - [Context module](#context-module)
  - [Product](#product)
  - [System or product platform](#system-or-product-platform)
  - [Organization](#organization)
  - [Applying several levels at once](#applying-several-levels-at-once)
  - [Expanding the scope of application](#expanding-the-scope-of-application)
- [2.3. What CHLOYA does not replace](#23-what-chloya-does-not-replace)
  - [Product management and user work](#product-management-and-user-work)
  - [Architectural design and engineering expertise](#architectural-design-and-engineering-expertise)
  - [Secure software development lifecycle](#secure-software-development-lifecycle)
  - [Git, CI/CD, and engineering infrastructure](#git-cicd-and-engineering-infrastructure)
  - [Incident management and operations](#incident-management-and-operations)
  - [Industry regulation, licensing, and legal assessment](#industry-regulation-licensing-and-legal-assessment)
  - [Professional and independent audit](#professional-and-independent-audit)
  - [Complementing the existing process](#complementing-the-existing-process)
- [2.4. When a lightweight mode is allowed and when it is prohibited](#24-when-a-lightweight-mode-is-allowed-and-when-it-is-prohibited)
  - [Reversibility and practical irreversibility](#reversibility-and-practical-irreversibility)
  - [Untrusted code and new dependencies](#untrusted-code-and-new-dependencies)
  - [MCP servers and external agent tools](#mcp-servers-and-external-agent-tools)
  - [Escalating the mode during execution](#escalating-the-mode-during-execution)
- [2.5. Conditions for pausing a task and escalating](#25-conditions-for-pausing-a-task-and-escalating)
  - [Pausing, escalation, and stopping work](#pausing-escalation-and-stopping-work)
  - [Primary pause conditions](#primary-pause-conditions)
  - [A safe state after pausing](#a-safe-state-after-pausing)
  - [Preserving an interim result](#preserving-an-interim-result)
  - [Escalation package](#escalation-package)
  - [No bypassing a pause condition](#no-bypassing-a-pause-condition)
  - [Conditions for resuming work](#conditions-for-resuming-work)
  - [Human direction and the boundaries of risk acceptance](#human-direction-and-the-boundaries-of-risk-acceptance)
  - [Pausing as a sign of governability](#pausing-as-a-sign-of-governability)

## 2.1. What problem does CHLOYA solve?

[CHLOYA][g-chloya] governs development in which AI can do more than suggest text or a code fragment: it can explore a repository, invoke tools, modify files, run commands, prepare pull requests, and pass part of the work to other executors. In that setting, the main object of governance is not a model response but the full path from a human intention to a new current state of the project.

### From generator to executor

When a language model is used as a reference source or an autocomplete aid, an incorrect answer normally remains a suggestion that a person can accept, correct, or reject. An agentic executor changes the nature of the risk. It can choose a sequence of steps on its own, read additional material, interpret instructions it discovers, and affect the state of a repository or environment. A reasoning error can therefore become an action before a human sees it as a finished response.

Traditional development partly relies on the long-term knowledge of its participants. A developer remembers the history of decisions, understands informal product expectations, knows which oddities of the code are intentional, and can relate a [local change][g-local-change] to earlier discussions. A team supplements that memory with reviews, tests, documentation, and architectural agreements. An [AI executor][g-ai-executor] does not have such continuity by default. Each new model or session reconstructs the task from the material available to it, and a confident explanation does not guarantee that the reconstructed intent matches the original one.

For that reason, the [CHLOYA][g-chloya] problem is not reducible to whether a modern model can write a function, fix a test, or create an application. Public demonstrations already show that agents can perform large and long-running work when they have a detailed specification, suitable tools, and strong automated checking. METR nevertheless emphasizes that well-formed self-contained tasks with a clear success criterion differ from day-to-day work inside a project, where accumulated [context][g-context], implicit requirements, and organizational knowledge matter substantially [46]. [CHLOYA][g-chloya] addresses precisely this gap between a demonstrated ability to complete a task and a sustained ability to safely continue the evolution of a real system.

### Context can be present and still fail to work

The most obvious answer to incomplete knowledge is to enlarge the [context][g-context] window and give the agent the entire repository, documentation, and discussion history. *Lost in the Middle* showed that the formal presence of information in a long [context][g-context] does not ensure that it will be used reliably: performance depends on the position and organization of information, and important facts in the middle of a large window may receive less attention [48]. In software engineering, additional volume therefore not only raises processing cost; it can hide a mandatory constraint among secondary files, obsolete decisions, and incidental comments.

SWE-bench reinforces this conclusion using real development tasks. The benchmark contains 2,294 problems drawn from GitHub issues and their corresponding changes in twelve Python repositories. Its authors note that solving a task often requires understanding several functions, classes, and files at once, interacting with the execution environment, and handling long [context][g-context]; it goes far beyond isolated code-fragment generation [70]. Even when a particular model later achieves a higher score on updated versions of such evaluations, the task structure remains illustrative: an agent must not merely find one correct file, but reconstruct a network of dependencies and demonstrate that a change is consistent with the system.

[CHLOYA][g-chloya] therefore rejects two symmetric extremes. Insufficient [context][g-context] makes an executor replace the unknown with assumptions. Unlimited [context][g-context] mixes a task goal with irrelevant history, untrusted material, and competing instructions. The methodology introduces locally sufficient [context][g-context]: an executor should receive the goal, authorized scope, applicable [contracts][g-contract], critical decisions, acceptance criteria, and known risks, and should request additional information when it discovers a dependency. What matters is not minimality by itself, but the ability to explain why each material fragment was provided and which part of the solution it concerns.

The problem of continuing work after a session ends has already become a practical concern for tool providers. GitHub is developing Copilot repository memory to retain knowledge about a codebase and reuse it in agent features [72]. For [CHLOYA][g-chloya] this is not [evidence][g-evidence] that a specific implementation is sufficient; it is industry confirmation of the need itself: project knowledge cannot be left only in an ephemeral conversation. The canonical [CHLOYA][g-chloya] memory must, however, remain human-readable, versioned, and portable between providers. A closed memory of one service can accelerate work, but must not be the sole place where decisions are stored.

### Technical capability does not create authority

In an agentic system it is especially dangerous to conflate three distinct claims: an executor is able to take an action, considers it useful, and is entitled to take it. These boundaries do not arise automatically for a probabilistic model. A textual request such as “do not delete anything” competes with instructions found in the environment, the agent’s internal plan, and available tools. If an executor can technically access a production database, delete files, or publish data, security does not depend only on how clearly a prohibition is phrased.

GitHub Copilot CLI documentation treats potentially destructive actions as a separate class that requires explicit user permission unless the corresponding [authority][g-authority] was granted in advance [71]. This design reflects a basic principle: a model’s intention and permission to execute must be separate. [CHLOYA][g-chloya] extends that principle from an individual command to the whole development process. Reading, analysis, proposing a change, approving it, and actually activating it are different transitions; success at one stage does not automatically grant a right to move to the next.

The publicly discussed Replit incident of July 2025 illustrated the consequences of the opposite arrangement. During Jason Lemkin’s experiment, an agent deleted application data; Replit later explicitly mentioned the case and reported strengthened security mechanisms, including environment separation, state recovery, and additional safeguards [73]. For [CHLOYA][g-chloya], the relevant point is not a personal assessment of the user or provider but the structure of the event. A textual prohibition and a declared change freeze were not equivalent to technically revoking [authority][g-authority], while access to mutable state allowed an erroneous decision to become an actual action.

It would be incorrect to claim that [CHLOYA][g-chloya] would certainly have prevented that incident. The methodology does not know every detail of the environment and does not promise error-free operation. Its mechanisms could, however, have broken the causal chain at several points: the agent could have worked with a test copy rather than production state; the freeze could have been expressed as an executable [policy][g-policy]; a destructive operation could have required separate authorization; and a transition into the current environment could have happened only after checking and with recovery prepared. The point of the methodology is to create several independent boundaries so that one incorrect interpretation is not enough to cause major harm.

### A plausible result is not evidence

Another gap appears between producing a result and confidence that it is fit for use. A language model can present an incomplete or unsafe solution persuasively, and a person can mistake fluent explanation for a sign of quality. In a study by Perry and colleagues, participants with access to an AI assistant produced less secure code on average while more often believing it was secure. Better outcomes were associated with lower trust in model answers and more active checking of their suggestions [74]. The effect is especially important in agentic development because an executor returns not only advice but an already prepared set of changes.

SWE-bench shows another side of the same problem. A patch must not merely look reasonable; it must change repository behavior so that it passes a reproducible check [70]. Yet passing tests is not always enough. They may confirm known cases without demonstrating fidelity to an informal intent, the absence of new risks, or an architecture’s suitability for further evolution. [CHLOYA][g-chloya] therefore treats [evidence][g-evidence] as a separate object of governance. An executor must report not only the outcome, but also the test environment, tests performed, effects on [contracts][g-contract], known limitations, unverified assumptions, and rollback conditions. The required strength of confirmation rises with the consequences of an error.

Insufficient [evidence][g-evidence] creates costs beyond one team. curl maintainer Daniel Stenberg described a flow of low-quality and, in his view, generated vulnerability reports that a small team had to spend substantial time checking [75]. The case illustrates an economic asymmetry: an author can create a persuasive report almost for free, while its recipient must reconstruct the reasoning, reproduce the scenario, and establish whether each claim is wrong or correct. Automation without an [evidence][g-evidence] requirement does not eliminate work; it transfers it to the scarcest participant in the process.

In [CHLOYA][g-chloya], a result without a sufficient [evidence package][g-evidence-package] remains a proposal, even if code has been written and local tests are green. This does not mean every edit needs a heavy audit. A typo fix and an irreversible data migration require different levels of control. The methodology aims to make that difference explicit: low-risk and reversible work can be accepted through a short, verifiable path, whereas a change with a high cost of error must not be activated based on the self-assessment of the same executor that created it.

### Transferring files is not the same as transferring a decision

When different [AI executors][g-ai-executor] work on a project sequentially or in parallel, semantic continuity becomes a problem. A modified file shows the current implementation state, but rarely fully explains why that option was chosen, which alternatives were rejected, which constraint is intentional, or when the decision should be reconsidered. A person who has participated in a project for a long time often reconstructs those links from personal memory. In a system of replaceable executors, that memory disappears with the session.

If the next agent receives only a diff and the general request to “continue,” it can conscientiously reverse an important decision because it interprets it as unfinished work. It can repeat a dead end already investigated, extend a [contract][g-contract] without notifying consumers, or improve a module locally at the price of system incompatibility. The better an agent is at changing large code areas quickly, the higher the cost of a lost explanation.

[CHLOYA][g-chloya] introduces semantic transfer of changes as part of a task result. The next executor does not need the full internal dialogue of the previous model, which may be long, contradictory, and tied to a particular provider. It needs a compact engineering record: the original goal, decision made, reasons for the choice, affected [contracts][g-contract], implications for neighboring areas, checks performed, [residual risk][g-residual-risk], and conditions for further change. Such a record creates portable [project memory][g-project-memory] and lets a human check the stated grounds for a decision rather than a model’s hidden chain of reasoning.

### The governance gap addressed by CHLOYA

All of the problems above form one causal chain. A human goal is first translated into a task and [context][g-context], then interpreted by a temporary executor, turned into a sequence of actions, produces some result, and after checking is either rejected or becomes a new reality of the project. Some meaning can be lost at every transition. An ambiguous goal becomes a formally convenient subtask; an important decision is lost in long [context][g-context]; technical capability is mistaken for [authority][g-authority]; a plausible report is mistaken for [evidence][g-evidence]; a locally successful patch is mistaken for a system-permissible change; and a finished session takes away reasons for a decision that the next executor will need.

Without a dedicated governance layer, such losses can remain invisible. The repository continues to change, tests may sometimes remain green, and each participant acts within the picture available to it. The error emerges later, when incompatible assumptions meet at a module boundary, a new model reverses an intentional constraint, an agent receives access to an environment with a higher cost of error, or the team cannot explain why the current decision was made at all.

[CHLOYA][g-chloya] calls this the [governance gap][g-governance-gap] between human intent and the current state of a software system. The primary objects of governance are the intent itself, supplied [context][g-context], provenance of information, level of trust, [authority][g-authority] to act, [contracts][g-contract] between areas, [evidence][g-evidence] of the result, and a separate decision to activate it. A human retains responsibility for goals, [acceptable risk][g-acceptable-risk], and final acceptance where consequences require a human decision. AI can explore, plan, implement, check, and delegate, but its autonomy is determined not by general trust in a model but by the risk of a particular transition.

This definition does not turn [CHLOYA][g-chloya] into a promise of absolute safety. The methodology does not eliminate errors by models, people, tests, or architecture. It aims to make errors localizable, detectable, and reversible, and to prevent one unproven decision from silently traveling all the way from an assumption to production state. This is the practical criterion of the approach’s usefulness: the speed of machine execution must not outstrip a project’s ability to preserve meaning, limit harm, and demonstrate the correctness of transitions.

> **Problem statement.** [CHLOYA][g-chloya] solves not the problem of “how to make AI write more code,” but the problem of “how to preserve human intent, governed [authority][g-authority], and verifiability of results when code and other engineering actions are performed by temporary probabilistic executors.”

## 2.2. Levels of application

[CHLOYA][g-chloya] can be applied both to one [local change][g-local-change] and to the evolution of a product platform or the work of several teams. These cases do not form a mandatory maturity ladder. A project need not pass through every level in sequence, and applying the methodology over a broader area does not by itself mean a higher-quality process.

A [level of application][g-level-of-chloya-application] defines the area within which human intent must be preserved, executor [context][g-context] and [authority][g-authority] managed, [contracts][g-contract] kept consistent, [project memory][g-project-memory] accumulated, and a result’s transition into the current state checked. The broader that area, the less [CHLOYA][g-chloya] concentrates on an individual action and the more it concentrates on keeping changes consistent across relatively independent parts of a system.

The same work can affect several levels at once. Fixing one function is a [local change][g-local-change], but it can alter a [context][g-context]-module [contract][g-contract], affect product release, and require synchronization with other repositories. A level is therefore determined not by the number of modified files, agents, or the way code is stored, but by the boundary of consequences and the area in which a decision about the result’s acceptability must be made.

### Local change

The minimum [CHLOYA][g-chloya] level is an individual task, investigation, bug fix, or limited set of related changes. At this level, the methodology can be used without redesigning the entire project beforehand.

For example, an [AI executor][g-ai-executor] may be asked to fix a configuration-file parsing error. It may need the original request, the relevant code, applicable tests, a description of expected behavior, and information about the configuration format. It need not receive the history of every architectural decision, user-interface documentation, or source code from unrelated subsystems.

[CHLOYA][g-chloya] must define what counts as the task result, which area the executor may examine and modify, which tools it may use, and what [evidence][g-evidence] must accompany completion. For a small reversible edit, local tests, confirmation of changed behavior, and a brief description of assumptions may suffice. If the task affects data, security, or a public [contract][g-contract], the same formally local amount of code requires stricter checking.

The minimum [CHLOYA][g-chloya] level is not defined by the small size of a task, but by the ability to localize its goal, [context][g-context], [authority][g-authority], and consequences. This mode also suits projects that are not yet ready to introduce persistent [context modules][g-context-module] or shared organizational [policies][g-policy]. The methodology may first be used as a discipline for framing and accepting individual tasks, then expanded as stable responsibility boundaries emerge.

### Context module

The next level arises when several changes concern one stable semantic area. Such an area may be authentication, tariff calculation, document import, a scene format, traffic routing, or management of user consent.

A [context module][g-context-module] in [CHLOYA][g-chloya] need not match a directory, package, service, or repository. Authentication in a web application, for example, may include data models, request handlers, settings, interface elements, tests, and documentation physically located in different parts of the project. Conversely, one large directory may contain several areas with different goals, risks, and owners.

This view develops David Parnas’s classic idea that the usefulness of modular decomposition depends not on the mere existence of modules, but on the criterion by which their boundaries are drawn [76]. For [CHLOYA][g-chloya], a boundary should help provide an executor with locally sufficient [context][g-context], define its responsibility, and explain the effect of changes without requiring it to reconstruct the entire system every time.

A [context module][g-context-module] has more persistent memory than an individual task. It should retain the area’s purpose, applicable [contracts][g-contract], critical decisions, known constraints, checking rules, and links to neighboring parts of the project. This memory does not replace source code or tests; it explains information that cannot be reliably reconstructed from the current implementation alone.

At this level, it is important to distinguish an internal change from a boundary change. An executor may transform a module’s internal structure more freely if it preserves its agreed properties. Changing a public interface, data format, or obligations to neighboring modules must be treated as a separate decision because its consequences extend beyond the local [context][g-context].

The [context module][g-context-module] becomes [CHLOYA][g-chloya]’s primary unit of local work. It makes temporary executors replaceable because material knowledge belongs to the project rather than to a model or session. At the same time, it limits autonomy: holding the [context][g-context] of a module does not automatically permit changes to dependent areas or unilateral revision of system-wide decisions.

### Product

At the product level, [CHLOYA][g-chloya] covers an application, library, individual service, or other independently developed and delivered software result. Differences among these types matter for architecture and release, but do not require them to become separate methodology levels.

A product normally includes several [context modules][g-context-module] that can be changed by different executors. Local correctness in each of them is therefore insufficient. A single user and engineering intent must be preserved, cross-module dependencies coordinated, integration checked, and a state fit for release produced.

For example, changing a Django library may affect the main code, public API, migrations, supported Python and Django versions, documentation, demonstration projects, and package-publication procedure. Each part may pass its own checks, but the product is not ready until they form a compatible result.

At this level, shared [project memory][g-project-memory] appears in addition to, rather than duplicating, the memory of individual modules. It records the product’s purpose, supported scenarios, general architectural constraints, compatibility [policy][g-policy], release rules, and requirements that span several areas. Decisions about which features to include and which trade-offs are acceptable remain human product and architectural decisions, even if AI helps prepare options and assess their consequences.

The product level also makes the difference between task completion and readiness for use visible. An executor may successfully implement a change inside a module, but moving it into the current product version must take account of integration checks, documentation, versioning, migrations, security, and recoverability. [CHLOYA][g-chloya] does not require an equally heavy procedure for every change, but does require an explicit definition of what [evidence][g-evidence] is needed for the level of risk involved.

### System or product platform

The system level covers several independently changeable products, applications, libraries, or services that jointly provide a user or internal process. Such a system may reside in one repository or many; the way code is stored does not itself define the [CHLOYA][g-chloya] level.

For example, the ArtGlyph Engine family may eventually include an engine, a studio, converters, experimental labs, and machine-learning components. Each product may have its own lifecycle, but a change to a shared scene format or rendering [contract][g-contract] can affect several of them. A successful change in one repository does not by itself mean a successful change to the platform.

This level requires memory above individual products. It should describe shared [contracts][g-contract], the dependency map, version-compatibility rules, the order in which changes propagate, and owners of cross-product decisions. An agent that changes a format in one component must not assume that other products will adapt automatically or that all consumers have already been found.

Research on socio-technical congruence draws attention to the fact that technical dependencies create a need for coordination among the people doing the work. Modular separation alone is insufficient if a change crosses responsibility boundaries and the needed communication does not occur [77]. For [CHLOYA][g-chloya], this means that semantic transfer of a change must follow the actual direction of consequences rather than directory or repository structure.

Coordination of technical and organizational links should not, however, be claimed as a quality guarantee. A large-scale study of 25 open-source projects found no statistical relationship between the authors’ measure of socio-technical congruence and either defect count or code churn [78]. The result limits overly strong conclusions: coordination is necessary for governed change, but does not itself demonstrate implementation correctness or replace testing, architectural assessment, or risk management.

At the system level, it is especially important to determine where the autonomy of an individual product owner ends. A local team or agent may choose the internal structure of its area, but a change to a shared protocol, data schema, security [policy][g-policy], or user process must be taken to a level that represents affected products. [CHLOYA][g-chloya] thus preserves local independence without turning it into a right to change system-wide obligations unilaterally.

### Organization

The organizational level appears when [CHLOYA][g-chloya]’s shared rules apply across several people, teams, repositories, environments, and data classes. Here the object of governance is not only software architecture, but also the distribution of roles, [authority][g-authority], responsibility, and decision channels.

An organization must determine who may formulate goals and change priorities; who may grant an executor access to data and tools; who approves a critical [contract][g-contract] change; and who decides on publication or deployment. It is equally important to establish which models and external services are allowed for different information categories, which actions require independent checking, and where memory required by several teams is stored.

This level is needed because one [AI executor][g-ai-executor] can technically cross boundaries that belong to different roles in a human organization. An agent can simultaneously analyze requirements, write code, run infrastructure commands, change documentation, and prepare public publication. Technical combination of these capabilities does not mean organizational [authority][g-authority] should be combined as well.

Melvin Conway’s work shows a relationship between an organization’s communication structure and the structure of the systems it designs [79]. For [CHLOYA][g-chloya], the relationship is two-way. Organizational boundaries affect architecture and [contracts][g-contract], while technical dependencies found by agents may in turn show that the existing distribution of responsibility no longer matches the real flow of changes.

*Team Topologies* treats team boundaries, modes of interaction, and management of cognitive load as means of organizing a sustainable flow of change [80]. [CHLOYA][g-chloya] applies similar reasoning to a mixed environment in which permanent human teams work alongside temporary [AI executors][g-ai-executor]. Agent [context][g-context] and [authority][g-authority] also create cognitive and coordination load, although part of that load shifts from the executor to the people who must prepare the task, check the result, and understand its system effects.

The organizational level does not mean centralizing every decision. Its purpose is to define explicitly which decisions belong to local owners and which must be raised because of the scale of their risk or consequences. If every change requires organization-wide approval, the methodology creates a bureaucratic bottleneck. If any executor may independently change a shared [policy][g-policy] or public [contract][g-contract], the organization loses governability. [CHLOYA][g-chloya] should support local autonomy inside established boundaries and controlled [escalation][g-escalation] when they are crossed.

### Applying several levels at once

[CHLOYA][g-chloya] levels are not isolated from one another. A single change passes through them according to its effects.

Suppose an executor changes a scene format in the ArtGlyph Engine. The immediate implementation is a local task. The scene format is a [context module][g-context-module] with its own memory and [contracts][g-contract]. A new format version affects the engine as a product. If the format is used by a studio, converters, and experimental tools, the change reaches the platform level. If publishing the specification can affect intellectual property or obligations to external parties, part of the decision moves to the organizational level.

It is not necessary to perform all work at the highest affected level. Implementation can remain local while only the [contract][g-contract] change and its implications are transferred to the platform level. An organizational decision may concern permission to publish rather than the structure of internal classes. Such separation avoids overloading every participant with the entire system [context][g-context] while still retaining consequences that exceed its [authority boundary][g-authority-boundary].

For every task, [CHLOYA][g-chloya] should make it possible to identify the primary execution level, the scope over which consequences propagate, and the level of final acceptance. Those three boundaries can coincide, but must not be assumed to coincide automatically.

### Expanding the scope of application

Moving between levels is not merely increasing the number of files, agents, or repositories. At the individual-task level, the correctness of a particular change must be demonstrated. At the [context][g-context]-module level, preserving local [contracts][g-contract] and memory is added. The product level requires consistency across several modules and readiness for release. The system level introduces cross-product dependencies and the propagation of changes across independent-area boundaries. The organizational level connects the technical process with roles, [policies][g-policy], [authority][g-authority], and responsibility.

[CHLOYA][g-chloya] should expand only where a narrower level no longer covers the real consequences of changes. The methodology does not require platform governance for an independent small application or an organizational committee for every local edit. It also does not allow a change to be treated as local merely because an executor physically edited one file.

Thus, a [CHLOYA][g-chloya] application level is defined by the broadest area in which a change creates obligations for other participants or parts of the system. The aim of this classification is not to make the process more complex, but to find the right governance boundary: broad enough not to lose consequences and local enough to retain clarity, speed, and responsibility.

## 2.3. What CHLOYA does not replace

[CHLOYA][g-chloya] is a specialized governance layer for AI-assisted development, not a universal replacement for existing software engineering. It defines how to give an [AI executor][g-ai-executor] a goal, [context][g-context], and [authority][g-authority]; how to preserve [project memory][g-project-memory]; how to substantiate a result; and how to decide whether it enters the project’s current state. It does not, however, assume every function needed to create, release, and operate a software product.

That limitation is fundamental. If [CHLOYA][g-chloya] were declared a replacement for product management, architecture, a secure lifecycle, version control, operations, or legal assessment, it would have to duplicate entire professional disciplines. Instead of a governed addition to an existing process, this would create a parallel system of documents, statuses, and approvals that raises complexity and creates a false impression of complete control.

### Product management and user work

[CHLOYA][g-chloya] helps preserve a human-formulated goal, relate it to tasks, and prevent an executor from silently substituting a technically convenient interpretation for the original intent. It does not independently determine which product should be built, which user problem should be solved, which feature matters more, or whether development cost is justified.

AI can help analyze feedback, prepare requirement options, find contradictions, or form a prototype. Choosing a target audience, validating a real need, defining a business model, prioritizing features, and accepting product risk nevertheless require interaction with users and a responsible human decision.

For example, an agent may competently implement a subscription system in an application. [CHLOYA][g-chloya] can help constrain the change scope, record payment requirements, and check the result. It cannot demonstrate that users are willing to pay, that the selected subscription model meets their expectations, or that the feature is more important than fixing other product problems.

Product research, interviews, usage analytics, experiments, and work with feedback therefore remain independent processes. Their conclusions can become [CHLOYA][g-chloya] inputs, but must not be generated and approved automatically by the same executor that has an interest in continuing implementation.

### Architectural design and engineering expertise

[CHLOYA][g-chloya] requires identifying area boundaries, dependencies, [contracts][g-contract], and the consequences of changes, but does not guarantee that the chosen architecture is correct. A formally detailed module passport does not repair an incorrect decomposition, and a large number of [contracts][g-contract] does not make an excessive system simpler.

An architectural decision depends on the domain, expected load, data lifecycle, security requirements, team capabilities, and maintenance cost. AI can propose alternatives and help assess their consequences, but final assessment requires professional knowledge of the project and an understanding of trade-offs that cannot always be expressed in one prompt.

It is particularly dangerous to regard [CHLOYA][g-chloya] as a replacement for specialized expertise in cryptography, authentication, payment processing, medical systems, personal data, critical infrastructure, and other high-cost-of-error domains. The methodology can require a competent specialist, retain that specialist’s decision, and prevent an agent from crossing set boundaries. It cannot create missing competence merely through a stricter task format.

[CHLOYA][g-chloya] therefore governs the process of making and executing architectural decisions; it does not assume the role of an architect or turn a model decision into a professional opinion.

### Secure software development lifecycle

[CHLOYA][g-chloya] does not replace Secure SDLC, vulnerability management, threat modeling, security assessment, incident management, or software supply-chain control.

NIST’s Secure Software Development Framework describes practices for preparing an organization, protecting software, producing well-secured releases, and responding to discovered vulnerabilities [13]. [SLSA][g-slsa], in turn, focuses on supply-chain integrity, artifact provenance, and protection of the build process [12]. Those concerns are broader than AI-executor governance and remain relevant whether code is written by people, agents, or a mixed team.

[CHLOYA][g-chloya] can fit into such a lifecycle. A change package can, for example, contain static-analysis results, dependency-provenance information, build data, secret-scanning results, and links to mandatory control procedures. An [authority][g-authority] [policy][g-policy] can prohibit an agent from publishing a package or modifying a protected pipeline on its own.

But a task package, handoff, or record of human approval does not prove that software is secure. If an organization does not model threats, track vulnerabilities, protect its build environment, or prepare to respond to incidents, [CHLOYA][g-chloya] cannot fill those gaps with its own artifacts.

[NIST AI RMF][g-nist-ai-rmf] further shows that AI risks must be considered in the [context][g-context] of goals, participants, environment of use, and organizational responsibility [25]. [CHLOYA][g-chloya] specifies part of that governance for agentic development, but does not replace a general AI risk-management system.

### Git, CI/CD, and engineering infrastructure

[CHLOYA][g-chloya] does not replace version control. Its concept of a current state is broader than a particular [Git][g-git] implementation, but a project still needs change history, version comparison, an identifiable base revision, and the ability to recover.

Nor does the methodology replace [CI/CD][g-ci-cd]. It can define which checks must be run and which results count as [evidence][g-evidence], but builds, tests, analyzers, deployment environments, and delivery mechanisms remain engineering infrastructure.

For example, [CHLOYA][g-chloya] can prohibit activation of a change until a migration, backup, and rollback plan have been successfully checked. It does not automatically create a reliable backup or demonstrate that recovery works. That requires configured operational tools and regular practical exercises.

Likewise, a green CI status must not automatically mean that a change is ready. Tests may not cover the semantic requirement, the build environment may differ from production, and deployment may require monitoring and a limited rollout. [CHLOYA][g-chloya] links such [evidence][g-evidence] to an activation decision; it does not replace monitoring, logging, configuration management, backups, or the work of an operations team.

### Incident management and operations

Development does not end once a change is applied. Even a properly checked release can meet unforeseen load, an external failure, changed data, or an integration error.

[CHLOYA][g-chloya] can retain information about a change’s contents, known risks, checks performed, and rollback method. That information can speed investigation because the next participant need not reconstruct the decision history from chats and scattered messages.

Responding to an incident, however, requires observability, accountable on-call staff, [escalation][g-escalation] channels, communication with users, service restoration, and subsequent root-cause analysis. Those functions remain part of operations and incident management. An agent log or change package is an information source for that process, not the process itself.

### Industry regulation, licensing, and legal assessment

[CHLOYA][g-chloya] can require data classification, mark limits on transfer to an external model, retain provenance of external code, and record the person who accepted a risk. It does not automatically determine which laws and contractual terms apply to a particular project.

Legal compliance depends on jurisdiction, data category, the organization’s role, [contract][g-contract] terms, industry, and the actual way in which the system is operated. The same technical decision may be allowed in an experimental local project and prohibited in a medical, banking, or government system.

Similarly, automatic checking of a license name does not replace analysis of its compatibility with a product’s distribution model, obligations to a customer, and other dependencies. AI can collect information and find a potential conflict, but a legally significant decision must be made by someone with the relevant [authority][g-authority] and competence.

A user statement such as “I take all responsibility” also does not remove third-party rights or organizational obligations. A person cannot authorize transfer of someone else’s personal data, trade secrets, or licensed code to an external service without holding that right.

### Professional and independent audit

[CHLOYA][g-chloya] improves verifiability: it retains the goal, change scope, [context][g-context] provenance, checks performed, residual risks, and activation decision. The presence of well-organized [evidence][g-evidence] does not, however, amount to an independent audit.

An executor that created a change may fail to notice its own mistaken premise. A second agent can repeat it if it uses the same model, [context][g-context], and test expectations. A person within the team may also have an interest in release or lack competence to check a specialized area.

Where independent audit is required by law, [contract][g-contract], industry practice, or a high cost of error, [CHLOYA][g-chloya] should provide an auditor with reproducible information, but must not declare an internal check equivalent to an external one. The methodology helps prepare the audit subject and remove some information losses; the conclusion remains with an independent, competent participant.

### Complementing the existing process

[CHLOYA][g-chloya] should use existing engineering and organizational mechanisms whenever possible rather than duplicating them. If requirements are maintained in an existing task-management system, the methodology can retain a link and the necessary verifiable summary. If architectural decisions are documented as ADRs, no second parallel log is necessary. If CI already produces signed reports and build-provenance information, a change package should link to them rather than copy the results manually.

[CHLOYA][g-chloya]-specific artifacts are justified where an existing process does not retain information specific to agent work: supplied [context][g-context], its provenance and trust level, the executor’s [authority][g-authority] scope, semantic transfer between temporary participants, unverified assumptions, and a separate decision to move a result into the project’s current state.

[CHLOYA][g-chloya] therefore does not create an alternative software engineering discipline. It connects existing disciplines around a new governance problem: temporary probabilistic executors that can independently read, plan, and affect project state.

> **[CHLOYA][g-chloya] does not replace professional processes, standards, or responsibility. It makes AI participation in those processes constrained, portable, and verifiable.**

## 2.4. When a lightweight mode is allowed and when it is prohibited

A lightweight [CHLOYA][g-chloya] mode is not an abandonment of governance. It is a proportionate reduction in formalization for tasks whose consequences are limited, verifiable, and reversible. Its purpose is neither to make a small local project reproduce the procedures of a large organization nor to turn every edit into a multi-stage approval process.

A small amount of code does not, however, mean low risk. A one-line command can delete working data, a one-parameter change can expose an external interface, and a small local script can send secrets or personal data to an external service. The mode is determined not by the number of files, lines of code, agents, or repositories, but by possible action consequences, the [authority][g-authority] available to the executor, and the quality of [evidence][g-evidence] that can be obtained before a result enters the current state.

In [lightweight mode][g-lightweight-mode], a brief task description may replace a full package; [project memory][g-project-memory] may be minimal; there may be one primary executor, fewer control transitions, and local checking rather than an independent audit. At a minimum, though, the work goal, authorized scope, readiness criterion, visibility of changes made, and accountable acceptance decision must remain. Without them, this is not lightweight [CHLOYA][g-chloya] but work without governed boundaries.

The mode must become stricter as the cost of error, scope of impact, sensitivity of information, irreversibility of action, difficulty of independent checking, and uncertainty about component provenance increase. This risk-dependent approach accords with the general logic of a secure development lifecycle and AI risk management [13], [25].

| Situation | Basis for mode selection | Permitted mode | Mandatory minimum |
|---|---|---|---|
| One-off local script using a replaceable copy of data and having a simple rollback | Effects are limited to a local environment; the result can be checked before use and the initial state is easy to restore | L0/L1: short task, one executor, local tests, and manual check | Explicit goal; limited directory or file set; preview of results; source-data copy; no production, secrets, or external-network access without a separate need |
| Small package or application entirely understandable to one competent person and one agent process | Architecture and dependencies are visible; one person can assess intent, main consequences, and [evidence][g-evidence] | One agent process, minimal [project memory][g-project-memory], no complex hierarchy of roles or modules | Brief project map; change rules; tests; record of material decisions; manual check before release |
| Secrets; personal, medical, or other protected data; authentication and cryptography | An error can cause disclosure, third-party rights violations, or a false sense of security; a technical rollback cannot undo a disclosure | [Lightweight mode][g-lightweight-mode] prohibited; conservative processing in an authorized environment and independent review | Data classification and minimization; check of the right to process and transfer; no secrets in prompts; approved model or provider; vetted libraries; competent review |
| Irreversible migrations, payments, production changes, critical infrastructure, and automatic deployment | An error can change live state, create financial or physical consequences, or affect many users | Separate planning from execution, separate confirmation of application, stronger [evidence package][g-evidence-package] | Dry run or copy-based check; restore point; demonstrated recovery procedure; limited first-application scope; observability; explicit production-step confirmation |
| Import of untrusted code, repository, or artifact | Code and documentation can contain malicious logic, [prompt injection][g-prompt-injection], installation scenarios, and instructions that must not gain execution [authority][g-authority] merely because an agent read them | Quarantine and separation of analysis from execution | Isolated environment; no secrets or working keys; no production access; recorded provenance; analysis of install, build, and hook scenarios; separate execution decision |
| New or recently released dependency | A component can be legitimate but lack sufficient operational history, review, and fixes; an update can enlarge the supply chain | By default, a waiting period of at least ten days and a review before inclusion; an urgent exception requires explicit risk acceptance | Pinned version and source; no floating versions; dependency and installation-scenario analysis; reputation and change review; isolated testing; deadline for reassessing an exception |
| New or substantially updated [MCP][g-mcp] server, plugin, skill, or external tool provider | A component can add instructions to the agent, read files and secrets, access the network, run commands, and change environment configuration. A standard protocol or harmless name does not establish safety [81], [82] | [Lightweight mode][g-lightweight-mode] prohibited until the particular version is checked and its [authority][g-authority] constrained | Verified provenance; pinned version; tool and permission inventory; isolated first run; no secret access by default; network limits; call log; immediate-disable capability |
| Public release of source code, package, documentation, article, issue, or PR containing disclosive details | Publication is practically irreversible: removed material may remain in forks, indexes, caches, and local copies | Separate publication/IP gate; an executor may not independently publish working material | Rights-holder check; search for secrets and internal information; licensing; assigned publication owner; organizational permission or established approval procedure |
| Change to a public API, file format, protocol, data schema, or another external [contract][g-contract] | A small [local change][g-local-change] can create obligations for an unknown number of consumers and cause incompatibility outside the repository | The maximum mode is not always necessary, but lightweight local acceptance is insufficient | Consumer search; backward-compatibility analysis; a version or migration path; [contract][g-contract] tests; semantic change transfer; separate activation decision |

### Reversibility and practical irreversibility

Mode selection must assess not only whether a rollback command exists, but whether the system can be returned to its previous factual state.

Technical [reversibility][g-reversibility] means that code, configuration, or data can be restored from a verified point. [Git][g-git] history alone does not prove that a database migration, external payment, or infrastructure change is reversible. A recovery plan must apply to the real environment rather than exist only as an assumption or untested scenario.

Practical irreversibility arises when local state can be restored but consequences have already left the controlled environment. A sent payment, published secret, personal data transferred to an external model, distributed message, or released public package cannot be undone by an ordinary `revert`. Read-only operations can therefore also require a strict mode: reading a `.env` file, SSH key, or medical document becomes dangerous if the information can be passed outside.

The right to read is consequently not automatically safe and must not be granted to an agent as universal [authority][g-authority]. Assessment considers data value, request provenance, the possibility of external transfer, and the tool’s ability to influence the executor’s later actions.

### Untrusted code and new dependencies

Untrusted provenance and insufficient maturity are different risks.

An untrusted repository or package can be created specifically to compromise an environment. Its source code, documentation, configuration files, and tests should be treated as data for analysis, not as instructions an agent may execute. Reading such material gives no [authority][g-authority] to run commands found there, connect suggested tools, change global configuration, or send the author information about the local system.

A new dependency may have no malicious purpose but may not yet have passed sufficient operational testing. [CHLOYA][g-chloya]’s ten-day waiting period reduces the probability of immediately importing an accidentally published, unstable, or quickly withdrawn version. It is not, however, a standalone defense against a targeted attack. A malicious package may exist longer than the period, use a compromised account of a known maintainer, or activate a payload after a delay.

The waiting period therefore supplements rather than replaces version pinning, provenance verification, analysis of installation and build scenarios, isolated execution, and limits on accessible secrets. These measures align with the supply-chain-integrity objectives considered by [SLSA][g-slsa] [12] and the secure-development practices of [NIST SSDF][g-nist-ssdf] [13].

### MCP servers and external agent tools

Connecting an [MCP][g-mcp] server must be treated as expanding the trusted computing boundary. A server can not only receive structured calls, but also offer the agent tool descriptions that become part of its working [context][g-context]. It can receive data selected by a model, initiate network interaction, and act with the [authority][g-authority] of the process in which it runs.

The `SANDWORM_MODE` campaign, first described in detail by Socket and later analyzed by CrowdStrike, demonstrated a practical combination of a supply-chain attack and compromise of AI development tools. Malicious npm packages stole [credentials][g-credentials], affected repositories and CI, installed a hidden [MCP][g-mcp] server, and registered it in the configurations of Claude Desktop, Cursor, VS Code, and Windsurf [81], [82].

The server disguised malicious capabilities as plausibly named tools for project indexing, code checking, and dependency analysis. Tool descriptions embedded instructions that encouraged an AI assistant to read SSH keys, cloud [credentials][g-credentials], npm tokens, `.env` files, and environment variables containing secrets, then transmit them through the tool interface [82].

CrowdStrike separately notes how difficult this attack class is to detect from behavior alone. Creating commits, opening pull requests, publishing packages, calling APIs, and working with configuration are normal actions of modern development and [CI/CD][g-ci-cd] tools. An attacker uses the same mechanisms and privileges as legitimate automation, so an outwardly correct action does not demonstrate that its origin or purpose is correct [81].

[CHLOYA][g-chloya] therefore cannot base trust in an [MCP][g-mcp] server on protocol compliance, provider name, claimed functions, or successful technical connection. Before [authority][g-authority] is granted, its provenance, exact version, actual file-system and network access, need for each permission, and ability to transfer data outward must be checked.

The first run takes place in an environment without working secrets, user data, or critical repositories. Permissions follow least privilege. Even a server described as read-only must not automatically gain access to the home directory, `.env`, SSH configuration, cloud-credential stores, or message history.

After checking, a particular version can move to a less strict mode if its [authority][g-authority] is technically limited, its behavior is observable, and updates are not applied automatically. A change of source, version, launch command, tool set, descriptions, system instructions, or required permissions cancels the prior assessment and requires a new review.

### Escalating the mode during execution

The mode assessment made before work begins is not final. An executor can discover circumstances absent from the original task: sensitive data, an unknown dependency, an external [contract][g-contract], an irreversible operation, a need for network access, an unexpected [MCP][g-mcp] server, or a move outside authorized scope.

Such a discovery must not be treated as an ordinary implementation detail. It changes task risk and cancels the previously granted permission to use [lightweight mode][g-lightweight-mode]. The executor must [pause][g-suspension] application of the result, retain the safely obtained information, and request a new [authority boundary][g-authority-boundary] or a decision from a competent owner.

Escalating the mode need not discard all work already performed. Analysis, a local patch, or tests may be preserved as a proposal. What is prohibited is automatically proceeding to the next action when the original risk assessment no longer fits it.

A strict mode also cannot compensate for the absence of a person who understands the consequences and may decide. If no such owner exists, adding another report or a second AI reviewer does not create the required competence. Work must stop and be taken to a level at which a substantive decision can be made.

Thus, [lightweight mode][g-lightweight-mode] is allowed not for “small tasks in general,” but for tasks whose consequences are genuinely limited, reversible, and verifiable. It shortens the procedure but does not remove the goal, boundaries, [evidence][g-evidence], or accountable acceptance of a result.

> **The smaller the project, the shorter [CHLOYA][g-chloya] can be. The higher the consequences of an error, the less the size of a change matters and the stricter the boundaries of its application must be.**

## 2.5. Conditions for pausing a task and escalating

Applying [CHLOYA][g-chloya] does not mean that every assigned task must necessarily be carried through to technical completion by an executor. Work can reveal contradictions, unknown dependencies, insufficient [authority][g-authority], or consequences not considered in the original framing. In such cases, continuing at any cost creates more risk than temporarily delaying the result.

[CHLOYA][g-chloya] establishes conditions under which a human or [AI executor][g-ai-executor] must [pause][g-suspension] a specific action, preserve the safely obtained result, and transfer the unresolved question to a participant with the necessary [authority][g-authority] or competence. Such a [pause][g-suspension] is a governance result provided for by the methodology, not a refusal to apply it.

> **[Pausing][g-suspension] a task does not mean stopping the application of [CHLOYA][g-chloya]. It prevents an insufficiently justified action from entering the project’s current state.**

The methodology does not itself stop a process, grant permission, or make decisions. Those actions are performed by people, [AI executors][g-ai-executor], and technical controls under the rules established for the project.

### Pausing, escalation, and stopping work

A [pause][g-suspension] means declining to perform a particular action until the discovered limitation is removed. It may apply not to the whole task but only to its risky or insufficiently justified part.

For example, an executor can continue compatibility analysis and prepare solution options, but cannot change a public API without agreement from the [contract][g-contract] owner. It can prepare a migration and tests, but cannot apply it to a working database. It can examine an external repository’s structure, but cannot run the scenarios it contains or connect tools it suggests.

[Escalation][g-escalation] means transferring an unresolved question to a participant who has the missing competence, decision right, or [authority][g-authority] to change task boundaries. It must not be reduced to a formal request to “confirm continuation.” The recipient needs to understand which constraint was found, which action is [paused][g-suspension], and which decision is required.

Work must be stopped completely if the task has lost its purpose, further execution would knowingly violate established constraints, a necessary competent owner is unavailable, or the [acceptable risk][g-acceptable-risk] level cannot be achieved with available means.

A [pause][g-suspension] must also be distinguished from a technical rollback. A rollback is a separate action with its own consequences and must not run automatically merely because an original operation ended in error. An untested rollback can increase harm, destroy data, or conceal information needed for investigation.

### Primary pause conditions

A task or individual action must be [paused][g-suspension] if the initial grounds for the work no longer match the actual situation.

| [Pause][g-suspension] condition | Executor’s immediate action | [Escalation][g-escalation] target | Condition for resumption |
|---|---|---|---|
| [Context][g-context] is contradictory, outdated, or lacks confirmed provenance | Do not choose the convenient version of requirements; record the conflict and its impact on the task | Task owner, product owner, or [canonical project-memory][g-project-memory] owner | An active source is identified and the decision is retained in [project memory][g-project-memory] |
| Continuing requires leaving authorized scope or obtaining new [authority][g-authority] | Do not perform a new kind of read, write, network call, publication, or change to another area | Owner of the relevant resource, module, data, or access [policy][g-policy] | Explicit, limited [authority][g-authority] with a clear scope is granted |
| No person is both competent and authorized to decide | Preserve analysis and options without applying the result | Manager, product owner, or domain specialist | A participant able to assess consequences substantively and decide is appointed |
| The action is irreversible or its consequences are unknown | Do not apply the result; preserve a safe initial state | Risk, data, or operational-environment owner | [Evidence][g-evidence], a limited application plan, recovery, and accountable approval are prepared |
| Provenance of code, dependency, command, model, or tool is unconfirmed | Isolate the component; do not execute its instructions or provide it working data | Dependency, agent-environment, or information-security owner | Source and version are confirmed; behavior and necessary [authority][g-authority] are checked |
| [Evidence][g-evidence] is insufficient or checks give contradictory results | Do not declare the task complete or activate the change | Requirements, testing, or relevant-risk owner | The discrepancy is resolved, or [residual risk][g-residual-risk] is explicitly described and accepted by an authorized participant |
| Secrets; personal, medical, or other protected data not anticipated by the task are discovered | Stop external transfer and excessive processing; do not copy sensitive values into reports | Data owner, security owner, or legal-compliance owner | Legal basis, authorized environment, and permitted processing scope are determined |
| Signs of compromise, malicious code, or [prompt injection][g-prompt-injection] are discovered | Do not continue normal execution or run the suspicious component again; preserve only minimally necessary information | Security or incident-response owner | The incident is assessed and the environment is declared safe, or a clean continuation environment is prepared |
| An [MCP][g-mcp] server, plugin, skill, or other tool provider unexpectedly appears or changes | Disable the new or changed component; do not grant it additional permissions | Agent-environment or information-security owner | The exact version, tool set, instructions, and [authority][g-authority] are checked again [81], [82] |
| Budget, time limit, or permitted iteration count is exceeded | Stop new generation cycles and preserve current state | Task or budget owner | Continuation is separately justified and approved |
| Work no longer serves the original goal | Do not expand the task around a discovered technical solution | Task or product owner | The goal is clarified or a separate task with its own boundaries is created |

The table lists typical conditions rather than an exhaustive set. An executor must [pause][g-suspension] an action in any other situation where it cannot reasonably substantiate that it has [authority][g-authority], that continuing is safe, or that the result serves the stated goal.

This approach is consistent with the general logic of [NIST AI RMF][g-nist-ai-rmf], which links risk management to the [context][g-context] of use, accountable participants, and continuing assessment of emerging consequences [25]. [NIST SSDF][g-nist-ssdf] practices likewise include not only creating secure software but also identifying vulnerabilities, responding to them, and adjusting the development process [13].

### A safe state after pausing

After a [pause][g-suspension], a task must not leave the system in an unclear or knowingly unsafe state. The executor must stop further impact, preserve information needed to understand the situation, and avoid additional irreversible actions without a separate basis.

If a potentially dangerous operation has not started, the safe result is to preserve the current state without starting it. If an operation was partly performed, the reached state must be recorded and the recovery decision transferred to a competent owner.

Automatic rollback is allowed only when it was planned in advance, tested for the relevant environment, and does not destroy data needed for analysis. In all other cases, rollback must be treated as a new intervention requiring its own assessment.

When possible compromise is discovered, a suspicious package or tool must not be run again merely to confirm an observation. Full secrets, personal data, or contents of private files must not be placed in an [escalation package][g-escalation-package] either. It is enough to state the kind of information discovered, where it was found, and the nature of the possible impact.

### Preserving an interim result

[Pausing][g-suspension] a dangerous action does not require discarding all work performed. Safe results can be retained as a proposal that has not entered the current state of the project.

Such results can include analysis, a solution design, a local patch, tests, a migration scheme, a list of discovered dependencies, compatibility options, or a description of missing [evidence][g-evidence]. They must be clearly marked as unverified, incomplete, or awaiting a decision.

An executor must not present an interim result as complete merely because it cannot continue. Its status must state the real situation: what was done, what was not checked, what action was not performed, and why another participant’s decision is required to continue.

### Escalation package

[Escalation][g-escalation] must not consist of passing the entire dialogue history or an unstructured set of logs. The next participant needs a compact package that enables a decision without repeating all work already done.

An [escalation package][g-escalation-package] must explain the original goal, safely completed part, discovered [pause][g-suspension] condition, action not performed, possible consequences of continuation, and the specific decision or [authority][g-authority] the executor needs.

If several options are acceptable, the executor may present them with their known advantages, risks, and constraints. It must not substitute the owner’s decision with the option most convenient for continuing its own work.

The package should contain only information necessary for the decision. Secrets, personal data, private source text, and other sensitive material must not be copied into it without a separate need and permission.

### No bypassing a pause condition

A discovered [pause][g-suspension] condition applies to the entire related execution chain. Passing a task to another agent, changing the model, restarting, splitting an operation, or changing the wording of a request does not remove the constraint.

A [pause][g-suspension] must not be bypassed by assigning the dangerous part to an executor that was not informed of the risk. A delegated executor must receive the [pause][g-suspension] condition along with the rest of its [context][g-context].

Another model may be queried for independent analysis, but this creates no new [authority][g-authority] and does not turn a lack of [evidence][g-evidence] into [evidence][g-evidence]. Agreement among several models also does not replace checking if they relied on the same mistaken [context][g-context] or the same incomplete data.

Risk must not be formally reduced by splitting work. A sequence of small actions that jointly leads to publication, a production change, or transfer of protected data is assessed by its combined result.

Silence from an owner does not count as permission unless the opposite was set in advance for a particular class of low-risk tasks. Expiry of a waiting period does not automatically remove a prohibition either.

### Conditions for resuming work

Work can resume only after the specific cause of a [pause][g-suspension] has been removed. An ordinary answer of “continue” is insufficient if it does not define the new boundaries, grounds, and responsibility.

If the problem was contradictory [context][g-context], an active source of requirements must be named. If [authority][g-authority] needed to be expanded, the specific permitted actions and resources must be recorded. If [residual risk][g-residual-risk] was accepted, its content, decision owner, and limits of acceptance must be stated.

If an external component was checked, permission must apply to a specific version, source, and configuration. An abstract statement that “this package can be trusted” must not automatically extend to later updates, new maintainers, or a changed dependency set.

On resumption, the executor rechecks the goal, current [context][g-context], [authority][g-authority] scope, and readiness criteria. Work continues from a new control point, and the decision that removed the constraint is added to [project memory][g-project-memory] or the task package.

If the reason for a [pause][g-suspension] cannot be removed, the task remains [paused][g-suspension] or is stopped. Costs already incurred, a ready patch, or proximity to a planned release are not sufficient reasons to accept uncontrolled risk.

### Human direction and the boundaries of risk acceptance

A human can change a goal, expand authorized scope, accept residual product risk, or stop a task. The existence of human direction does not mean that every participant may override every constraint.

A task owner is not always the owner of data, a production environment, corporate code, or the right to publish publicly. That person cannot authorize transfer of others’ personal data, disclosure of trade secrets, license violation, or bypass of a mandatory [policy][g-policy] unless such [authority][g-authority] has been granted.

The phrase “the user accepts all responsibility” should be retained as a statement by a particular participant, not treated as a universal release from third-party rights, contractual obligations, and established organizational constraints.

If a human direction conflicts with an active [policy][g-policy] or exceeds the person’s [authority][g-authority], the executor must preserve the conflict and refer it to the owner of the relevant area instead of selecting the most convenient command source.

### Pausing as a sign of governability

The requirement to [pause][g-suspension] must not encourage executors to conceal uncertainty in pursuit of formal task completion. A process in which every request must end in an applied change inevitably rewards unsupported assumptions, boundary bypasses, and concealment of [residual risk][g-residual-risk].

A good result can be not only working code, but also a demonstrated absence of a safe basis for proceeding. That result protects the project from a more expensive error and gives an owner enough information to make an informed decision.

> **A good executor is not required to complete every task. It is required to recognize the boundary of its grounds for action and not turn a lack of [context][g-context], [authority][g-authority], or [evidence][g-evidence] into an irreversible act.**

[g-acceptable-risk]: ../../research/GLOSSARY.en.md#acceptable-risk
[g-ai-executor]: ../../research/GLOSSARY.en.md#ai-executor
[g-authority]: ../../research/GLOSSARY.en.md#authority
[g-authority-boundary]: ../../research/GLOSSARY.en.md#authority-boundary
[g-chloya]: ../../research/GLOSSARY.en.md#chloya
[g-ci-cd]: ../../research/GLOSSARY.en.md#ci-cd
[g-context]: ../../research/GLOSSARY.en.md#context
[g-context-engineering]: ../../research/GLOSSARY.en.md#context-engineering
[g-context-module]: ../../research/GLOSSARY.en.md#context-module
[g-contract]: ../../research/GLOSSARY.en.md#contract
[g-credentials]: ../../research/GLOSSARY.en.md#credentials
[g-current-project-state]: ../../research/GLOSSARY.en.md#current-project-state
[g-data-is-not-instruction]: ../../research/GLOSSARY.en.md#data-is-not-instruction
[g-devops]: ../../research/GLOSSARY.en.md#devops
[g-effective-irreversibility]: ../../research/GLOSSARY.en.md#effective-irreversibility
[g-escalation]: ../../research/GLOSSARY.en.md#escalation
[g-escalation-package]: ../../research/GLOSSARY.en.md#escalation-package
[g-evidence]: ../../research/GLOSSARY.en.md#evidence
[g-evidence-package]: ../../research/GLOSSARY.en.md#evidence-package
[g-git]: ../../research/GLOSSARY.en.md#git
[g-governance-gap]: ../../research/GLOSSARY.en.md#governance-gap
[g-level-of-chloya-application]: ../../research/GLOSSARY.en.md#level-of-chloya-application
[g-lightweight-mode]: ../../research/GLOSSARY.en.md#lightweight-mode
[g-local-change]: ../../research/GLOSSARY.en.md#local-change
[g-mcp]: ../../research/GLOSSARY.en.md#mcp
[g-nist-ai-rmf]: ../../research/GLOSSARY.en.md#nist-ai-rmf
[g-nist-ssdf]: ../../research/GLOSSARY.en.md#nist-ssdf
[g-policy]: ../../research/GLOSSARY.en.md#policy
[g-portable-core]: ../../research/GLOSSARY.en.md#portable-core
[g-project-memory]: ../../research/GLOSSARY.en.md#project-memory
[g-prompt-injection]: ../../research/GLOSSARY.en.md#prompt-injection
[g-proposed-action]: ../../research/GLOSSARY.en.md#proposed-action
[g-residual-risk]: ../../research/GLOSSARY.en.md#residual-risk
[g-reversibility]: ../../research/GLOSSARY.en.md#reversibility
[g-safe-state-after-suspension]: ../../research/GLOSSARY.en.md#safe-state-after-suspension
[g-semantic-change-handoff]: ../../research/GLOSSARY.en.md#semantic-change-handoff
[g-slsa]: ../../research/GLOSSARY.en.md#slsa
[g-stopping-condition]: ../../research/GLOSSARY.en.md#stopping-condition
[g-suspension]: ../../research/GLOSSARY.en.md#suspension
[g-verifiable-readiness]: ../../research/GLOSSARY.en.md#verifiable-readiness
