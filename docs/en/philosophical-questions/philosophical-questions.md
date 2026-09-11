# Philosophical Questions and Open Tensions

> **Version:** `0.3.1`  
> **Status:** in development

CHLOYA is being developed at a time when AI capabilities are changing faster than professional roles, organizational structures, and ideas about the limits of automating intellectual work can stabilize. Many of the methodology's practical decisions therefore rest on questions for which no final answer can yet be offered.

This section does not establish normative CHLOYA requirements and does not attempt to predict the future structure of software development or organizations. It records the tensions that arise as AI ceases to be merely a tool for preparing text or isolated code fragments and gains the ability to research, plan, implement, verify, and coordinate substantial bodies of work.

Some of these questions have empirical foundations. AI-assisted development productivity, human oversight, [delegation][g-delegation], multi-agent interaction, preservation of project knowledge, and the organizational consequences of agent systems are already being studied. Yet the existence of research does not remove the uncertainty. Some findings apply only to particular classes of tasks; others still exist as preliminary publications or isolated practical observations. CHLOYA itself also treats many of the propositions below as hypotheses that must be refined as practical experience accumulates.

The philosophical questions are deliberately placed before the main contents. The chapters that follow offer partial engineering answers: [context][g-context] management, constrained [authority][g-authority], preservation of [project memory][g-project-memory], outcome verification, [risk-adaptive autonomy][g-risk-adaptive-autonomy], human-readable code, and role allocation. An engineering solution, however, does not necessarily settle the broader question that gave rise to it.

## Contents

- [Open Status of the Questions](#open-status-of-the-questions)
- [PQ-01. Why Is a Developer Needed If AI Can Write Code?](#pq-01-why-is-a-developer-needed-if-ai-can-write-code)
- [PQ-02. Does a Person Equipped with Agents Still Need a Team?](#pq-02-does-a-person-equipped-with-agents-still-need-a-team)
- [PQ-03. Are Functional Departments Needed If Agents Can Perform Their Work?](#pq-03-are-functional-departments-needed-if-agents-can-perform-their-work)
- [PQ-04. What Becomes Scarce When Intellectual Production Becomes Cheap?](#pq-04-what-becomes-scarce-when-intellectual-production-becomes-cheap)
- [PQ-05. What Happens When Creating Becomes Cheaper Than Understanding?](#pq-05-what-happens-when-creating-becomes-cheaper-than-understanding)
- [PQ-06. Must Humans Understand What They No Longer Have to Be Able to Create?](#pq-06-must-humans-understand-what-they-no-longer-have-to-be-able-to-create)
- [PQ-07. Does Automation Destroy the Competence Needed to Oversee It?](#pq-07-does-automation-destroy-the-competence-needed-to-oversee-it)
- [PQ-08. When Does Human Oversight Become a Fiction?](#pq-08-when-does-human-oversight-become-a-fiction)
- [PQ-09. What Does It Actually Mean to “Trust AI”?](#pq-09-what-does-it-actually-mean-to-trust-ai)
- [PQ-10. Can AI Verify AI?](#pq-10-can-ai-verify-ai)
- [PQ-11. Who Is Responsible for a Decision That AI Effectively Shaped?](#pq-11-who-is-responsible-for-a-decision-that-ai-effectively-shaped)
- [PQ-12. Why Does Another Person Sometimes Understand an Unfinished Thought Faster Than AI?](#pq-12-why-does-another-person-sometimes-understand-an-unfinished-thought-faster-than-ai)
- [PQ-13. Must Code Remain a Human Language If Machines Become Its Main Authors and Readers?](#pq-13-must-code-remain-a-human-language-if-machines-become-its-main-authors-and-readers)
- [PQ-14. What Will Remain for Humans After Execution Is Automated?](#pq-14-what-will-remain-for-humans-after-execution-is-automated)
- [PQ-15. When Does AI Begin to Finance Its Own Continued Use?](#pq-15-when-does-ai-begin-to-finance-its-own-continued-use)

## Open Status of the Questions

The questions listed here should not be treated as introductory theses that the subsequent chapters are required to prove. Their purpose is different: they delineate the area of uncertainty within which CHLOYA is developing.

Some already have partial practical answers. [Risk-adaptive autonomy][g-risk-adaptive-autonomy] addresses the problem of [meaningful human control][g-meaningful-human-control]; [context][g-context] management addresses the need to transfer to machines some knowledge that was previously informal; portable [project memory][g-project-memory] addresses dependence on particular people and models; [evidence][g-evidence] addresses the asymmetry between generation and verification; and human-readable code addresses the preservation of human understanding.

Each such mechanism, however, is only a current way of working with a broader tension. The ability to organize verification does not finally answer the question of the future of human competence. Contextual memory does not prove that all tacit knowledge can be formalized. Gradations of [authority][g-authority] do not solve the philosophical problem of responsibility. An agent-based organization does not reveal the optimal number of people.

This section should therefore remain alive. New questions may appear as the methodology develops, while existing ones may be refined, combined, or converted from open questions into testable hypotheses. If enough empirical evidence accumulates for any of them, it may receive a more definite answer in the main body of CHLOYA. Until then, the absence of a final answer is not a gap in the document but an honest reflection of the state of the field.

## PQ-01. Why Is a Developer Needed If AI Can Write Code?

Software development has historically been closely tied to the ability to create code directly. As AI advances, that connection is weakening. Modern agent systems can inspect repositories, modify many files, run tools and tests, fix errors, and carry out long-running tasks, while experimental projects demonstrate the possibility of creating large software artifacts with a substantial amount of machine execution [40]–[46].

The ability to write code, however, is not the same as the ability to lead development. A real project contains not only source text but also accumulated decisions, implicit requirements, environmental constraints, trade-offs, dependencies, a history of errors, and knowledge of why the system is designed as it is. METR explicitly distinguishes well-specified, self-contained tasks with clear success criteria from everyday work that depends on a broader [context][g-context] [46]. SWE-bench likewise shows that real tasks require reconstructing relationships among multiple parts of an existing system, not merely generating an isolated fragment [70].

Even the productivity question does not yet admit a universal answer. Peng et al. found a speedup in a constrained programming task [15], whereas Becker et al. found a different effect for experienced developers working on open-source projects familiar to them [16]. These findings caution against moving directly from “AI can write code” to “developers are no longer needed.”

The more substantive question is therefore: **what combination of functions must be transferred to AI before the developer's role truly becomes redundant?** If a person stops writing most of the code but continues to define the problem, choose the architecture, recognize false premises, evaluate the outcome, and accept the consequences of decisions, has the developer disappeared—or has the substance of the profession changed?

The next level of this question also remains open. If task definition, design, risk analysis, and verification are progressively automated as well, is there a stable human remainder to the profession, or will the boundary between human and machine work continue to move?

## PQ-02. Does a Person Equipped with Agents Still Need a Team?

Agent systems change not only the productivity of an individual developer but also the possible scale of that person's activity. One person gains the ability to investigate alternatives in parallel, write code, prepare tests and documentation, analyze failures, and perform other tasks that previously required several specialists.

At first glance, this points toward ever-smaller teams. Yet the amount of work performed is only one function of a team. Other people provide independent perspectives, share attention and responsibility, retain different portions of informal knowledge, notice one another's mistakes, and can jointly make sense of a problem that has not yet been fully articulated.

Coordination itself also has a cost. Every additional participant—human or machine—requires [context][g-context] transfer, synchronization, integration of results, and conflict resolution. Consequently, neither adding people nor adding agents is by itself a sign of a more mature organization. CHLOYA's accumulated concepts already address this problem through coordination cost and the [principle of the minimum necessary number of agents][g-minimum-agent-count].

Classic work on socio-technical congruence, Conway's law, and team organization shows that the structure of technical dependencies and the structure of human interaction are related [77]–[80]. This work predates modern agent systems and does not answer the question of mixed human–AI teams, but it gives reason to doubt that organizational structure becomes irrelevant merely because execution can be automated.

AI may not eliminate the team but instead change its minimum effective size. One person with a system of agents may indeed replace a substantial portion of an earlier structure. The reverse may also be true: several people, each amplified by their own agents, may be able to address problems on a scale previously beyond the reach of an entire organization.

The question is therefore not only **how many people can be replaced**, but also **what minimum human structure must sit above an advanced agent system to preserve the quality of thought, independent verification, and resilience of the work**.

## PQ-03. Are Functional Departments Needed If Agents Can Perform Their Work?

The same tension extends beyond software development. Market research, publication preparation, audience analysis, documentation, user support, analytics, parts of project management, and many other functions can already be performed partly by AI. Current literature on agent systems separately considers functional- and organizational-level agents capable of operating in support, finance, human resources, compliance, and marketing [339].

The disappearance of particular operations does not yet mean the disappearance of the function. A marketing department is not merely a group of people who write copy. It accumulates knowledge of its audience, chooses objectives, reconciles conflicting signals, interacts with other units, and bears organizational responsibility for decisions. Development, analytics, and support likewise represent more than a set of produced artifacts.

An additional tension arises because human departments also use AI. The real comparison is therefore shifting from **“human or AI”** toward different organizational configurations: one person with agents, a small team with personal agents, a traditional department with AI tools, or a predominantly agent-based function with a human [governance plane][g-governance-plane].

If the same models are available to all these structures, the source of advantage must be sought in more than the ability to produce text, code, or analysis. It may instead lie in the quality of goal-setting, access to domain knowledge, independence of viewpoints, speed of decision-making, relationships with other people, allocation of responsibility, and the ability to notice errors in the problem formulation itself.

The broader question therefore remains open: **which organizational functions require a durable human structure, and which can genuinely be transferred to a person managing a collection of agents?**

## PQ-04. What Becomes Scarce When Intellectual Production Becomes Cheap?

Much of traditional engineering organization arose under conditions in which producing an outcome was expensive. Writing a program, preparing an analytical review or documentation, and developing several architectural alternatives required substantial human time. The ability to generate such outputs quickly changes the distribution of cost.

The disappearance of one scarcity does not mean the disappearance of scarcity altogether. If dozens of alternatives can be generated in minutes, the constraint becomes the ability to choose among them. If thousands of lines of code are created almost instantly, the constraint becomes the ability to understand and verify them. If research can be expanded rapidly, attention needed to distinguish the essential from the secondary becomes scarce.

CHLOYA previously formulated this observation as a **[scarcity shift][g-scarcity-shift]** and a **[bottleneck shift][g-bottleneck-shift]**: as production becomes cheaper, scarcity may move into problem definition, architectural understanding, [context][g-context], verification, integration, responsibility, and preservation of competence. For now, this should be treated as a working CHLOYA hypothesis rather than an established universal law.

Practical and research observations give reason to take the hypothesis seriously. Different studies do not show the same productivity gain from the use of AI [15], [16], and maintainers of open-source projects have already described cases in which cheap generation of low-quality messages transfers substantial cost to the people required to review them [75].

If the production of intellectual artifacts becomes virtually unlimited, a philosophical question follows: **what then determines their value?** Creation alone ceases to be sufficient. The principal scarcity may no longer be the ability to produce an answer, but the ability to ask the right question, select a direction worth implementing, and demonstrate that the resulting outcome is actually needed.

## PQ-05. What Happens When Creating Becomes Cheaper Than Understanding?

Cheaper generation creates an even sharper asymmetry. In a short time, AI can produce a volume of program code, documentation, alternatives, or analytical conclusions that a human physically cannot examine carefully in the same period.

CHLOYA's working concepts describe this problem as **verification asymmetry**:

`cost of creation << cost of understanding + cost of verification`

An important constraint follows: faster production does not necessarily make the system as a whole faster. If the queue of unverified results grows more quickly than the capacity to understand them, additional generation begins to increase rather than reduce unfinished work. Verification backpressure emerges: at some point, the rate of creation must be constrained by verification throughput.

This changes the meaning of productivity itself. A system that creates one hundred changes per hour is not necessarily more productive than one that creates ten if a person can responsibly accept only five. A more capable agent, or a larger number of agents, may merely move the bottleneck toward the human more quickly.

This leads to a question extending far beyond programming: **what happens to intellectual activity when an outcome can be produced faster than the responsible subject can understand it?** The main limiting factor of future agent systems may prove to be neither computing power nor generation quality, but the finite throughput of human attention and meaningful decision-making.

## PQ-06. Must Humans Understand What They No Longer Have to Be Able to Create?

If AI can implement a complex component on its own, must the person responsible for it be capable of writing the same component without AI? Requiring complete manual reproduction would quickly make much of automation pointless. Yet the opposite extreme—owning a system whose workings the person does not actually understand—also creates a problem.

CHLOYA's working concepts use the idea of **operational understanding** for this boundary. A person does not have to remember every line. The owner of an area must, however, retain sufficient understanding of why it exists, where its boundaries lie, which invariants apply, what it depends on, how it can fail, how a change can be verified, and how the system can be returned to a safe state.

This distinction matters because a plausible outcome does not by itself guarantee correctness. In the study by Perry et al., participants using an AI assistant not only produced less secure code in the tasks examined but were also more likely to judge their own output as secure; a more cautious attitude toward model suggestions and active verification were associated with better results [74].

Even the notion of operational understanding does not settle the question. Where is the boundary between a person who truly owns a system and one who merely knows enough terminology to describe its behavior? How deeply must the internals be understood when good specifications, tests, observability, and AI-assisted detailed analysis are available?

AI development may progressively separate the ability to **create** from the ability to **understand and control** much more sharply than was previously possible. If so, a central professional competence will no longer be the manual reproduction of every operation but the ability to maintain a sufficient model of the system for meaningful decision-making.

## PQ-07. Does Automation Destroy the Competence Needed to Oversee It?

The preceding question has a temporal dimension. Even if an experienced specialist can verify an agent's work today, where will the next experienced specialist come from if much of the activity through which that competence was previously formed is automated?

This creates the **[verification competence paradox][g-verification-competence-paradox]**: the more low-level work is delegated to AI, the fewer natural opportunities people receive to acquire the skills needed to recognize errors in that work. CHLOYA's working concepts already identify this problem.

It is not solely an internal hypothesis of the methodology. In *Building Applications with AI Agents*, Michael Albada explicitly identifies skill degradation as a vulnerability of human oversight in agent systems: as routine operations are handed to agents, it may become harder for a person to intervene effectively in critical situations. The same discussion identifies [automation bias][g-automation-bias] and [alert fatigue][g-alert-fatigue] [339].

The problem may be especially visible in professions with long learning trajectories. If a junior engineer no longer performs the work that once enabled the formation of internal models of typical failures, productivity gains today may create a competence shortage tomorrow.

This does not necessarily mean that manual labor must be preserved artificially. Training may instead have to separate from production execution: simulators, post-incident analyses, independent exercises, controlled periods without AI, and other forms of deliberate practice may replace some of the experience that was previously acquired automatically.

The question remains open: **can society sustainably delegate the execution of intellectual work without losing the human ability to understand and verify that work when automation fails?**

## PQ-08. When Does Human Oversight Become a Fiction?

Keeping a human in the loop is often treated as a universal safety measure. The mere presence of a person, however, does not amount to [meaningful control][g-meaningful-human-control].

If an agent performs thousands of actions while an operator receives hundreds of confirmation requests, human attention becomes the constraining resource. Confirmation gradually changes from a decision into a ritual. The person becomes accustomed to accepting the system's recommendation, particularly when the overwhelming majority of previous requests were safe.

This problem is directly grounded in the literature. Work on human oversight of agent systems considers the need to scale human participation according to risk [18], [19]. Albada's applied analysis specifically names [automation bias][g-automation-bias] and [alert fatigue][g-alert-fatigue]: an excessive number of low-priority signals can reduce the likelihood that an operator will pay close attention to the critical case [339].

CHLOYA's question therefore cannot be reduced to the presence of a “Confirm” button. [Meaningful control][g-meaningful-human-control] requires that a person have time, competence, the necessary [context][g-context], and a genuine ability to alter the decision. If even one of these conditions is absent, a formal approval point may create only the appearance of responsibility.

A harder formulation follows: **what volume of decisions can one person genuinely oversee, and at what point does further growth in the number of agents turn human governance into a fiction?** The limit probably depends on risk, task repeatability, the quality of automated evidence, and the degree of independence of the control mechanisms themselves.

## PQ-09. What Does It Actually Mean to “Trust AI”?

In everyday speech, trust is often attributed to a model as a whole: one model is “trusted,” while another is considered unreliable. For an agent system, this framing is too coarse.

A model may perform extremely well on one class of tasks and fail on another. The same answer may be acceptable as a hypothesis and unacceptable as the basis for an irreversible action. The ability to read data does not imply the right to change a system, and a high average test score does not prove the correctness of a particular decision.

Research on governance and [delegation][g-delegation] already relates autonomy not only to the ability to perform a task but also to [authority][g-authority], responsibility, risk, and control mechanisms [19], [20]. The NIST AI RMF likewise treats trustworthiness not as a simple property of a model but through a set of managed characteristics and risks [25]. CHLOYA therefore ties the degree of autonomy to a particular transition and its possible consequences, not to generalized trust in a vendor or model.

Perhaps an engineering system should not trust “AI” as a unitary subject at all, but rather **a particular capability within a particular domain, under specified constraints and with available evidence**. Trust then becomes a property of the relationship among the executor, task, [context][g-context], [authority][g-authority], and method of verification.

This creates the inverse problem. If every AI result must be completely reproduced and independently verified by a person, the economic value of [delegation][g-delegation] disappears. The boundary beyond which accumulated evidence and constraints are sufficient to stop manually rechecking every action therefore remains an open question.

## PQ-10. Can AI Verify AI?

The natural response to limited human verification capacity is to transfer part of the control function to other models and agents. One executor writes code, another reviews it, a third analyzes security, and a fourth evaluates tests. Such a structure can substantially expand verification throughput.

The number of reviewers, however, does not guarantee the independence of their review. Models may share similar training data, architectural properties, reasoning patterns, and characteristic errors. Several agents may independently reach the same false conclusion or, conversely, create the appearance of consensus by successively relying on one another.

The study by Cemri et al. shows that multi-agent systems have their own classes of specification, interaction, and verification failures [21]. An earlier CHLOYA version had already recorded as an open research question when another agent or model genuinely constitutes an independent verifier. The methodology's broader evidence base also connects [21] with the need for formalized handoffs and independent verification.

Independence may therefore be determined not by the number of models but by differences in the **grounds for verification**. An executable test, a formal schema, a static analyzer, observation of real behavior, or an independent data source can sometimes provide stronger confirmation than one more concurring piece of linguistic reasoning.

The open question can be stated as follows: **can a quantity of machine checks substitute for independence of evidence, and what should count as an independent verifier in a system where related models perform a substantial part of the analysis?**

## PQ-11. Who Is Responsible for a Decision That AI Effectively Shaped?

Traditionally, it is usually possible to distinguish the author of a proposal from the person who accepted the decision. In an agent system, that boundary becomes less clear.

Suppose a person identifies a problem. One agent gathers information, a second develops options, a third compares them, a fourth proposes an architecture, a fifth implements it, and another verifies the result. The person receives a final summary and approves the proposed option. Formally, the final act remains human, but much of the intellectual construction of the decision arose before it.

Tomašev et al.'s work on intelligent delegation treats [delegation][g-delegation] as broader than task transfer and includes questions of [authority][g-authority], trust, responsibility, and control [20]. This matters precisely because the capability to perform work and the right to accept its consequences are different categories.

Such a system must distinguish at least authorship, decision rights, accountability, and the ability to understand consequences. These may belong to different participants in the process. A person may bear legal or organizational responsibility for a decision whose intellectual structure was largely proposed by a machine. Conversely, a substantial AI contribution to a decision does not by itself create organizational responsibility for the AI.

The resulting question is: **does responsibility follow from authorship of the decision, the [authority][g-authority] to approve it, the ability to understand its consequences, or the acceptance of risk on behalf of others?** Practical systems must still designate an accountable subject, but that is an organizational necessity, not a final philosophical answer.

## PQ-12. Why Does Another Person Sometimes Understand an Unfinished Thought Faster Than AI?

The ability of one person to manage many agents creates a strong argument for small teams. Real collaboration, however, has a property poorly captured by the number of completed tasks: people can often understand one another before a complete formal description of the problem exists.

A colleague who has worked on the same project for a long time may recognize the meaning of a short remark, an intonation, a gesture toward the screen, or the phrase “something is wrong here.” Behind it lie shared history, professional experience, earlier disagreements, familiarity with the product, and many assumptions that no one explicitly enumerates.

For AI, much of this environment must be made explicit. Modern approaches to codified [context][g-context] and [project memory][g-project-memory] seek to represent externally the knowledge that would otherwise remain inside a person or an individual session [22], [23]. CHLOYA likewise builds managed [context][g-context] and portable memory precisely because the project's essential meaning cannot be reconstructed from scratch every time.

Successful externalization of [context][g-context], however, does not prove that all tacit shared understanding can be converted into documents without loss. Moreover, describing a thought for AI is itself work. A person may perform the assigned task more slowly than a machine yet understand a still-unformulated problem faster than it can be turned into a good prompt.

This advantage should not be assumed permanent either. Long-term memory, observation of the work process, multimodal interfaces, and a more persistent shared [context][g-context] may gradually narrow the gap.

The open question is therefore: **how much of the value of a human team lies not in execution, but in the ability to understand together what has not yet been fully expressed?**

## PQ-13. Must Code Remain a Human Language If Machines Become Its Main Authors and Readers?

CHLOYA assumes that a project must remain accessible to people and that code must express intent clearly enough to be understood, verified, and continued without mandatory dependence on a particular model. In the main body of the methodology, this is a practical principle.

A deeper question precedes it.

Modern programming languages, naming conventions, architectural patterns, and much of the documentation were formed in a world where people were the principal writers and maintainers of code. If machines create and read the overwhelming majority of future changes, human readability will no longer be an obviously optimal criterion.

Machine executors may find it easier to work with a representation that people perceive less readily. A choice then arises: require the machine system to preserve a human form of code, or move human oversight to another level—specifications, contracts, tests, behavioral models, [evidence][g-evidence], and the observable state of the system.

This question directly precedes the chapter “Code as a Shared Language for Humans and AI.” That chapter presents **CHLOYA's position for the current technological stage**, not [evidence][g-evidence] that code will forever remain the primary shared representation.

The open question is broader: **which artifact must remain understandable to a person in a system whose internal structure is substantially created by machines?** It may always be source code. Over time, it may instead become a higher layer of formalized intent.

## PQ-14. What Will Remain for Humans After Execution Is Automated?

Many of the preceding questions admit a provisional answer: goals, values, trade-off choices, responsibility, risk acceptance, creativity, semantic judgment, and the decision about what is worth doing will remain with humans.

That is the normative position CHLOYA takes today. Humans set direction and acceptable risk, approve consequential decisions, and accept outcomes, while AI is treated as a temporary and replaceable executor.

It does not follow, however, that the listed functions are fundamentally beyond automation. The methodology makes a governance choice about **where human responsibility should reside now**; it does not assert the existence of a proven intellectual boundary that AI can never cross.

If models become better at formulating goals, recognizing tensions, comparing values, and proposing decisions under uncertainty, the human role may change again. The former boundary between execution and governance would then prove temporary.

The final question of this section may therefore be the most general:

> **Is there a fundamental boundary to the automation of intellectual activity, or are we observing only a continual movement of the boundary between what people do themselves and what they are prepared to transfer to machines?**

CHLOYA does not need an answer to this question to be practically useful. The methodology addresses the present reality, in which AI capabilities are expanding but goals, [authority][g-authority], risk, [evidence][g-evidence], and responsibility still require explicit organization. If that reality changes, the methodology itself must change with it.

## PQ-15. When Does AI Begin to Finance Its Own Continued Use?

In the early stages of developing a commercial product, AI acts primarily as a consumer of resources. A person pays for access to models, agent systems, computing capacity, and other tools in order to obtain an outcome that does not yet generate a comparable cash flow. These expenses can be viewed not only as the current cost of development, but also as investment in a future productive asset: a software product, service, infrastructure, or another system capable of subsequently creating economic value.

This framing is especially visible in agent-based development. A substantial share of intellectual work begins to carry a directly measurable cost: researching a problem, generating alternatives, writing and revising code, testing, preparing documentation, analyzing failures, and other operations consume computing resources. What was previously expressed mainly in hours of human labor, and was therefore often perceived as a hidden cost, increasingly acquires a visible monetary equivalent.

The appearance of the first revenue, however, does not mean that the product has become economically self-sufficient. Several transitions can be distinguished between initial investment and a sustainable development model.

The first is the **[demand validation threshold][g-demand-validation-threshold]**: users begin paying for the product, providing the first empirical confirmation that the outcome being created has commercial value. At this stage, revenue may still be substantially lower than accumulated and current expenditure.

The next transition is the **[self-financing threshold][g-self-financing-threshold]**. Product revenue can now cover operation and a reasonable amount of continued development without constant external funding from the creator. The project ceases to exist solely through additional investment and begins to support its own development partly or completely.

Agent-based development has an even more interesting threshold: a **[positive marginal return on machine labor][g-positive-marginal-machine-labor-return]**. It is reached when each additional expenditure on AI produces, with sufficient repeatability, additional profit greater than the cost of the development cycle itself and its associated expenses.

In simplified form, the condition can be represented as follows:

$$
\Delta P > C_{AI} + C_{other},
$$

where \(\Delta P\) is the additional profit arising from a product change, \(C_{AI}\) is the cost of the AI resources used, and \(C_{other}\) represents the other incremental expenses of implementing, verifying, operating, and promoting the change.

It is essential that this not be a single fortunate case. One set of changes may happen to pay for itself while another does not. An economically mature loop emerges when the system can **repeatedly convert part of the revenue already earned into further improvements that create still more value**.

A self-sustaining sequence appears:

**product revenue -> AI resources -> product improvement -> additional revenue -> new development resources.**

At this point, AI ceases to be merely an item of initial investment. The results of earlier cycles of machine labor begin to finance subsequent cycles.

Cheaper development also creates the opposite effect. The less expensive a new feature becomes to produce, the weaker the natural barrier to implementing it. There is a temptation to keep adding capabilities simply because doing so has become technically easy and relatively cheap. As a result, a project may expend resources with great efficiency on creating something users do not need.

Reducing the cost of intellectual production therefore does not eliminate the problem of choice. On the contrary, it can make choice the central problem. Where many decisions were previously eliminated by the question “can we afford to develop this?”, advanced agent systems increasingly require a different question: **“why should this be developed at all?”**

As execution becomes cheaper, scarcity may thus move from the ability to create a change to the ability to determine **which particular change will create additional external value**. This is directly connected to the broader question of the [scarcity shift][g-scarcity-shift]: cheap generation does not automatically make market understanding, direction selection, hypothesis testing, or decision-making cheap.

It is especially important to separate sunk expenditure from the decision about the next step. If a project has already consumed substantial resources, that alone does not demonstrate a need to continue spending them in the same direction. The marginal question is more important for the next development cycle:

> **If one more unit of AI resources is spent now, what additional value must it create, and how likely is that value to exceed the cost of obtaining it?**

This also changes the conception of engineering value. The complexity of the artifact produced ceases to be a reliable indicator of economic outcome. A small change that removes a critical obstacle to purchasing or using a product may have a much higher return than a large technical reworking that is almost invisible to the user.

A more general question follows:

> **If the cost of creating a software change continues to fall, should the value of engineering work be determined by the complexity of the result created or by the change that result causes in the external world?**

For CHLOYA, this question also has a methodological continuation. An agent task can be assessed not only by technical feasibility, risk, and required authority. In a commercial system, execution cost, verification cost, expected effect, and expected return also become material.

Before a consequential agent cycle begins, another decision layer therefore appears:

**value hypothesis -> expected effect -> execution cost -> verification cost -> probability of a successful outcome -> actual return.**

This approach differs fundamentally from a model in which an agent performs every technically permissible task. The ability to automate an action does not mean that it should be performed. For a commercial project, agent work must be justified not only technically but economically.

At the limit, one can imagine a system in which the orchestrator evaluates not only **“can I perform this task?”** but also **“is it justified to spend computing resources and human attention on it now?”** The final decision still depends on project goals: some work is necessary for safety, compliance, reduction of future risk, or accumulation of technical potential and therefore need not produce an immediate short-term profit.

A more fundamental question remains open:

> **If the cost of intellectual execution continues to fall, will the principal constraint on commercial systems cease to be the capital needed for production and instead become the ability to find tasks in which an additional unit of machine labor creates more value than it consumes?**

If such a regime becomes sustainable, it is possible to speak of a **[self-financing agentic development loop][g-self-financing-agentic-development-loop]**: a system in which previously created economic value supplies resources for subsequent machine labor, while the continued use of AI is supported by the results of its earlier use.

This does not imply infinite automatic growth. Any such loop is constrained by demand, competition, product saturation, customer acquisition cost, human attention, decision quality, and many external factors. Yet the very possibility of such a loop changes the economics of development: AI becomes not only a tool on which capital is spent, but potentially part of the mechanism through which a product can reproduce resources for its own continued development.

[g-authority]: ../../research/GLOSSARY.en.md#authority
[g-alert-fatigue]: ../../research/GLOSSARY.en.md#alert-fatigue
[g-automation-bias]: ../../research/GLOSSARY.en.md#automation-bias
[g-bottleneck-shift]: ../../research/GLOSSARY.en.md#bottleneck-shift
[g-context]: ../../research/GLOSSARY.en.md#context
[g-delegation]: ../../research/GLOSSARY.en.md#delegation
[g-demand-validation-threshold]: ../../research/GLOSSARY.en.md#demand-validation-threshold
[g-evidence]: ../../research/GLOSSARY.en.md#evidence
[g-governance-plane]: ../../research/GLOSSARY.en.md#chloya-governance-plane
[g-meaningful-human-control]: ../../research/GLOSSARY.en.md#meaningful-human-control
[g-minimum-agent-count]: ../../research/GLOSSARY.en.md#principle-of-the-minimum-necessary-number-of-agents
[g-project-memory]: ../../research/GLOSSARY.en.md#project-memory
[g-positive-marginal-machine-labor-return]: ../../research/GLOSSARY.en.md#positive-marginal-return-on-machine-labor
[g-risk-adaptive-autonomy]: ../../research/GLOSSARY.en.md#risk-adaptive-autonomy
[g-scarcity-shift]: ../../research/GLOSSARY.en.md#scarcity-shift
[g-self-financing-agentic-development-loop]: ../../research/GLOSSARY.en.md#self-financing-agentic-development-loop
[g-self-financing-threshold]: ../../research/GLOSSARY.en.md#self-financing-threshold
[g-verification-competence-paradox]: ../../research/GLOSSARY.en.md#verification-competence-paradox
