# Code as a Shared Language for Humans and AI

> **Version:** `0.3.1`  
> **Status:** under discussion

## Contents

- [9.1. Code as a Shared Language for Humans, AI, and the Computing System](#91-code-as-a-shared-language-for-humans-ai-and-the-computing-system)
- [9.2. From Intent to a Machine-Interpretable Artifact](#92-from-intent-to-a-machine-interpretable-artifact)
- [9.3. Contextual Self-Sufficiency and Context Debt](#93-contextual-self-sufficiency-and-context-debt)
- [9.4. Code Structure as a Means of Conveying Meaning and Constraining Interpretation](#94-code-structure-as-a-means-of-conveying-meaning-and-constraining-interpretation)
- [9.5. Code, Comments, and Project Memory](#95-code-comments-and-project-memory)
- [9.6. Verifiable Properties and the External Verification Loop](#96-verifiable-properties-and-the-external-verification-loop)
- [9.7. Code Changes as Controlled State Transformations](#97-code-changes-as-controlled-state-transformations)
- [9.8. Execution as a Way of Understanding Code](#98-execution-as-a-way-of-understanding-code)
- [9.9. Code for the Next Participant](#99-code-for-the-next-participant)
- [9.10. The Limits of Code as a Shared Language](#910-the-limits-of-code-as-a-shared-language)
- [9.11. Code as a Shared Working Surface](#911-code-as-a-shared-working-surface)
- [Chapter 9 Conclusion](#chapter-9-conclusion)

## 9.1. Code as a Shared Language for Humans, AI, and the Computing System

Software code has traditionally been viewed primarily as a means of specifying computation. In this view, a human formulates a solution in a programming language, after which a compiler, interpreter, or other computing environment transforms the recorded description into a sequence of executable actions. Classic work on programming, however, already showed that this view is too narrow. A program is not intended only for a machine. It also serves as a way to express ideas about a computational process, communicate intent to other developers, and preserve part of the knowledge about the system that has been built.

*Structure and Interpretation of Computer Programs* treats a programming language as a means of formally expressing computational processes and a program not merely as a set of instructions for a computing machine, but also as a way of recording human thought about the problem being solved [369]. Donald Knuth approached a similar issue from another direction when he proposed literate programming: a program should be organized so that its structure can be explained coherently to a person and its machine representation is not completely separated from the human account of its intent [370]. These approaches differ in their goals and practical implementation, but they agree on one important point: source code has more than one audience.

In classical software engineering, those audiences were primarily the computing system and other developers. The machine requires formal correctness from a program, whereas a person must reconstruct the program's purpose, organization, and relationship to its surrounding system from its text. These processes are fundamentally different. A computing system does not need to understand the program's domain intent: it is enough for the representation to satisfy the language rules and be executable. A person, by contrast, constructs a mental model while reading code, relating individual constructs to known architectural decisions, the problem domain, and the system's expected behavior. Research on program comprehension shows that this process is not reducible to reading source lines in sequence. A developer uses the project structure, documentation, prior knowledge, element names, relationships between modules, and other sources of context [371].

Even well-written code, therefore, has never been a complete equivalent of knowledge about a software system. In *Programming as Theory Building*, Peter Naur observed that the outcome of programming cannot be reduced to the resulting program text. Developers form a certain account—a “theory”—of why the system has its particular structure, how individual decisions relate to the original problem, and under what conditions those decisions may be changed [372]. Part of this theory is expressed in source code, but some of it inevitably remains outside the code.

This limitation is fundamental to CHLOYA. Describing [code as a shared language][g-code-shared-language] does not mean that code contains all knowledge required about a project or can replace natural language, documentation, and [project memory][g-project-memory]. The claim concerns a different property: code is a formalized object on which different participants in the system can perform different but interrelated operations.

The emergence of modern AI models substantially changes the set of those participants.

The statistical regularity of software code was studied long before modern [large language models][g-llm] appeared. Hindle et al. showed that software code exhibits enough repetition and predictability for statistical language-modeling techniques to be applied to it [373]. This line of research subsequently led to models capable not only of predicting individual program elements, but also of analyzing large bodies of source code, generating new implementations, performing transformations, finding defects, producing tests, and participating in other software-lifecycle tasks. Recent surveys of [large language model][g-llm] use in software engineering show that their application is no longer limited to generating code from a textual prompt; it now spans dozens of task classes involving the analysis, maintenance, testing, and modification of software systems [374].

This introduces a new active participant between the human and the computing system.

An AI model can take existing code as input, relate its elements to one another, form hypotheses about their purpose, create changes, and return the result to the same codebase. Unlike a compiler or interpreter, it does not work only with the program's formal correctness. The model can use names, comments, surrounding context, characteristic programming constructs, and natural-language instructions. At the same time, the way it interacts with code is not identical to human understanding. A model should not be treated as simply another developer that constructs the same mental model of the system in the same way as a person.

The phrase **“[code as a shared language][g-code-shared-language]”** therefore requires clarification.

Shared use does not imply identical understanding.

A human, an AI model, and a computing system interact with the same representation in different ways. For a human, code is a source of information about the program's intent and organization. For a model, it is both input context and an object that may be transformed. For a computing system, code—or a representation derived from it—specifies formally defined behavior.

The ability of a single artifact to participate in all three processes is what makes code a distinctive medium of coordination.

In the simplest traditional model of programming, the interaction can be represented as intent passing from a human to a machine through a program:

**human -> code -> computing system.**

Using AI as a simple generator extends this model only slightly:

**human -> AI -> code -> computing system.**

Agentic development creates a more complex loop. Code exists independently of any one interaction and can repeatedly become input for humans, models, and engineering tools. A person changes the code directly or formulates requirements for an agent. The agent analyzes the project's current state and creates a change. Compilers, tests, analyzers, and the running system itself check the result. After verification, the new code state becomes available once again to the person and to subsequent agents.

The interaction therefore becomes cyclical:

**human <-> AI <-> code <-> execution and verification tools.**

In this model, code ceases to be merely the end product of generation. It becomes a persistent intermediate state of collaborative work.

Empirical research on programmers' use of generative assistants already shows that human–AI interaction is not limited to the one-way delivery of a finished solution. Developers use such systems both to accelerate actions they already understand and to explore possible solutions, successively accepting, modifying, or rejecting proposed variants [375]. As development moves from an individual assistant to agentic systems, this property becomes more important: one executor may work with another's result, while a new model invocation often lacks the complete internal context of the previous interaction.

Under these conditions, external representations of state that persist between individual acts of work become especially valuable.

An analogy with the **[boundary object][g-boundary-object]** concept introduced by Susan Star and James Griesemer is useful in describing this function. [Boundary objects][g-boundary-object] allow different groups to interact through a shared artifact even when each group uses it in its own context and interprets it according to its own tasks [376]. In software engineering, similar reasoning is applied to artifacts that support coordination between participants with different areas of responsibility and professional contexts [377].

Directly identifying source code with the classic [boundary object][g-boundary-object] would be inaccurate: the original concept describes interaction between social groups, whereas a human–agent system includes a computational executor as one of its participants. The functional similarity is nevertheless significant. The same code can be used by a person to analyze architectural intent, by a model to construct and apply a transformation, by a testing tool to verify properties, and by a computing system to execute it.

CHLOYA uses the concept of a **[shared working surface][g-shared-working-surface]** to describe this property.

A [shared working surface][g-shared-working-surface] is a persistent external representation accessible to multiple types of participants through which they can perceive system state, make changes, and verify the consequences of those changes within their respective capabilities.

Source code is one of the most important examples of such a surface, but it is not the only one.

This definition avoids two extremes. On the one hand, code should not be treated only as a machine product that humans create and that AI helps them create faster. That view underestimates its role in transferring state between participants and stages of work. On the other hand, code cannot be treated as a universal carrier of all project knowledge. Even a fully accessible codebase does not automatically explain product goals, organizational constraints, the reasons rejected decisions were rejected, temporary compromises, or plans for future development.

Natural language and code do not, therefore, displace one another.

Natural language is well suited to setting goals, discussing uncertainty, explaining reasons, and forming intent. Code provides a substantially stricter representation of those parts of a solution that can be expressed through program structure and checked by tools. [Project memory][g-project-memory] preserves information that must survive individual interactions but has no natural or unique representation directly in code.

Together, they form different representational layers of the same system.

The emergence of AI therefore does not reduce the importance of source code as a medium of communication. On the contrary, it increases that importance. The more participants can independently read and modify a project, the more important it is to have a persistent representation that does not depend on the internal context of one particular person or one particular model.

For an agent-modular approach, this yields an important methodological proposition:

> **code should be treated not only as the result of an executor's work, but also as an external state of collaborative activity accessible to humans, AI, and engineering tools.**

Such a state can outlast individual conversations, model invocations, and changes of executor. It can be read again, transformed, compared with a previous version, and independently verified. Code thus becomes one of the mechanisms through which continuity of work is achieved not by preserving an agent's internal state, but by preserving the project's verifiable external state.

Source code, however, is only one instance of a broader class of such representations. A modern software project includes data schemas, tests, configurations, queries, interface descriptions, infrastructure declarations, verification rules, and other formalized artifacts. Some are not software code in the traditional sense, but they have the same important property: they can be read by a person, processed by AI, and interpreted by a specialized software tool.

Further analysis must therefore move from source code itself to the broader concept of a [machine-interpretable artifact][g-machine-interpretable-artifact] and examine how natural-language intent is transformed through such artifacts into an executable and verifiable system state.

[Back to contents](#contents)

## 9.2. From Intent to a Machine-Interpretable Artifact

The previous section treated code as a [shared working surface][g-shared-working-surface] available to humans, AI, and computing tools. Source code, however, is only one possible representation of this kind. A modern software system consists not only of the functions, classes, and modules that implement it. A substantial part of its behavior is determined by data schemas, interface descriptions, configurations, queries, verification rules, infrastructure declarations, tests, and other artifacts that people can perceive and software tools can process.

This broadens the chapter's initial proposition. In human–agent development, the important transition is not so much a direct move from natural language to software code as a gradual move from human intent to a representation with which a computing environment can work.

The starting state is **intent**. It may express required behavior, an admissible system state, a constraint that must be observed, a rule governing component interaction, or the expected outcome of an operation. Initially, such intent often exists in natural language: in a task statement, a discussion, a requirements document, or an instruction to an agent.

Natural language is well suited to expressing uncertainty, discussing alternatives, and explaining reasons. That flexibility also creates room for interpretation. Different people or different model invocations may understand the same wording differently. Even when a requirement is understood correctly, compliance may depend entirely on whether the executor retained the relevant constraint in working context and applied it at the right moment.

Formalization allows part of this risk to be moved from interpretation to tool-enforced control.

The history of software engineering contains several approaches to this transition. Formal methods use mathematically defined representations to describe and analyze properties of software systems [378]. Their fundamental advantage is that a substantial part of the claims about a system ceases to exist only in natural language and acquires stricter semantics that specialized tools can analyze.

CHLOYA does not assume that every project should adopt a complete formal specification. In many applied systems, the cost of doing so would be disproportionate to the benefit. What matters methodologically is not maximum rigor, but the principle of progressively externalizing material constraints into representations that software tools can interpret independently.

Several levels of machine interaction with an artifact must therefore be distinguished.

A file may be available to a software tool as a sequence of characters or bytes, but availability alone does not imply an understanding of its structure. A structured format allows fields and values to be identified reliably, yet knowledge of that structure still does not establish what those values mean or how they should be used.

**Machine readability** and **machine interpretability** are therefore not synonyms.

A [machine-readable artifact][g-machine-readable-artifact] provides a representation whose structure a software tool can parse reliably. A [machine-interpretable artifact][g-machine-interpretable-artifact] goes further: a defined semantics exists for a material part of its elements, allowing a software tool to perform a check, transformation, analysis, or action on that basis.

The distinction is clear in structured text formats. A YAML or JSON file does not by itself tell a computing system what its fields mean; it merely provides a data structure. When that structure conforms to a defined schema, interface contract, infrastructure declaration, or workflow description, it acquires external semantics implemented by a particular tool.

Machine interpretability therefore does not arise from a filename extension or a superficial resemblance to source code. It arises from three elements acting together:

**a structured representation, defined semantics, and a software tool capable of applying those semantics.**

Executability is a still stronger property, but it should not be treated as a universal goal either.

Software engineering has long debated the advantages and limitations of executable specifications. Hayes and Jones observed that requiring every specification to be executable can restrict its expressiveness and prematurely bring a description of required properties closer to a particular implementation [379]. If making a requirement executable entails already determining algorithmic details or discarding important uncertainty, formalization begins to change the meaning of the original requirement.

Executable specifications also offer a substantial practical advantage. Fuchs emphasized that executing a specification makes it possible to explore the described behavior before a final implementation exists, identify inconsistencies, and involve the user earlier in evaluating the system under development [380].

These positions are less contradictory than they may appear. They describe two sides of the same problem.

Executability is useful when it makes a statement about the system observable and verifiable. It becomes harmful when it changes from a means of verification into a requirement to formalize something for which formalization does not yet fit the nature of the problem.

CHLOYA therefore imposes a fundamental limitation:

> **executability is a means of verifying and applying a specification, not an end in itself.**

This approach is especially important in agentic development. AI can formalize large bodies of requirements faster than a person, creating a temptation to convert every available project description into code or structured schemas. Automating the creation of formal representations, however, does not remove the need to verify that the chosen representation matches the original intent.

Moreover, the ability to produce a formalized artifact quickly may conceal a loss of meaning. A syntactically correct schema can formalize a misunderstood requirement with complete precision.

The move from intent to a [machine-interpretable artifact][g-machine-interpretable-artifact] should therefore not be seen as a one-way translation from an inferior form into a superior one. It is a progressive refinement of representation in which each new level of formality increases the possibilities for automated processing while also fixing a particular interpretation of the original intent.

Simple constraints illustrate the difference particularly well.

A task may state the following requirement:

> A user's age must be a positive integer.

This wording is understandable to a person and accessible to AI. As long as it exists only as a natural-language statement, however, compliance depends on the executor's behavior.

The same constraint can be expressed in a data schema. It then becomes available to a validator that can check the input independently of the agent that wrote the relevant program code.

A similar transition is possible for interfaces. A programming-interface method may be described in documentation, but an interface contract allows software tools to determine its operations, parameters, message structures, and other properties formally. Validators, client generators, documentation tools, and compatibility checks can then be built from that representation.

Infrastructure provides another characteristic example. A natural-language instruction may enumerate required servers, networks, access rules, and dependencies. A declarative infrastructure description converts some of this information into a representation from which a specialized tool can directly create or modify infrastructure state. Research into Infrastructure as Code practices documents precisely this transition from manual, primarily documentary descriptions of infrastructure to reproducible representations managed through software [381].

Different kinds of artifacts therefore have different degrees of operational capacity.

A requirements document may explain a desired state to a person and an agent. A data schema can additionally enforce constraints. An interface contract becomes a source for other tools. An infrastructure declaration may directly produce a change in external state. A test does not create the required behavior, but it can establish instrumentally whether that behavior is observed.

These representations do not form a linear scale on which each successive level is always better than the preceding one. They perform different functions. A greater degree of formalization is useful only when it matches the nature of the knowledge being recorded.

Some requirements are inherently difficult to reduce in advance to a fully defined executable form. Harel and Marron draw attention to the persistent problem of hard-to-specify requirements, where a material part of the task is discovering what the user regards as the correct result [382]. Uncertainty, subjective judgment, a changing context, and incomplete domain understanding do not disappear when a description is transferred into a formal syntax.

CHLOYA therefore does not treat formalization as a substitute for human discussion.

Instead, a [machine-interpretable artifact][g-machine-interpretable-artifact] should be understood as a way of fixing the part of intent that is already sufficiently well defined.

Uncertainty should remain visible where it genuinely exists. A prematurely fixed formal construct is dangerous because it creates the appearance of certainty and may later be treated by an agent as an unconditional source of truth.

This is especially significant in a human–agent system. A [large language model][g-llm] naturally works through probabilistic interpretation of context. If a material constraint appears only in a textual instruction, compliance depends on the model's ability to detect the constraint, relate it correctly to the current task, and retain it in working context until the moment of action.

When the same constraint is represented in a form that permits independent verification, the control architecture itself changes.

The condition is no longer merely part of an instruction to the executor. It becomes a property of the external working environment.

This marks an important boundary between two situations:

**the agent must remember the rule**;

and

**the system can independently detect a violation of the rule**.

The second arrangement is more robust because it moves part of the control out of the model's probabilistic behavior.

Recent research on coding agents has begun to use this capability directly. Jain treats executable specifications as runnable artifacts through which a coding agent or its surrounding system can observe properties of a candidate implementation by means of tests, input generators, dynamic analysis, and other tools [383]. In such a loop, the agent receives not only a textual description of expected behavior, but also a mechanism by which the result of its actions can be compared with that behavior.

CHLOYA can therefore formulate a more general principle:

> **if a material requirement can be expressed in a machine-verifiable form without losing important meaning, it should not remain exclusively in a natural-language instruction or in an agent's internal context.**

Machine verifiability does not necessarily imply complete executability.

A constraint may be expressed as a type, schema, contract, policy, test, static rule, or another formalized representation. What matters is not that the artifact perform an action on its own, but that a material part of the recorded knowledge can be applied independently of the current executor's interpretation.

This gives rise to the principle of **[sufficient formalization][g-sufficient-formalization]**.

[Sufficient formalization][g-sufficient-formalization] means moving intent to the level of machine interpretability required to perform the verification, application, or execution needed for a particular task, without forcing the formalization of properties for which it provides no comparable practical value or causes a loss of meaning.

This principle balances two extremes.

The first is to leave all material information in natural-language documentation and rely on each subsequent person or agent to reconstruct the necessary constraints independently.

The second is to attempt to turn every item of project knowledge into code, a schema, or a formal specification regardless of its nature.

CHLOYA takes an intermediate position: the degree of formalization is determined not by whether something can technically be formalized, but by the function the representation will perform in the working loop.

Moving to a formal representation does not finish the work on intent. Executing or verifying an artifact may reveal that the original description itself was incomplete or incorrect.

The process should therefore be treated as a closed loop:

**intent -> formalized artifact -> application or execution -> observation -> refinement of the intent or artifact.**

Feedback is fundamental here.

When a person sees only a natural-language description of future behavior, they must mentally model its consequences. An executable or verifiable artifact makes some of those consequences directly observable. The resulting observation may change the understanding of the task and lead to refinement of the specification itself.

In an agentic system, this cycle can be repeated many times. An agent helps formalize intent, applies the resulting artifact, runs available checks, analyzes the result, and proposes the next change. The person retains the ability to evaluate not only the text of the agent's proposal, but also the observable state of the system.

This does not give the agent the right to determine independently whether the goal is correct. A formalized artifact verifies that a result conforms to the recorded condition, but cannot itself prove that the condition faithfully reflects human intent.

Machine interpretability thus moves part of the control from the executor's reasoning into external mechanisms, but does not eliminate the need for people to define goals and evaluate meaning.

For CHLOYA, this extends the [shared working surface][g-shared-working-surface] principle formulated in the previous section. Such a surface may consist not of one kind of artifact, but of several interrelated representations. Natural-language documentation explains intent, a schema fixes structure, a contract defines an interaction boundary, a test records expected behavior, a declarative description specifies state, and software code implements the corresponding transformation.

The interaction of these representations gradually reduces the number of material conditions that exist only in the implicit context of a person or AI.

Formalization alone, however, still does not guarantee that the next participant will be able to use the artifact correctly. A formally valid schema, configuration, or program may require substantial external knowledge about why it exists, the assumptions on which it rests, and the other project elements to which it is related.

The next question is therefore not **how formal an artifact is**, but **how much additional context is required to understand and change it safely**.

That is the problem of [contextual self-sufficiency][g-context-self-sufficiency] and the [context debt][g-context-debt] created when it is lacking, to which we now turn.

[Back to contents](#contents)

## 9.3. Contextual Self-Sufficiency and Context Debt

Moving from natural-language intent to a [machine-interpretable artifact][g-machine-interpretable-artifact] reduces a result's dependence on an executor's unconstrained interpretation, but it does not eliminate another fundamental problem. Formally correct code, schemas, contracts, or configurations may remain difficult to change safely when their purpose becomes clear only after studying a substantial part of the project, reconstructing the history of decisions, or searching previous tasks and discussions.

Artifact quality is therefore determined not only by how rigorously it expresses the required state. It is equally important how much additional knowledge the next participant must recover in order to understand the artifact correctly, establish the boundaries of an admissible change, and assess its consequences.

This problem predates AI.

In his work on information distribution in design, David Parnas observed that giving every participant all available information about a system does not necessarily make development easier. Architecture and documentation should instead limit the information that must be considered when making a particular decision [384]. He later developed information hiding as a criterion for decomposing software systems: modules should conceal design decisions whose change should not require knowledge of the entire system's internal organization [76].

In this sense, modularity governs not only technical dependencies. It also governs the **distribution of knowledge**.

A good module boundary reduces the number of elements whose behavior must be understood at once. An explicit interface permits interaction with a component without reconstructing its entire implementation. A stable contract reduces the assumptions a participant must independently make about another part of the system.

One fundamental property of good architecture is therefore that it limits the body of knowledge required for local action.

Merely dividing a program physically into files and modules does not guarantee this property. A conceptually unified solution may be distributed among several distant parts of the system. Soloway et al. described such constructs as **[delocalized plans][g-delocalized-plan]**: elements of one plan may occur in different program fragments, so local reading reveals only part of the relevant picture [385].

An individual fragment may consequently appear understandable and logically complete while a correct change depends on a constraint in another module, a non-obvious order of calls, the behavior of an external component, or a reason for a decision that cannot be reconstructed directly from the code.

Research on software maintenance shows that much of a developer's work consists precisely of reconstructing such context. Ko et al. observed developers searching for supposedly relevant code, following incoming and outgoing dependencies, returning to elements found earlier, and gradually constructing a working area for the task. About 35% of the observed time was spent on mechanical navigation within source code and between files [386]. In their study of changes to existing systems, Sillito et al. identified a broad class of questions about the purpose, relationships, uses, behavior, and consequences of changing program elements that programmers must answer before they can confidently perform a local task [387].

The cost of understanding is therefore not determined only by the number of lines of code.

A substantial share of that cost is created by the **distance to required knowledge**: how many relationships must be discovered, how many representations compared, and how many assumptions checked before a participant has sufficient grounds to act.

Large language models change the technical capacity for such search, but do not eliminate the problem itself.

A model can process far more text than a person can hold in working attention at once. This can suggest a tempting conclusion: if a repository fits within a context window, architectural locality and careful context selection become less important.

Recent research on repository-level code work shows the opposite.

RepoCoder bases generation on iterative retrieval of relevant repository fragments because information useful for changing a particular part of a program may be distributed across several files [388]. The effectiveness of this approach itself demonstrates an important distinction: **access to the entire project is not the same as having the right working context**.

Moreover, different kinds of retrieved information are not equally useful. Gu et al. showed that information about directly related code and potentially used programming interfaces can improve repository-level generation, whereas superficially similar code fragments can create noise and, under some conditions, degrade results by as much as 15% [389].

Context is therefore characterized not only by volume, but also by relevance.

Excess information can compete with material constraints, present a model with outdated or alternative implementation patterns, and increase the number of plausible but incorrect relationships. A larger context window expands the available search space but does not determine which part of that space is required for a particular action.

MutaGReP is especially illustrative: rather than filling the context with a substantial portion of the repository, it searches for a plan linked to particular codebase symbols. In experiments, the resulting working context occupied less than 5% of an available 128,000-token window while producing results comparable to those obtained by supplying a much larger portion of the repository [390].

Modern repository-level generation methods increasingly use the structural dependencies of code itself. InlineCoder, for example, constructs context around callers and callees because textual similarity does not necessarily reflect the actual semantic relationship between program elements [391].

These results support a distinction important to CHLOYA between **available context** and **[required context][g-required-context]**.

Available context comprises all information a participant could potentially access: source code, documentation, tests, schemas, [project memory][g-project-memory], change history, execution results, tasks, and other related artifacts.

[Required context][g-required-context] is substantially narrower. It is the information without which a particular operation cannot be performed with the required reliability.

The goal is therefore not to saturate an agent with as much information as possible. The practical objective is for [required context][g-required-context] to be **bounded, discoverable, current, and recoverable**.

On this basis, CHLOYA uses the concept of **[contextual self-sufficiency][g-context-self-sufficiency]**.

> **[Contextual self-sufficiency][g-context-self-sufficiency] is a property of an artifact or bounded area of a system whereby the context required for typical safe work can be recovered from that area and a small number of explicitly discoverable related artifacts, without reconstructing a substantial part of the project or the history of previous work.**

Self-sufficiency in this definition does not mean physically concentrating all information in one file.

A type may reside in another module, an interface constraint in a contract, the reason for an architectural decision in [project memory][g-project-memory], and a [verifiable property][g-verifiable-property] in a test. What matters is not the physical distance between these representations, but how explicitly a participant can discover the relationship and navigate to the required source.

**Discoverability** is therefore one of the most important characteristics of [contextual self-sufficiency][g-context-self-sufficiency].

If a material constraint is moved out of the code but the code or project structure reveals where it is defined, the context remains manageable. If the same constraint exists only in an old discussion unknown to the next participant, the information may formally have been preserved but is effectively outside the working loop.

This distinction directly extends the rules for context transfer introduced earlier in CHLOYA. Giving the next executor several relevant files is insufficient if the provenance of a material claim, its degree of confirmation, the force of a constraint, the boundaries of an accepted decision, or known uncertainty are lost.

**Context sufficiency is therefore not only a quantitative property, but a semantic one.**

Two datasets of equal size may have fundamentally different value. One contains verified constraints and clearly exposes their provenance. The other mixes current decisions with assumptions, outdated instructions, and intermediate variants. The second may be larger without being more sufficient.

It also follows that transferring information does not by itself increase its trustworthiness.

An artifact appearing in the next agent's context does not become more reliable merely because a previous executor preserved it. Where later decisions depend on them, its provenance, verification status, and applicability boundaries must be preserved with its content.

[Contextual self-sufficiency][g-context-self-sufficiency] therefore cannot be achieved simply by accumulating text.

This problem is particularly visible in long agent trajectories.

For a short action, a model may temporarily retain much of the working state inside its current context. As work continues, intermediate decisions, verification results, discovered constraints, rejected hypotheses, and changed project state accumulate. If continuity depends mainly on the history of one session, the context inevitably grows larger and more heterogeneous.

CHLOYA therefore treats a long-running task not as a single, continuously growing dialogue stream, but as an external process with persistent state.

Material results must be embodied in code, [project memory][g-project-memory], checkpoints, verification results, and other recoverable artifacts. The next stage of work should begin by reconstructing a bounded current task state, not by rereading the entire preceding reasoning trajectory.

This approach makes context part of workflow architecture.

The opposite condition is **[context debt][g-context-debt]**.

> **[Context debt][g-context-debt] is the accumulated additional search, reconstruction, and interpretation required to change a system safely because material context is distributed, implicit, outdated, contradictory, or accessible only through a disproportionately large area of the project.**

It may exist even in a technically correct, well-functioning system.

For example, a function may be compact, covered by tests, and free of obvious defects, yet depend on an external constraint whose rationale survives only in a long-closed task. The next executor may understand the function's algorithm completely and still make a locally reasonable change that violates a system requirement.

In another case, all required information may be present in the repository but distributed across many files without explicit paths between them. The information has not formally been lost, yet reconstructing it requires disproportionate effort.

[Context debt][g-context-debt] also arises from the opposite problem: excess. Several documents may contain different versions of the same rule. Old instructions remain beside new ones. Exceptions, temporary decisions, and information about components that no longer exist gradually accumulate in an agent's persistent context file.

Research into persistent context files for coding agents shows that such documents are already becoming complex artifacts in their own right. An analysis of 2,303 files from 1,925 repositories found that they change regularly and contain substantial information about project implementation, architecture, building, and execution, while security and performance requirements appear far less often [392].

A single large instruction file is therefore not a universal solution to the context problem.

If all project knowledge is successively transferred into it, [context debt][g-context-debt] does not disappear. It moves from the codebase into a new monolithic artifact that itself requires maintenance, localized ownership, and the removal of outdated information.

CHLOYA therefore favors distributing knowledge according to its nature and scope. Project-wide rules remain at project level, component knowledge is linked to the component, interface constraints are expressed in contracts, [verifiable properties][g-verifiable-property] in tests and schemas, and the reasons for nontrivial decisions in [project memory][g-project-memory]. An agent need not receive all of this information in advance. It must be able to discover and attach the next layer of context as needed.

In this view, context resembles a **graph of related knowledge** more than a single document.

The graph's nodes are code, tests, contracts, documentation, decisions, verification results, and other artifacts. Its edges indicate which information must be considered together. A bounded working area is formed from this space for a particular operation.

This is why [contextual self-sufficiency][g-context-self-sufficiency] does not mean minimizing the number of files.

It means **minimizing implicit transitions**.

The clearer the ownership boundary, the material external conditions, and the path to the next required level of knowledge are to a participant, the lower the cost of constructing a working model of the system.

The problem has another dimension that is especially visible in agentic development.

For a person, poorly organized context primarily increases the cognitive cost of work. For AI, it also creates direct computational cost. Repeated search, loading excess files, analyzing irrelevant fragments, additional model iterations, and rerunning checks consume time, computing resources, and paid tokens.

[Context debt][g-context-debt] is therefore more than a maintainability characteristic. In an agentic system, it can become an **operational cost attached to every subsequent change**.

A more capable model's ability to read a large repository may temporarily conceal this debt, but does not eliminate it. If an agent must re-investigate a substantial part of the project for every small operation, the cost of context reconstruction is paid on every invocation.

This is particularly important for systems in which AI becomes a permanent development participant. A lower cost of code generation alone does not guarantee a lower cost of development if a substantial part of the computational budget is spent repeatedly reconstructing poorly organized project context.

Architectural quality thus begins to affect not only the cost of human maintenance, but also the economics of agent execution directly.

This relates to another problem observed in development with generative models: new code may appear faster than people can form a durable understanding of the system. Ahmad describes this condition as **comprehension debt**—the gap between what a team actually knows about a codebase and what it must know to maintain it reliably [393].

[Context debt][g-context-debt] is related to this phenomenon, but is not identical to it.

Comprehension debt lies primarily in participants' collective knowledge. [Context debt][g-context-debt] characterizes the organization of the knowledge environment itself: how expensive it is for a person or agent to obtain the information required for action.

A project may have high [context debt][g-context-debt] even while an expert team compensates for it through its own experience. The debt becomes visible when a new developer joins, the team changes, or a task is transferred to an agent that lacks the previous participants' implicit knowledge.

The reverse is also possible: a project may have well-organized code, contracts, and documentation while a particular team still lacks sufficient understanding of a complex domain.

These forms of debt therefore require different reduction mechanisms.

For [context debt][g-context-debt], the key mechanisms are architectural boundaries, explicit dependencies, localized rules, [project memory][g-project-memory], current artifacts, and a way to discover relevant information.

Comprehension debt instead requires a process through which participants build knowledge.

Likewise, [context debt][g-context-debt] is not reducible to technical debt or documentation debt. A poor technical decision may be thoroughly explained and readily discoverable; its technical debt is then high while its context debt is relatively low. Conversely, a technically sound decision may have almost unrecoverable grounds and hidden constraints.

Context thereby becomes a design object in its own right.

CHLOYA derives the following principle:

> **design not the maximum context, but sufficient and reliably recoverable context; material information should be available through bounded and predictable relationships, just as system functionality is available through its interfaces.**

This approach changes the criterion of architectural quality in a human–agent environment.

A well-structured project limits not only how far the consequences of a change propagate. It also limits how far the knowledge required for that change must spread.

If correcting local behavior routinely requires reading a substantial part of the repository, reconstructing old discussions, explaining the architecture again, and loading a large body of persistent instructions, the problem cannot be reduced to an insufficiently large context window. It is a property of the system's organization.

At the same time, [contextual self-sufficiency][g-context-self-sufficiency] is always relative to the operation being performed. One body of information may be sufficient to correct a local defect and insufficient to change a component's architectural role. The goal is therefore not to create absolutely autonomous elements.

The goal is to keep the required body of knowledge bounded for typical classes of action and to expand it through explicit, verifiable relationships.

This is where [contextual self-sufficiency][g-context-self-sufficiency] connects directly to modularity.

A module, interface, type, contract, and dependency begin to perform two functions. They define the program's execution structure while organizing the knowledge space available to humans and AI.

The next section therefore considers code structure not only as a traditional mechanism of software decomposition, but also as a means of conveying meaning, constraining the space of interpretation, and governing the context available to the next participant.

[Back to contents](#contents)

## 9.4. Code Structure as a Means of Conveying Meaning and Constraining Interpretation

[Contextual self-sufficiency][g-context-self-sufficiency], discussed in the previous section, requires more than the mere presence of necessary information in a project. Material information must be discoverable, and the path from an element being changed to related constraints, dependencies, and contracts must remain reasonably short and predictable. The structure of the software system itself is one of the main mechanisms for achieving this property.

Code communicates information through more than the operations it performs.

Entity names, function signatures, types, interfaces, the placement of elements in modules, dependency directions, and architectural boundaries form an additional representation of the system. They show which concepts exist in the project, which parts of the system belong together, how a component may be used, and which details should be immaterial to an external participant.

In this sense, code structure performs two functions.

It organizes computation, and it organizes knowledge about that computation.

This view directly extends the classic idea of information hiding. In Parnas's approach, a module boundary conceals design decisions that the rest of the system should not need to know [76]. Information hiding does not mean that information disappears. It redistributes it: internal complexity remains inside the component, while a more stable and bounded representation required to use it is exposed.

The abstract data types proposed by Liskov and Zilles follow the same logic. An abstract object is characterized primarily by the operations available on it rather than by its particular internal storage and implementation [394]. Its external interaction contract matters to a user, while its implementation may change independently.

Abstraction can therefore be treated not only as a way to manage implementation complexity, but also as a **context boundary**.

If using a component requires knowing all its internal algorithms, data structures, and private conventions, the component creates almost no information boundary. If a bounded, stable interface expresses the material part of the interaction, the next participant can work with the component without reconstructing its internal implementation model.

A good abstraction thereby reduces the knowledge required outside it while preserving the necessary interaction guarantees.

Parnas, Clements, and Weiss developed this idea for complex software systems and proposed supplementing modular decomposition with a hierarchical module guide that helps a developer determine which parts of a system must actually be understood for a particular task [395]. The direction of this approach is important: architecture should not only divide a program into elements, but also help a participant navigate the space of knowledge about them.

System structure can therefore be viewed as a mechanism for **routing understanding**.

A person or agent encountering an entity can determine its place in the system, external dependencies, permitted operations, and the direction of further search. The more clearly structure expresses these relationships, the less participants must rely on guesswork and their predecessors' implicit knowledge.

Structural meaning arises at several levels at once.

At the local level, naming plays a significant role. A function, parameter, variable, or type name does not change a program's machine semantics to the same extent as changing the operation it performs, but it does change the information environment in which a person or AI interprets that operation.

For example, two functions with identical bodies but the names `process()` and `calculate_invoice_total()` provide an external reader with fundamentally different amounts of domain context. A computing system may execute them identically, but the second name gives a person or model a hypothesis about the operation's purpose before its implementation is analyzed.

An identifier should therefore be treated not as a decorative label, but as a **claim about an entity's meaning**.

Empirical research confirms that naming can affect program comprehension, although the effect is not mechanical. Avidan and Feitelson found that meaningful parameter names can substantially aid code comprehension, whereas the effect of local names was weaker. At the same time, in some production methods they examined, the original names were so poor or misleading that they offered no advantage over meaningless identifiers [398].

This observation is especially important to CHLOYA.

A good name reduces [required context][g-required-context] because part of the domain knowledge becomes available directly at the point of use.

A weak name fails to communicate that information.

An incorrect name is more dangerous than either: it creates plausible but false context.

The last case carries additional significance in human–agent development. A large language model relies heavily on lexical cues when interpreting surrounding code. A semantically convincing but outdated or incorrect name can therefore direct a solution down the wrong path before the executor investigates the implementation's actual behavior.

Names should consequently reflect an entity's current role, not the history of how it arose.

If a component's purpose has changed so much that its old name no longer describes its function, retaining the familiar identifier is not neutral; it preserves a false contextual signal.

Naming, however, is only a weak form of structural knowledge. A name conveys intent but by itself places almost no constraint on how an entity may be used.

Signatures, types, and interfaces provide stronger mechanisms.

An interface defines the part of a component available to an external participant and thereby draws a boundary between knowledge required to use the component and knowledge required to implement it.

Traditional software engineering treats this mainly as a means of reducing coupling and allowing implementations to be substituted. A human–agent environment adds another function: an interface **constrains the space of interpretation**.

A well-defined interface communicates which operations are permitted, which data is accepted and returned, which entities belong to the external contract, and which internal details the rest of the system must not use.

An interface does not prescribe a component's sole possible implementation. Preserving multiple possible internal implementations is one of abstraction's purposes. At the same time, however, the interface reduces the set of assumptions an external participant may make about that implementation.

This distinction matters.

What is narrowed is not the space of possible implementations, but the space of admissible external interpretations.

Meyer's Design by Contract strengthens this idea by explicitly representing preconditions, postconditions, and invariants of interacting components [397]. The interface then conveys not only the shape of a call, but also some of the parties' obligations: which state is assumed before an operation and which properties must hold afterward.

In Section 9.4, the contract matters primarily as a means of conveying meaning.

The ability to check such conditions automatically is considered separately below. At this earlier stage, what matters is that a condition ceases to exist only in a developer's mind, a comment, or a discussion history and becomes explicitly connected to the system boundary to which it applies.

This is another way of reducing [context debt][g-context-debt].

If an external participant needs to know that a function parameter must be nonzero, the constraint can be stated in documentation. But when it can naturally be expressed in a type, signature, or contract, the participant no longer has to discover a separate textual rule and manually associate it with the relevant operation.

Part of the [required context][g-required-context] becomes embedded in the structure of the [shared working surface][g-shared-working-surface].

These properties are not limited to internal programming interfaces.

Research by Bogner, Kotstein, and Pfaff shows that the design of an external programming interface directly affects its comprehensibility. In a controlled experiment with 105 participants, violating 11 of 12 studied REST API design rules produced statistically worse performance on comprehension tasks; for nine rules, participants also rated the violating variants as more difficult [399].

The particular set of REST rules is not the central point for CHLOYA.

The result demonstrates a broader property: interface form affects the cost of reconstructing its meaning.

An interface may be functionally sufficient while forcing users to make additional assumptions, remember exceptions, and learn non-obvious conventions. In another interface, the organization itself helps predict behavior before detailed documentation is read.

Consistent structure can thus turn system regularity into a contextual advantage.

When similar entities are organized similarly, the next participant can transfer an already validated model of understanding to new parts of the project. When equivalent tasks are solved through entirely different constructs for no substantive reason, every new location must be investigated afresh.

This does not require mechanical uniformity.

Different domain entities may require different structures. The problem arises when a difference expresses no meaning and is merely an accident of development history.

Structural heterogeneity then becomes additional context that every subsequent executor must reconstruct.

From this perspective, Green and Petre's cognitive dimensions of notations are useful. They consider properties of representations that affect the difficulty of working with them, including hidden dependencies, viscosity of change, and secondary notation [396]. The idea of a **hidden dependency** is especially important to CHLOYA: one element may be logically related to another while the representation makes that relationship difficult for its user to see.

Such dependencies can take many forms in a software system.

A function relies on global state not reflected in its interface. A component's behavior depends on an unstated order of calls. Changing one type requires a corresponding change in another module even though the structural link between them is difficult to discover. A material constraint exists only as a convention among developers.

In all these cases, the program's formal structure reveals less than must be known to change it safely.

This yields an important distinction between an **existing dependency** and an **expressed dependency**.

A relationship may exist in the system's behavior without being sufficiently visible in its software representation.

The more such relationships exist, the more a participant must compensate for missing structure with external context.

This directly connects to the [context debt][g-context-debt] discussed in 9.3: an implicit material dependency forces each subsequent participant to rediscover something that the system could have communicated structurally.

The opposite conclusion—that all knowledge should be expressed through as many structural constructs as possible—does not follow.

Explicitness also has a cost.

An additional interface, type, adapter, factory, or abstraction layer may locally make an element's purpose more explicit while increasing the number of transitions required to understand the overall operation. A system made up of a large number of extremely small abstractions can hide a simple action behind a long chain of indirect calls.

Individual boundaries may then be formally well defined while the operation's meaning is distributed across too many layers.

Structural explicitness and [contextual self-sufficiency][g-context-self-sufficiency] therefore do not mean maximizing the number of abstractions.

Good structure must **hide irrelevant details without hiding material relationships**.

This supports a more practical constraint:

> **an abstraction is useful only while the cost of understanding its boundary and crossing it is lower than the cost of understanding the details it makes unnecessary to consider.**

This criterion is especially important when code generation is inexpensive. AI can quickly create additional architectural layers, interfaces, helper types, and wrappers. The technical ease of creating an abstraction does not mean its appearance reduces the system's overall complexity.

Each new structural element should either reduce the knowledge required for subsequent actions or express a material boundary or rule that would otherwise remain implicit.

Otherwise, the number of formal constructs grows without reducing the cost of reconstructing meaning.

Similar caution is needed when evaluating types as documentation.

Type information can substantially narrow the set of admissible states and explicitly reveal relationships between entities. A signature `UserId -> User` provides the next participant with substantially more information than an operation on two unspecified objects.

It does not follow, however, that adding more type annotations automatically improves program comprehension.

A 2026 eye-tracking study by Alznauer et al. found an interesting difference between subjective perceptions of types and objective comprehension measures. Almost all participants considered type annotations useful, yet the experiment with 40 developers found only limited effects on measured behavior and understanding; on average, annotations even slightly increased the time spent on the fragments [401].

This aligns well with the [sufficient formalization][g-sufficient-formalization] principle from 9.2.

A type is a valuable structural signal when it reduces actual ambiguity.

A type that repeats information obvious from the surrounding expression can add text without adding meaningful knowledge. A type that expresses a domain distinction, forbidden state, or material interface boundary can substantially reduce the space of interpretation.

The goal is therefore not maximal typing as such, but **sufficient structural explicitness**.

The same reasoning applies to other constructive program elements.

An architectural layer is useful when it expresses a real ownership boundary.

An interface is useful when it separates a stable mode of interaction from a changeable implementation.

A separate type is useful when it expresses a material distinction between states or concepts.

A named function is useful when it identifies an independent operation and communicates its purpose.

In every case, the criterion is the same: the structural element must reduce the need for external assumptions more than it increases the cost of navigating the system.

This issue also directly concerns AI.

Large language models can process source code as a sequence of tokens, but the code's structure can provide an additional source of information. AST-T5 uses a program's abstract syntax tree during model pretraining and demonstrates advantages of a structure-oriented representation on code generation, transformation, and comprehension tasks compared with similarly sized models that do not use such processing [400].

At repository level, the same idea appears in InlineCoder [391], where relevant context is determined not only by textual similarity, but also by the structural relationships between callers and callees.

This supports a significant conclusion.

**Program structure is not merely a human way of organizing source text. It is a machine-extractable source of context.**

An abstract syntax tree, call graph, imported dependencies, module membership, signatures, types, and scopes expose relationships that a tool can discover without having to infer them solely from natural-language cues.

The same architecture thereby begins to serve several participants on the [shared working surface][g-shared-working-surface] at once.

It helps a person form a mental model of the system.

It gives AI additional signals for determining the purpose and relationships of elements.

It gives compilers, analyzers, and other software tools formally extractable relationships.

This does not mean that people, models, and tools interpret structure identically. As Section 9.1 showed, the ways in which they interact with code differ fundamentally. Well-organized structure can nevertheless reduce uncertainty for several kinds of participants at once.

Particularly interesting evidence comes from a 2026 study by Abdelsalam et al. The authors compared the responses of programmers and large language models to code regions containing known comprehension obstacles. Human difficulty was assessed using neurophysiological measures, while model difficulty was assessed through changes in perplexity. Increased model uncertainty correlated with the location and severity of regions that produced signs of difficulty in people [402].

This does not mean that a person and a large language model understand a program in the same way.

It demonstrates a narrower property important to CHLOYA: some characteristics of a program representation can make code harder to process for different participants at the same time.

Human readability and suitability for AI should therefore not be treated as opposing goals by default.

The emergence of coding agents does not require a separate “code language for the model” that is difficult for people to understand. On the contrary, many properties traditionally associated with maintainability—clear boundaries, consistent naming, discoverable dependencies, and predictable structure—become more important because more participants now interact through them.

CHLOYA calls this body of information **[structural context][g-structural-context]**.

> **[Structural context][g-structural-context] is the part of [required context][g-required-context] expressed directly by the organization of software artifacts: naming, signatures, types, interfaces, the assignment of elements to components, dependency directions, and other explicitly discoverable structural relationships.**

This concept connects the results of Sections 9.3 and 9.4.

Not all [required context][g-required-context] should be moved into documentation or separate memory files. Much of it already has a natural structural expression within the software system itself.

If a dependency can be shown through an architectural relationship, it should not exist only as a rule in an instruction to an agent.

If a permitted mode of interaction can be expressed through an interface, each new executor should not be expected to reconstruct it independently from implementations.

If a domain distinction is critical to system correctness and is naturally expressible through types, preserving the distinction only in a comment leaves unnecessary room for misinterpretation.

This yields the **[principle of structural explicitness][g-structural-explicitness]**:

> **relationships and constraints material to the safe understanding and modification of a system, and naturally expressible through its structure, should wherever possible be fixed in the structure of software artifacts themselves rather than left solely in implicit conventions, comments, or a participant's internal context.**

The principle does not require a maximum number of types, interfaces, or architectural layers.

Its purpose is the opposite: to reduce the number of assumptions the next participant must make.

Structural sufficiency is therefore determined not by the number of explicitly represented entities, but by the cost of reconstructing the required meaning.

A well-structured area of code answers basic questions about its role before its implementation is studied deeply: which component it belongs to, what input it receives, what it exposes, which parts of the system it depends on, and which boundaries it must not cross.

If answering these questions requires reading a long natural-language guide, task history, or dozens of apparently unrelated files, part of the [structural context][g-structural-context] has effectively been moved out of the program structure and turned into [context debt][g-context-debt].

This also clarifies the role of documentation.

Documentation should not compensate for every possible lack of clarity in program structure.

If a fact is naturally expressed directly by code, a type, an interface, or an architectural dependency, duplicating it in prose creates two sources of the same knowledge that may later diverge.

Text is especially valuable where it must explain something that program structure cannot express or does not express well enough.

An interface, for example, may clearly show that a component does not depend on a particular system layer. It does not necessarily explain **why** that boundary was considered important.

A type can preserve a distinction between two classes of values but may not preserve the history of the problem that caused the distinction to be introduced.

A contract can record a mandatory condition without adequately explaining the external organizational or domain constraint that produced it.

This is the natural limit of what code structure can do.

It can express much of the system's current organization and constrain the set of permitted interactions. Not all material project knowledge, however, has a natural structural representation.

The next question is therefore not how well the code is organized, but **which knowledge should remain in the code itself, which should be explained immediately beside it, and which belongs in long-term [project memory][g-project-memory]**.

The next section addresses that division.

[Back to contents](#contents)

## 9.5. Code, Comments, and Project Memory

The preceding sections showed that much [required context][g-required-context] can be expressed directly through the structure of a software system. Names, types, interfaces, contracts, and dependency directions make some knowledge discoverable without a separate explanation. This mode of representation, however, has limits.

Current code can show **how** a system is organized. It is much harder to determine why one option was selected from several possibilities, which external constraint produced an unusual construct, which alternatives were investigated and why they were rejected, whether an existing solution is final or temporary, and which assumptions held when it was adopted.

Attempting to preserve all such information in program structure causes excessive formalization. Putting it in comments turns source code into a development log. Leaving it only in conversation history, individual memories, or closed discussions creates [context debt][g-context-debt].

Human–agent development must therefore separate kinds of knowledge according to their purpose and useful lifetime.

Code, comments, change history, and [project memory][g-project-memory] are not competing ways of documenting the same fact. They serve different functions.

### Current State and State Provenance

Software code primarily represents the **current state of the implemented system**.

This does not mean that source code always determines the complete behavior of the entire system; behavior may depend on configuration, data, environment, and external components. With respect to implementation itself, however, code is the principal representation of what the system does now.

Historical explanations that do not directly help explain current behavior are therefore poorly suited to source code.

A comment such as:

> this area used a different algorithm before; the agent then tried two more approaches, after which the code was rewritten

may be accurate while doing almost nothing to help the next participant use the existing implementation. It forces the reader to distinguish the current solution from the stages through which it arose and gradually turns the file into a mixture of program state and development log.

This problem is especially visible in agent execution. AI can generate detailed explanations of its actions with almost no additional human effort. A technically easy but methodologically dangerous path therefore appears: preserving much of the work process directly in comments.

The code then accumulates statements that something “was fixed,” “was added by an agent,” “was used previously,” “was changed after testing,” or “was left for future rework.”

Such records create persistent contextual noise.

Every subsequent person and agent must reread a history much of which no longer bears on the decision at hand. As the project evolves, this information becomes outdated while continuing to shape context and increase the computational and cognitive cost of work.

CHLOYA therefore distinguishes between **system state** and **state provenance**.

Code and its local explanations should primarily describe what is material to understanding the current implementation correctly.

The provenance of a solution—who changed it, when, for which task, which intermediate variants existed, and how the system arrived at its present state—belongs in change history and [project memory][g-project-memory].

This distinction does not discard history. On the contrary, history is preserved in a representation intended for it, where it can be examined when it is genuinely needed.

### A Comment as a Local Layer of Meaning

The [principle of structural explicitness][g-structural-explicitness] introduced in 9.4 might be taken too far: good code supposedly needs no comments because everything material should be expressed through names, types, and architecture.

Empirical research does not support that conclusion.

Pascarella, Bruntink, and Bacchelli analyzed more than 40,000 lines of comments from open and closed projects and showed that comments perform many different functions [403]. They may briefly describe an element's purpose, explain behavioral details, give reasons for a decision, warn about usage characteristics, record tasks, or provide other information related to the code.

The common rule that “a comment should explain why, not what” is therefore a useful practical heuristic, but an insufficient methodological principle.

Sometimes a short explanation of **what a complex construct represents** genuinely reduces the cost of understanding. In another case, a warning about unusual behavior or a constraint is more useful. Sometimes a small fragment's purpose is already clear from program structure, and describing it again merely creates noise.

For CHLOYA, the more precise criterion is not the grammatical form of a “what?” or “why?” question, but whether there is **[locally necessary knowledge][g-locally-necessary-knowledge]** that cannot be obtained reliably enough from code structure itself.

> **A comment should supplement the current software representation with knowledge that is required beside a particular area of code and is not expressed clearly enough by the code itself.**

Such a comment may explain the reason for an unusual decision.

It may warn that an external system violates formally expected behavior.

It may record a non-obvious invariant when the language or architecture cannot express it directly.

It may point to a related project decision.

It should not mechanically repeat an obvious program operation.

If a line increments a counter by one, a comment saying “increment the counter by one” adds almost no knowledge.

If the increment occurs at that exact location because of a nontrivial event-processing order, a comment explaining the reason for its placement may be material.

A comment's usefulness is thus determined by its **added semantic information**, not by its mere presence.

A 2026 study of comments' effect on code comprehension also shows a mixed picture. In an experiment by Abdelsalam et al., comments in different fragments both improved and worsened measured comprehension; the effect depended on the particular code and comment. Comments nevertheless directed participants' visual attention noticeably and were subjectively perceived as useful in difficult fragments [405].

A comment is therefore not a cost-free improvement.

It consumes human attention and, in an agentic system, part of the model's context. Every persistent comment must therefore justify its own cost through the knowledge it adds.

### A Comment Is Part of Current State

There is another consequence of this approach.

A comment cannot be treated as an independent historical explanation that is added to code once and then remains unchanged.

If a comment describes the current system, it must evolve with the system.

Fluri, Würsch, and Gall studied the co-evolution of code and comments and showed that changes to these two representations are far from always synchronized [404]. A mismatch between them creates one of the most dangerous forms of documentary information: a comment appears to offer additional knowledge but describes a previous program state.

An outdated comment can be more dangerous than a missing one.

When an explanation is absent, a participant knows that the meaning must be recovered from other sources.

When a confidently worded but outdated explanation sits beside the code, it receives high local priority and may create a false model of the system.

This is especially important for AI. A natural-language explanation immediately beside the fragment being changed is a strong contextual signal. If it conflicts with the implementation, the model must independently discover the conflict and decide which source to trust.

A comment should therefore be treated as part of the project's maintained state.

Changing code requires checking related explanations just as it requires checking tests, contracts, and documentation directly associated with the changed behavior.

This does not mean that every changed line of code must change a comment. It means that retaining a comment makes a claim: **this explanation still applies to the current implementation**.

### Why Code Should Not Preserve an Agent's History

In traditional development, people rarely tried to comment every step they took because producing such text required additional effort.

AI removes that natural economic boundary.

A model can almost instantly produce dozens of comments explaining exactly what it changed. On superficial inspection, the result looks like a well-documented project.

In reality, this practice mixes three kinds of information:

the current organization of the system;

reasons required to understand the current solution;

the executor's action history.

The first two sometimes belong in the code's local context. The third almost never does.

Information about which agent made a change, the request it received, which files it first changed incorrectly, and which intermediate solutions it tested may matter for audit, reproducibility, or process analysis. Those needs call for a separate execution log, change history, or another form of [project memory][g-project-memory].

An agent's identity should not automatically become a source-code comment either.

If change provenance matters to trust, it should be preserved with the corresponding action and result in the auditable loop discussed earlier in CHLOYA. Adding a single `generated by ...` line inside a file does not provide complete traceability and clutters the system's working representation.

Agents should therefore be prohibited not from commenting as such, but from **automatically turning their own work process into permanent product documentation**.

### Change History as a Separate Layer of Knowledge

Some information about a program's provenance is naturally preserved by version control.

Commits, differences between versions, authorship, and temporal sequence make it possible to determine when a fragment arose, which elements changed together, and how the system evolved.

An empirical study by Codoban et al. demonstrates how important this information is in practice. In a survey of 217 developers, 85% regarded a software project's history as important to their work, and 61% consulted it several times a day or more. Developers used history to discover reasons for existing solutions, reconstruct requirements, analyze change impact, and understand current work [408].

This supports an important proposition: history is an independent source of knowledge that current code cannot replace completely.

The reverse is also untrue.

Having Git history does not mean a project automatically has a complete memory of its decisions.

Change history primarily records a sequence of changes. A decision's rationale may be distributed across task text, discussion, several commits, experimental results, and the knowledge of the people who performed the work.

Research by Al Safwan, Elarnaoty, and Servant shows that developers regularly need to reconstruct change rationales and that rationale itself includes many elements: purpose, necessity, constraints, alternatives, the selected option, dependencies, verification, side effects, and other information. In complex cases, finding that rationale can take substantial time, and developers sometimes abandon the search without finding an adequate answer [409].

Change history therefore primarily answers the question:

**how did the system move from one state to another?**

It does not necessarily provide a compact answer to another question:

**why was this particular state considered correct?**

The second question requires a layer of preserved project knowledge.

### Project Memory as Curated Long-Term Knowledge

CHLOYA calls this layer **[project memory][g-project-memory]**.

[Project memory][g-project-memory] is not an archive of every message, document, and action that occurred in the project.

Simply preserving all available material replaces the loss-of-knowledge problem with a search problem. The next participant must once again study large amounts of history, determine which information remains current, and separate decisions from options that were discussed but rejected.

Such an archive increases available context without necessarily increasing required and sufficient context.

[Project memory][g-project-memory] should therefore be a **curated and maintained external representation of durable project knowledge**.

It is appropriate to transfer information into it when that information:

has no natural canonical representation directly in code or other formalized artifacts;

must survive the current session, task, or particular executor;

could materially change a future participant's decision;

would be disproportionately expensive to reconstruct from the project's complete history.

This often includes reasons for architectural decisions, constraints that existed, rejected alternatives, known trade-offs, assumptions about the external environment, and applicability limits of the selected approach.

The idea of preserving such knowledge has a substantial history in software-architecture research.

Tang, Babar, Gorton, and Han showed that practicing architects recognize the value of preserving design rationale, especially for later modification and impact analysis, even though such information remains incompletely documented in practice [406].

Jansen, Avgeriou, and van der Ven treat architectural knowledge as a separate object of management and emphasize the problems of losing, finding, and tracing such knowledge in large systems [407].

CHLOYA's [project memory][g-project-memory] thus continues an established line of design- and architectural-knowledge management while extending it to the human–agent working loop.

The future developer is no longer the only consumer of preserved rationale.

It may be another AI agent, a new model instance, a verification agent, a maintenance agent, or the original executor after its current context has been lost.

### Project Memory Should Not Duplicate Code

It does not follow that [project memory][g-project-memory] should contain a detailed description of the entire system.

That approach would again create two competing representations of one state.

If a function signature, dependency version, data-schema structure, or interface parameter set is unambiguously determined by a canonical [machine-interpretable artifact][g-machine-interpretable-artifact], manually copying it into [project memory][g-project-memory] usually reduces reliability rather than increasing it.

After the next change, the code becomes the new state of truth while the textual copy may remain unchanged.

[Project memory][g-project-memory] should therefore **refer to canonical state rather than reproduce it** wherever possible.

Code answers what is implemented now.

A contract records the external mode of interaction.

A test expresses a verifiable expectation.

Change history shows the trajectory of transformations.

[Project memory][g-project-memory] preserves knowledge that cannot be obtained reliably from those representations alone.

This division reduces duplication while making each artifact's responsibility predictable.

### Not Every “Why” Belongs in Project Memory

The boundary between a comment and memory is not determined simply by the question “why.”

Some reasons must be known while reading a particular area of code.

For example, an unusual sequence of operations may be required because of a defect in an external library. If a future executor who does not know this constraint is very likely to “simplify” the implementation and restore the defect, a short local explanation is justified.

A detailed history of discovering the defect, the list of libraries tested, links to experimental branches, and discussion of alternatives need not sit beside every implementation line.

This is why a comment and [project memory][g-project-memory] may be linked.

A comment contains the minimum locally necessary explanation:

> the operation order is retained because of constraint X; see decision ADR-017.

The decision record contains broader context:

the problem that occurred;

the evidence obtained;

the options considered;

why the current option was chosen;

the condition under which it may be reconsidered.

Local context remains compact while deeper knowledge remains discoverable.

This arrangement directly supports the [contextual self-sufficiency][g-context-self-sufficiency] discussed in 9.3.

### A Decision Record as a Unit of Memory

One practical form of such preservation is an **[architecture decision record][g-adr]** (ADR).

ADRs record a particular decision together with its context and rationale, preserving architectural knowledge alongside an evolving project.

A 2024 action-research study by Ahmeti et al. found that introducing such records helped a team develop its documentation culture, transfer knowledge, and determine which information to preserve. The authors also found that documentation location materially affects perceived usefulness and that a single centralized storage approach does not suit every kind of distributed knowledge [410].

For CHLOYA, this finding aligns with [contextual self-sufficiency][g-context-self-sufficiency].

[Project memory][g-project-memory] need not exist in one global file.

Excessive centralization risks turning memory into another context monolith.

Some decisions apply to the whole project. Others belong to a particular component. Some constraints make sense only for one external interface.

Memory must therefore retain scope and discoverable links to the artifacts to which the preserved knowledge applies.

### Memory Must Preserve the Status of Knowledge, Not Only Text

Preserving a statement is not enough for an agentic system.

Its kind must also be understood.

The statement:

> library X is unsuitable for our use case

may represent several different knowledge states.

It may have been confirmed by a reproducible experiment.

It may be one developer's conclusion about an old library version.

It may apply only to a particular platform.

It may be a temporary hypothesis that no one has verified.

If [project memory][g-project-memory] preserves only the text, these distinctions disappear. The next agent receives a statement without information about the strength of its basis and may interpret a hypothesis as a prohibition.

Memory must therefore inherit CHLOYA's earlier rules for trusted context.

For material information, provenance, scope, verification status, currency, and known uncertainty should be preserved wherever possible.

Transferring a statement to the next executor must not automatically increase its trust level.

If a previous agent proposed a cause but did not verify it, [project memory][g-project-memory] must preserve an **unverified hypothesis**, not turn it into an established fact.

This is especially important in long agent trajectories, where one erroneous conclusion may be passed repeatedly between subsequent executors and gradually acquire the appearance of stable project knowledge.

### Memory Must Be Able to Become Outdated

[Project memory][g-project-memory] is itself part of an evolving system.

A decision correct today may cease to apply after a change in architecture, an external library, or a business requirement. Memory cannot therefore be treated as a collection of eternal truths.

Deleting an old record is not always desirable either.

When a decision has been superseded, the fact that it once existed may explain part of the project's history and prevent an already rejected alternative from being investigated again.

Changing status rather than erasing the record is therefore a better model.

A decision may be current, superseded, revoked, or due for review. A new record may refer to the previous one and explain why it changed.

This preserves the distinction between:

**what is considered correct now**

and

**what was considered correct before and why that changed**.

This is the same temporal separation of responsibilities already applied to code and comments.

The current participant should be able to discover the present state quickly while retaining a path to its provenance when needed.

### Project Memory and Change History Complement Each Other

Version control is highly complete with respect to changes themselves, but comparatively weakly structured with respect to their reasons.

[Project memory][g-project-memory], by contrast, should be selective. It does not preserve every changed line, but concentrates material rationale.

Traceability between the two is therefore useful.

A decision record may refer to the task or changes that implemented it.

A commit may refer to the decision it implements.

A comment may point to a decision record when local behavior cannot be understood safely without it.

The result is a connected system of artifacts rather than one document, with each artifact preserving its own kind of knowledge.

This also reduces the cost of AI work.

When an agent does not need to reread hundreds of commits or an entire discussion history to understand the reason for one construct, [project memory][g-project-memory] reduces the amount of past context that must be reconstructed.

The saving arises only if memory itself remains compact, current, and addressable.

An unfiltered log of agent actions renamed “project memory” has the opposite effect.

### Principle of Separating Current State from History

The discussion supports another CHLOYA principle, the **[principle of separating current state from history][g-current-state-history-separation]**:

> **an artifact should primarily preserve the kind of knowledge for which it is a natural and maintainable source; the system's current state and the history by which that state arose should not be mixed without need.**

In practice, this means the following.

Code and its structure represent the current implementation.

A comment supplements it with locally necessary current knowledge.

Formalized contracts and tests record properties that can be expressed and verified by machines.

Change history preserves the sequence of transformations.

[Project memory][g-project-memory] preserves curated reasons, constraints, alternatives, and other long-term context needed by future participants.

An audit of agent execution preserves action provenance where trust and control require it.

These representations may refer to one another but should not copy one another's contents without need.

This separation reduces the risk of inconsistency, bounds the size of [required context][g-required-context], and allows the next participant to select the exact layer of knowledge required for the current operation.

This is especially important in human–agent development.

A generative model faces almost no cost in producing additional textual explanations, but every preserved explanation becomes part of the project's future cost. It must be stored, indexed, selected, read, checked for currency, and sometimes supplied to the next model.

Documentation quality in an agentic environment is therefore not determined by the volume of text produced.

The more important measure is the **ratio of preserved knowledge to its future usefulness**.

A well-organized project does not attempt to preserve every agent's entire reasoning process. It materializes only the reasoning results that should influence later actions and places them in the appropriate artifact type.

Code, comments, and [project memory][g-project-memory] therefore form complementary layers of the [shared working surface][g-shared-working-surface], not several copies of the same documentation.

Code shows the existing solution.

A comment helps interpret it correctly where structure is insufficient.

[Project memory][g-project-memory] recovers the grounds for a decision when they are required to change it.

History makes it possible to investigate the path by which the system reached its current state.

Knowledge about an existing solution does not, however, independently prove that solution correct. A comment may claim that an invariant holds. [Project memory][g-project-memory] may explain why it matters. As long as the property remains only a textual claim, satisfaction still depends on human or agent interpretation.

The next step is therefore to move material expectations from the explanatory layer into the layer of independent verification.

Tests, types, contracts, compilers, and other tools considered in the next section perform that function.

[Back to contents](#contents)

## 9.6. Verifiable Properties and the External Verification Loop

The preceding sections treated code and related artifacts as ways to preserve and transfer system state. Program structure narrows the space of admissible interpretations, comments supply [locally necessary knowledge][g-locally-necessary-knowledge], and [project memory][g-project-memory] preserves reasons and constraints that cannot be recovered reliably from the current implementation.

Understanding a result and demonstrating its properties, however, are different tasks.

An executor may correctly explain how it changed a system, offer a persuasive rationale for its chosen solution, and report that the work is complete. None of these statements by itself establishes that the resulting state actually has the required properties.

This distinction is fundamental to human–agent development.

AI can generate an implementation and also produce a confident account of its correctness. It may say that the program compiles, the tests pass, the interface remains compatible, the defect has been eliminated, and the new functionality meets the requirement. Yet the executor's textual confidence remains an output of the same probabilistic process that participated in constructing the solution.

An agent's statement about a result therefore cannot be treated as independent confirmation of that result.

This limitation is not specific to AI. Much of the history of software engineering concerns attempts to separate writing a program from establishing its properties. As early as 1969, Hoare proposed an axiomatic approach for reasoning about programs through formally specified preconditions and postconditions and proving program properties relative to those conditions [411].

For CHLOYA, the important point is not the particular mathematical apparatus, but the underlying idea:

> **an executor's claim about a property of a result must be distinguished from independently obtained evidence of that property.**

Another limitation follows directly.

What is verified is not “the correctness of the program as a whole.”

What is verified is a **particular property**.

Successful compilation establishes one class of properties; a type system establishes another. A static analyzer can detect or exclude certain states within its model. A test checks observed behavior against specified conditions and an expected result. Formal verification can establish much stronger claims, but only relative to an explicitly defined model and assumptions.

Statements such as “the code has been verified” or “all checks passed” therefore have limited informational value unless they identify the kind of verification performed.

A more precise question is:

**which property was verified, by which mechanism, under which conditions, and against which system state?**

### Verifiable Property

CHLOYA uses the concept of a **[verifiable property][g-verifiable-property]** to describe this boundary.

> **A [verifiable property][g-verifiable-property] is a property of a result or system state for which a sufficiently definite criterion exists, allowing a software or formal tool to establish satisfaction, violation, or—for some forms of analysis—the inability to reach an unambiguous verdict.**

A property may be very narrow.

For example, a program conforms to the syntax of the language in use.

A value belongs to a particular type.

A function returns a particular result for a given input.

An observed trace contains no prohibited state.

A migration preserves a particular data invariant.

An interface remains compatible with a specified schema.

None of these claims is a complete assertion about the correctness of the entire system. Each can nevertheless be established independently by a suitable mechanism.

This approach avoids the false binary distinction:

**verified / unverified.**

It replaces it with a set of individual claims about system state, each with its own verification basis.

### A Type System as Bounded Automatic Verification

Section 9.4 considered types as part of [structural context][g-structural-context]. They can convey material information about admissible values and relationships between entities.

Section 9.6 considers another aspect of a type system: its ability to reject certain classes of programs automatically.

Pierce defines a type system as a tractable syntactic method for proving the absence of certain program behaviors by classifying phrases according to the kinds of values they compute [412].

The word **“certain”** is especially important here.

A type system does not establish that a program implements the required business logic. It does not prove an algorithm correct or guarantee the absence of every possible defect.

It narrows the space of admissible programs and thereby excludes certain classes of erroneous state before execution.

For CHLOYA, this is a useful example of a bounded verification mechanism.

If an agent says that it supplied a function with a valid value, the statement may remain part of its reasoning.

If the constraint is represented in the type system and has actually passed compiler checking, independent evidence of a stronger class becomes available.

This is not because a compiler “understands the task better than the agent,” but because the particular property has been externalized into a mechanism whose operation does not depend on the executor's confidence.

### Static Analysis and Partial Knowledge of Behavior

Static analysis plays a similar role.

The classic abstract-interpretation theory of Cousot and Cousot shows how properties of actual computations can be studied through a simpler abstract representation of their possible behavior [413]. Abstract analysis can obtain useful information about a program without executing every possible trajectory, although by its nature the result may be incomplete or conservative.

This highlights another important property of external verification.

A verification mechanism need not return only two answers:

**true / false.**

In some cases, the correct result is:

**the property is confirmed;
a violation has been found;
the available data is insufficient for a conclusion.**

This is especially useful in an agentic system because it prevents another form of false confidence. If static analysis cannot prove the absence of a problem, that does not automatically establish a defect. Conversely, failure to detect a violation does not necessarily prove the absence of an error outside the analyzer's model.

[Verification evidence][g-verification-evidence] must therefore preserve not only a positive or negative result, but also the boundaries of what that result means.

### Verification Scope

CHLOYA introduces **[verification scope][g-verification-scope]** for this purpose.

> **[Verification scope][g-verification-scope] is the set of properties, input states, execution conditions, environmental constraints, and assumptions for which a particular verification mechanism can produce meaningful evidence.**

[Verification scope][g-verification-scope] determines the meaning of the result obtained.

A successful build does not confirm the correctness of a user scenario.

A passing unit test does not establish correct integration with an external system.

A performance test run on a small dataset does not confirm behavior under peak production load.

Validating a message schema does not prove that the data in the message has the correct business meaning.

Even two mechanisms both called “tests” may have fundamentally different [verification scopes][g-verification-scope].

The number of green indicators is therefore a weak measure of trust in a result.

What matters more is **coverage of material properties by different verification bases**.

### A Test as an Executable Agreement About Behavior

Tests occupy a special place among these mechanisms because they connect behavioral requirements to actual system execution.

In the simplest case, the natural-language expectation:

> under the stated conditions, the system must behave in a particular way

is transformed into an [executable artifact][g-executable-artifact]:

**prepare the input state -> execute the system -> obtain an observable result -> compare it with the expectation.**

In this sense, a test can be treated as an **executable agreement about behavior**.

It performs several functions at once.

For a person, a test can serve as an example of expected system use.

For an agent, it provides a machine-interpretable constraint.

For the execution environment, it automatically determines whether observed behavior meets a specified criterion.

For the next change, it preserves a [verifiable property][g-verifiable-property] that must continue to hold.

The last function makes tests especially important in long-running human–agent development. A natural-language requirement may disappear from the next model's working context. An existing test remains an external artifact and can present the same requirement to every subsequent change.

This arrangement nevertheless has a fundamental limitation.

### The Test Oracle Problem

Executing a program makes its behavior observable, but does not automatically determine whether that behavior is correct.

Barr, Harman, McMinn, Shahbaz, and Yoo call the task of determining whether an observed result is correct the **test oracle problem**. They show that expected behavior may be derived from formal specifications, models, contracts, metamorphic relations, and other mechanisms, yet in many practical situations the final decision still requires human domain knowledge [295].

CHLOYA therefore imposes a fundamental limitation:

> **a test automates verification of a recorded expectation, but does not guarantee that the expectation itself is correct.**

If a requirement was misunderstood when a test was created, automation merely makes the wrong check fast and repeatable.

This again shows why the provenance of a verification condition matters when assessing a result.

An existing regression test created after a confirmed defect and a test generated moments ago by the current agent from the same instruction have different evidentiary strength even if both produce the same technical result.

### From Examples to Properties

An ordinary test often records one specific correspondence:

**given input -> expected result.**

A material requirement, however, is often more general.

For example:

sorting must preserve the set of input elements;

serialization followed by deserialization must restore an equivalent value;

a particular transformation must be idempotent;

the sum of the parts must equal the whole regardless of particular values.

Property-based testing makes it possible to state such relationships directly and then explore them automatically over many generated inputs. The classic QuickCheck work by Claessen and Hughes demonstrated a practical approach in which program properties are stated in executable form and input data is generated automatically [210].

The particular tool is not what matters for agentic development.

What matters is the move from a set of individual examples to a **generalized verifiable claim**.

The more closely a test expresses the material property itself, the less likely an implementation is to satisfy several examples accidentally while violating the broader intent.

Property-based testing still does not eliminate the oracle problem. Someone must determine that the selected property actually represents the desired system behavior.

### The Verification Mechanism Must Also Be Checked

If a test is used as a basis for accepting an implementation, another question arises:

**how capable is the test of detecting a violation of the property of interest?**

A test suite may pass not because the program is correct, but because its checks are insensitive to material errors.

Mutation testing offers one way to assess this sensitivity. Small artificial changes are deliberately introduced into the program, after which the existing test suite is checked to see whether it detects them. A modern survey by Papadakis et al. treats mutation analysis as a mature way to assess test-suite adequacy and support other testing tasks [414].

For CHLOYA, the broader idea matters beyond the particular technique:

> **in critical loops, not only a verification result but also the verification mechanism's ability to detect the class of violation of interest must be assessed.**

This can be called second-order verification.

It is not required for every line of code or every small test. As the cost of error increases, however, merely having some verification mechanism is insufficient. Its actual sensitivity to the failures for which it is used must be understood.

### External Verification Loop

This leads from individual tools to a broader architecture.

In CHLOYA, an **[external verification loop][g-external-verification-loop]** is the set of mechanisms that receive a resulting artifact or system state and, independently of the executor's verbal self-assessment, establish particular properties of it.

Such a loop may include:

a compiler;

a type system;

static analysis;

a schema validator;

a contract;

a test suite;

dynamic analysis;

performance verification;

infrastructure-plan verification;

a formal proof;

a specialized domain validator;

human acceptance where a property cannot be formalized sufficiently completely.

What unifies these mechanisms is not their technical implementation, but their **role in the trust architecture**.

They do not create the main solution; they provide independent information about its properties.

### Independence Does Not Necessarily Mean a Second Agent

In a human–agent system, it is natural to assume that independent verification can be achieved simply by assigning another agent.

That is not always true.

Two copies of the same model may share the same systematic errors.

Two agents given the same incorrect statement of a requirement may independently reach the same incorrect conclusion.

Conversely, one agent may write code and then run an existing compiler or test suite created before the current change. Although the same executor is used, the verification basis is separate from its current interpretation of the task.

Verification independence therefore has several dimensions.

First, **operational independence**: a claim must actually be checked by a tool rather than restated by a model.

The statement:

> the build should pass

and an actual successful build execution are different artifacts.

Second, the **independence of the verification basis's provenance** matters.

If the success criterion predates the current implementation or comes from another canonical source—a contract, specification, user acceptance criterion, or known defect—the probability that the same interpretive error produced both the solution and the means of declaring it correct is reduced.

Third, **diversity of verification mechanisms** matters.

Type checking, static analysis, and integration testing observe different system properties and have different blind spots. Together they can provide a stronger basis not because there are quantitatively more checks, but because they establish properties in different ways.

### Verification Created by the Agent Itself

The situation is especially difficult when one agent creates both an implementation and its tests.

At first glance, this approach is natural. If tests do not exist, the model can derive them from the requirement, execute the implementation, and use discovered errors to correct the result.

In practice, this mechanism can indeed be useful.

Tests created by the same executor from the same understanding of the task nevertheless inherit the risk of a shared interpretive error.

In a study of code-model self-correction using self-generated tests, Chen et al. found **self-test bias**: incorrectly formed tests can give a model misleading positive feedback, especially when implementation and verification arise from the same representation of the task [418]. They showed that using intermediate execution state can reduce the problem in part, but the result remains dependent on the quality of self-generated tests.

CHLOYA therefore makes an important distinction.

**A test created by the current agent is a verification artifact, but not automatically an independent verification basis.**

It can detect implementation errors.

It can expand the project's verifiable surface.

It can become a good regression test after separate review.

When assessing completion of the current task, however, the test's provenance must be taken into account.

In critical situations, key [verifiable properties][g-verifiable-property] should be connected to more independent bases: existing tests, user criteria, schemas, contracts, reproducible defect examples, or a separately reviewed specification.

### Changing a Test Together with the Implementation

The same problem yields a practical rule.

If an existing test fails after a system change, automatically changing the test until it passes must not be treated as a neutral operation.

At least three explanations are possible.

The new implementation violated previously required behavior.

The requirement itself was deliberately changed and the old test no longer represents the project.

The test originally contained an incorrect expectation.

Technically, an agent can address any of these situations through the same action: changing the verification code.

Methodologically, they are fundamentally different.

Therefore:

> **changing a solution and the criterion by which the solution is declared correct at the same time reduces verification independence and requires a separate justification.**

This does not prohibit changing tests.

An evolving system necessarily changes both implementation and expected behavior.

A change to a verification artifact must, however, be tied to a changed requirement, a confirmed defect in the test itself, or another external basis—not merely to the desire for a positive result.

For an agentic loop, this is an especially important protection against local optimization for the check.

### Verification as Feedback During Work

External verification is not needed only when a task is completed.

It can participate in the solution trajectory itself.

Modern code-generation systems demonstrate the value of using actual execution as feedback. In LEVER, Ni et al. use execution results from generated programs together with the code and original problem to train a verifier that selects correct candidates more effectively [416].

SWE-agent likewise places test and program execution directly in the interface through which an agent interacts with the computing environment. The authors show that a purpose-designed interface allowing a model to navigate a repository, edit files, and receive execution results materially affects its ability to solve software-engineering tasks [417].

Verification therefore performs at least two distinct functions.

During work, it provides **feedback for searching for a solution**.

After completion, it provides **evidence of particular properties of the resulting state**.

These functions are related but not identical.

A failing test during work helps an agent find an error.

A passing final execution of the same test confirms only that the particular [verifiable property][g-verifiable-property] holds in the final state.

Intermediate execution results may therefore be used by an agent as working context, while final verification must apply to the actual resulting artifact.

### From a Result to Verification Evidence

CHLOYA introduces the concept of **[verification evidence][g-verification-evidence]** for this arrangement.

> **[Verification evidence][g-verification-evidence] is a preserved result of an instrumental or formal check associated with a particular artifact state and confirming, refuting, or leaving indeterminate a particular property within a stated [verification scope][g-verification-scope].**

Evidence may be very simple:

a compiler exit code;

a test result;

an analyzer report;

a validator verdict;

a formal-proof result.

In more critical systems, additional information may be preserved with it:

the tool used;

its version;

the project state checked;

the parameters used;

the environment in which the check ran;

the property it was intended to verify.

The knowledge-provenance rule formulated earlier in CHLOYA must be applied again here.

An agent's message:

> the tests passed

is not equivalent to the test execution result itself.

If a system can obtain a machine report directly from the verification tool, that report should be treated as the primary evidence.

An agent may interpret the result for a person, but its retelling should not replace the original verification artifact where the latter is available.

### Result Plus Evidence

This arrangement has a historical analogue in stricter systems for trusting code.

In Necula's Proof-Carrying Code, an untrusted producer of program code must supply the program together with a proof that it complies with a predefined security policy, and the receiving party independently checks the proof before execution [415].

CHLOYA does not assume that every agent result must be accompanied by a mathematical proof.

The architectural principle is nevertheless much broader than the particular technique:

> **a result from a potentially unreliable executor is accepted not only on the basis of the result itself or the executor's confidence, but together with independently verifiable evidence of material properties.**

For an ordinary software change, the set may be:

**code change + successful build + test results + static-analysis report.**

For a configuration:

**configuration + schema validation + trial application.**

For an infrastructure change:

**declaration + change plan + policy checks.**

For a data migration:

**script + structural validation + integrity checks + postconditions.**

Methodologically, each is an instance of the same pattern:

**artifact + [verification evidence][g-verification-evidence].**

### Evidence Is Not a Certificate of Complete Correctness

This model creates another risk: overestimating the evidence itself.

If an agent reports:

> 412 tests passed,

the number may create an impression of high confidence.

In fact, it means only that 412 particular checks detected no violation in a particular state and environment.

An unknown requirement may still be violated.

The test oracle may be wrong.

An unexplored class of inputs may contain a defect.

The external environment may differ from the test environment.

The verification tool itself may have limitations or errors.

Therefore:

> **[verification evidence][g-verification-evidence] must never be interpreted beyond its [verification scope][g-verification-scope].**

This rule is especially important for automated decision systems. A green result is convenient for machine processing and can therefore easily become a binary admission criterion.

CHLOYA requires more precise semantics to be preserved: exactly which barrier was passed and which properties remained outside it.

### Cost of Error and Strength of the External Loop

Not every change requires the same degree of verification.

A typo in isolated interface text and a change to an authorization mechanism have different potential costs of error.

The depth and independence of the external loop should therefore be proportionate to the consequences of an incorrect result.

For a low-risk action, a local test and ordinary review of the change may suffice.

A critical operation may require several independent mechanisms, separate human confirmation, verification in a specially prepared environment, or formal constraints.

This yields another principle:

> **the higher the cost of error, the stronger the separation should be between the source of a change and the basis on which that change is deemed admissible.**

This separation need not be organizational.

It may be achieved through different kinds of tools, independent specifications, separately defined acceptance criteria, or the verification roles described in earlier CHLOYA chapters.

The essential objective is to reduce the probability that the same mistaken interpretation produces both an action and the mechanism that declares the action correct.

### Verification as Part of the Project's External State

[Verification evidence][g-verification-evidence] has another role in long-running agent work.

It allows executors to transfer not only the assertion:

> the previous agent believes this code works,

but the observable state:

> checks V₁, V₂, and V₃ were actually run against version S₁ and produced these results.

This is substantially more robust than a retelling.

The next executor can determine which properties have already been checked, which checks apply to an earlier state, and which must be repeated after the next change.

Evidence is tied to a particular system state.

After code changes, an old test result does not automatically confirm the new state.

Even when a change appears unrelated to the verified functionality, a decision to reuse evidence must be based on known dependencies, not merely on the existence of a successful check in the past.

The [external verification loop][g-external-verification-loop] thus becomes part of the project's shared external state alongside code, contracts, and [project memory][g-project-memory].

It preserves not a belief in correctness, but a **history of observed results relative to defined states**.

### From Verification to Controlled Change

This changes the model of completing an agent operation.

Obtaining a new file or set of changed lines is insufficient.

An agent's explanation is insufficient.

Even a general “checks passed” status is insufficient.

A more complete representation of the result includes:

the initial state;

the change performed;

the resulting state;

material properties that had to be preserved or introduced;

verification mechanisms;

the evidence obtained;

areas that remain unverified.

This arrangement makes it possible to move from code generation to a **[controlled state transformation][g-controlled-state-transformation]**.

The agent no longer merely creates a new version of a program. It moves the system from one state to another under specified constraints, after which external mechanisms assess whether the transition is admissible.

Section 9.6 thus completes the transition from the codebase as a shared language to the codebase as a verifiable working environment.

People formulate intent and make decisions where a criterion cannot be fully formalized.

Agents create and modify artifacts.

Types, contracts, analyzers, tests, and other mechanisms independently establish the properties available to them.

The resulting evidence returns to people and agents as new external state.

CHLOYA therefore applies the principle:

> **where a property of a result can be established by a software tool, the decision that the property holds must not rely only on the executor's self-assessment.**

This approach neither eliminates uncertainty nor turns every development effort into a formally proven system.

It does something else: it progressively moves available checks from participants' beliefs into observable and reproducible artifacts.

The next step is to combine these elements into one model of system change.

When there is an initial state, a bounded scope of action, a set of invariants to preserve, a resulting state, and [verification evidence][g-verification-evidence], a code change can be treated not as an act of text generation but as a **[controlled transformation of project state][g-controlled-state-transformation]**.

The next section develops this model.

[Back to contents](#contents)

## 9.7. Code Changes as Controlled State Transformations

The previous section showed that an agent's result cannot be assessed solely by its own claim that a task is complete. Where result properties permit instrumental verification, external verification mechanisms must be used and the evidence obtained must be associated with a particular system state. This supports a broader conclusion: a code change cannot be treated as an isolated act of text generation either.

A coding agent almost never creates a system from nothing in an empty space. It receives an existing project in some state, analyzes it, changes a bounded set of artifacts, and passes on a new state. Even creating a new file usually occurs within an existing project structure and depends on its interfaces, dependencies, conventions, tests, and architectural constraints.

The natural unit of agent work is therefore not a generated file or an individual model response, but a **transition between project states**.

In its simplest form, such a transition can be represented as

$$
S_0 \xrightarrow{\Delta} S_1,
$$

where \(S_0\) is the initial state, \(\Delta\) the applied change, and \(S_1\) the resulting state actually obtained.

This notation appears simple, but fundamentally changes the object being governed. If only the new code is treated as the result, many conditions of the operation remain implicit. It is unclear which project version the change was constructed against, which properties had to be preserved, which elements could be modified, how far the operation's consequences extend, and how it was established that state \(S_1\) actually meets the goal.

For CHLOYA, a transition between states must therefore be considered together with intent, constraints, and verification.

Research on program transformation provides a historical basis for this view. Visser defines program transformation as mechanically changing a program, making the program itself the object of processing, while a complex transformation may be constructed as a sequence of simpler rules [421]. The program here is not only text intended for execution, but also state to which a transformation is applied.

The classic research tradition on refactoring is especially close to the issue at hand. Opdyke's dissertation describes refactorings as program transformations intended to change structure while preserving behavior; whether individual transformations may be applied depends on corresponding preconditions [419]. Later refactoring research systematized questions of behavior preservation, applicability conditions, and transformation automation [420].

CHLOYA does not reduce every change to refactoring. When a new function is implemented, a defect is corrected, or a requirement is deliberately changed, system behavior is expected to change. Refactoring research nevertheless supplies a broader principle: **a change operation has applicability conditions and a set of properties that must either be preserved or changed in a specified way**.

This extends the initial transition model.

Let \(G\) denote the change goal, \(C\) the applicable constraints, and \(I\) the properties that must remain invariant. The operation is no longer an arbitrary transition between states. It must produce an \(S_1\) that implements the required change without violating preserved constraints.

Some properties are expected to be preserved:

$$
I(S_0)=true \Rightarrow I(S_1)=true.
$$

For others, the purpose of the change is precisely to introduce a new property:

$$
P(S_0)=false,\qquad P(S_1)=true.
$$

When a defect is corrected, the inverse may apply: an observed undesirable property existed in the initial state and must be absent from the resulting state.

A change is therefore defined not by the number of modified lines, but by the **semantics of the transition between states**.

### The Initial State as Part of a Change's Meaning

A [change artifact][g-change-artifact] does not exist independently of its initial state.

The same textual patch applied to two different system versions may have different meaning, fail to apply, or produce different results. Even if the technical mechanism can apply the change without conflict, that does not mean the assumptions against which the change was designed remain valid.

For example, an agent may study a component interface and prepare a correct change to one of its consumers, while another participant changes the interface before the change is applied. The textual diff may remain technically applicable even though the original basis of the solution has changed.

A controlled transformation must therefore make it possible to determine **the state against which a change was formed**.

In version control, this naturally connects to a particular commit or tree state. For a data schema, the basis may be a particular schema version; for configuration, a particular revision; for an external system, the observed state against which an effect plan was constructed.

This creates a temporal relationship between artifacts: a change applies to a particular \(S_0\), while the [verification evidence][g-verification-evidence] from 9.6 applies to a particular \(S_1\). After another change, previous evidence cannot automatically be treated as evidence for the new state.

### Change Artifact

In this approach, the representation of the transition itself acquires independent value.

In traditional version-control work, a difference between states often performs this function. It allows a person to see not only the final file, but exactly which elements were added, removed, or modified.

This is especially important in agentic development. If an executor returns only the resulting file, the next participant must independently compare it with the preceding state and reconstruct the transformation's meaning. A representation of the change makes that meaning much more local.

A [change artifact][g-change-artifact] need not be an ordinary line-based diff.

Research on automated program evolution shows that a change itself can be expressed at a higher level. Padioleau, Lawall, Hansen, and Muller studied collateral changes to Linux drivers caused by the evolution of internal kernel interfaces. They used Coccinelle semantic patches to document and automate them, expressing not a concrete set of lines in one file but a transformation rule applicable to related areas of a program [424]. This automation was motivated in part by the fact that manually performing many dependent changes was labor-intensive and produced inconsistent modifications.

CHLOYA therefore uses a broader concept of a **[change artifact][g-change-artifact]**.

A [change artifact][g-change-artifact] represents a difference or transformation rule between a known initial state and an intended result. It may be an ordinary version diff, a database migration, a rule for transforming program structure, an infrastructure plan, or another formalized description of a transition.

Such an artifact becomes part of the [shared working surface][g-shared-working-surface]. A person can assess its meaning, an agent can construct or modify it, and software tools can apply and verify it within their supported semantics.

### The Smallest Change Is Not Always the Right Change

When coding agents are used, it is natural to limit change size. The smaller the affected area, the easier the result is to review, the lower the probability of unintended effects, and the cheaper subsequent verification becomes.

This does not support a universal rule that “the smaller the change, the better.”

A local correction may remove a symptom while leaving architectural integrity violated. An interface change may require all its consumers to be updated. A new schema constraint may require existing data to be migrated. If change size is held artificially small, the resulting state may be internally inconsistent.

The opposite extreme is equally dangerous. A generative agent can easily expand the original task to include unrelated refactoring, renaming, formatting changes, or dependency upgrades. The [change impact scope][g-change-impact-scope] grows, verification becomes more difficult, and it becomes harder to determine which transformation produced an observed effect.

CHLOYA therefore applies not a principle of minimal change, but the **[principle of minimally sufficient change][g-minimally-sufficient-change]**.

> **A change must include every element required to reach the target state and reconcile material consequences, but must not include transformations unrelated to the goal, dependencies, or the need to preserve required properties.**

Minimality here refers not to the number of lines or files, but to the semantic scope of the operation.

A change to twenty files may be minimally sufficient when all are consumers of a changed interface. A two-line change may be excessive when one line is unrelated to the task.

### Editing Scope and Change Impact Scope

The [principle of minimally sufficient change][g-minimally-sufficient-change] yields an important distinction.

The **permitted editing scope** identifies which parts of the system an executor is authorized to change directly.

The **[change impact scope][g-change-impact-scope]** identifies which system elements and properties may be affected by the consequences of the change.

The two scopes need not coincide.

Changing one function may affect many callers. Changing a shared type may affect every component that uses it. Changing a data schema may affect software code, migrations, reports, and external integrations. Modifying an infrastructure declaration may affect real resources that are not represented by individual repository files at all.

The need to investigate such consequences gave rise to change-impact analysis. A systematic study defines Change Impact Analysis as examining the potential effects of a change in other parts of a system; its review of 111 papers connects such analysis to lower maintenance cost and failure risk [423].

This distinction is especially important to CHLOYA because agent authority is bounded.

Restricting editing scope is a safety mechanism. It must not automatically be interpreted as a claim that the consequences of a change are also confined to that scope.

If an agent discovers that a correct operation requires changes beyond its authority, it has two fundamentally different options. It can cross the boundary covertly and expand the transformation on its own, or stop that branch of action and transfer the discovered dependency to a level able to change its authority or reconsider the task.

CHLOYA permits the second response.

> **An authority boundary limits an executor's admissible action, but must not limit its analysis of that action's possible consequences.**

This preserves control of the operation without replacing safety with an artificially local view of the system.

### Impact Analysis as Part of Change Preparation

The [change impact scope][g-change-impact-scope] should be identified before the actual change to the extent practical.

Completely predicting every consequence of a nontrivial change is often impossible. Available structural relationships, dependencies, types, call graphs, tests, schemas, and [project memory][g-project-memory] can nevertheless support a working estimate of the expected impact surface.

This again connects 9.7 to [contextual self-sufficiency][g-context-self-sufficiency] from 9.3 and [structural context][g-structural-context] from 9.4. The better a system reveals its own dependencies, the easier it is to determine which elements must be investigated before a transformation.

Impact analysis need not end in an exact list of all consequences. It may include explicitly marked uncertainty. For a trusted loop, knowing that impact on a particular area could not be determined is more useful than receiving a confident but unfounded claim of independence.

Uncertainty thereby becomes part of the operation's state rather than a hidden weakness in the executor's reasoning.

### Project State Is Broader Than Changed Files

Up to this point, the notation \(S\) may have suggested that state is simply repository content. For many software tasks, that model is insufficient.

A software system exists in several representations at once.

Changing a dependency file changes the set of external components participating in the build. A database migration concerns not only the migration script's text, but also the schema and data state to which it is applied. A change to a declarative infrastructure description may create, replace, or remove external resources. Generated code may require the source definition and derived artifact to remain synchronized.

CHLOYA therefore treats operation state as neither the entire potentially observable system nor merely a set of files, but as **the part of project state and the related environment that is material to the particular transformation and assessment of its result**.

This preserves the principle of sufficiency used earlier.

For a small local change, the relevant state may nearly coincide with code, tests, and direct dependencies.

For a data or infrastructure change, it necessarily extends beyond the repository.

This distinction is especially important for agents because the technical ability to change a textual artifact does not mean that actual external state has already been brought into the corresponding form.

Changing a declaration and changing reality are two different transitions when a separate application operation lies between them.

### Transformation Reversibility

This broader understanding of state makes another property material: change reversibility.

For an ordinary source-file change, returning to the previous version is often comparatively simple. Version control preserves the earlier state and allows it to be restored.

External state does not always behave this way.

Deleted data may be irrecoverable. A migration may lose information. An external call may cause an action that cannot be undone by an inverse request. Infrastructure deployment may change resources that carry their own state.

Reversibility must therefore be assessed **before a change is applied**, not after an adverse result occurs.

When a transformation is reversible, a rollback path may be part of an admissible execution strategy. When an action is irreversible or only partly reversible, stronger requirements apply to prior verification, authority scope, and human control. When a compensating action is available instead of an inverse transformation, it must be treated as a separate operation with its own conditions and risks.

This explains why software artifacts of the same size may require fundamentally different levels of control depending on the real transformation they initiate.

### Semantic Integrity of a Change

An operation's manageability depends not only on its size, but also on its semantic coherence.

A good [change artifact][g-change-artifact] should make it possible to state which transition it represents. Every material element should be explained by one goal or by unavoidable consequences of that goal.

If one transformation corrects an authorization defect, reorganizes an unrelated logging subsystem, and upgrades a third-party library unnecessarily, it becomes harder to establish a causal relationship between change and result. Review, reuse of verification evidence, regression diagnosis, and partial rollback all become more difficult.

Semantic integrity is therefore a more useful criterion than mechanical atomicity.

One semantic operation may affect many files and components. Conversely, one changed file may contain several independent transformations.

This is especially important in agentic development because a model can produce additional changes with almost no subjective sense of cost. A large unrelated refactoring takes a person time, while a generative system can technically include it in the same pass. Operation boundaries must therefore be defined by the goal, not by the generator's convenience.

### A Modern Coding Agent Already Works with State Transitions

The evolution of AI evaluation for software engineering shows a similar change in the unit of a task.

SWE-bench is not centered on generating one function from a short description. A model receives a real codebase and an existing issue, then must change the codebase so as to resolve the issue. The original SWE-bench dataset contains 2,294 tasks derived from real GitHub issues and corresponding changes in twelve Python repositories; solutions often require coordinated changes across multiple functions, classes, and files [70].

Methodologically, the form of the task itself is especially important:

**known repository state + problem description -> change -> new state -> verification execution.**

This is much closer to the real work of a coding agent than the classic “prompt -> code fragment” model.

CHLOYA develops this arrangement further because merely obtaining a patch is insufficient. The basis of the initial state, the executor's authority, the expected [change impact scope][g-change-impact-scope], preserved properties, and the provenance of verification evidence must also be considered.

### An Applicable Patch Is Not Automatically a Correct Transition

Representing a change as a separate artifact creates a risk of focusing on properties of the patch itself.

A change may be small, syntactically valid, well formatted, and apply cleanly to the initial state. That does not mean the resulting state meets the actual requirement.

This problem is well known in research on automated program repair. A survey of methods for evaluating automatically generated patches emphasizes that passing an available test suite is insufficient to declare a patch correct automatically: incomplete tests allow patches to satisfy existing checks without matching the expected repair semantics [425].

This directly extends the conclusions of 9.6.

What is verified is not the quality of \(\Delta\) as text in itself, but the properties of state \(S_1\) after it is applied.

A small, tidy set of changes is therefore not the ultimate goal. The goal is a controlled transition to a state in which the required property has appeared, necessary invariants remain, and no inadmissible consequences have been detected within the verification performed.

### Change Contract as an Operation Model

The elements considered above support a more complete representation of an agent operation.

It has an initial state and a goal for which that state must change. The executor has authority and known constraints. Some properties must be preserved and others changed. After execution, there is a resulting state and external evidence associated with it.

This set can be treated as a **[change contract][g-change-contract]**.

A [change contract][g-change-contract] is not necessarily a separate file and is not the same as Design by Contract. It is a methodological model that combines the material conditions of one operation.

In simplified form:

$$
C_{\Delta}=(S_0,G,A,I,P,V),
$$

where \(S_0\) is the initial state, \(G\) the goal, \(A\) the scope of effects the executor is authorized to cause, \(I\) the properties to preserve, \(P\) the properties to change or introduce, and \(V\) the available verification mechanisms.

In a real project, these elements need not be stored together. The goal may reside in a task, authority may be determined by the agent architecture, invariants may be expressed by contracts and existing tests, and verification mechanisms may be defined by the project's workflow.

The point of the model is not to create another mandatory document, but to treat these conditions as parts of **one operation** rather than unrelated elements of the agent's environment.

The result can be represented similarly after execution:

$$
R_{\Delta}=(S_0,\Delta,S_1,E,U),
$$

where \(E\) denotes the [verification evidence][g-verification-evidence] obtained and \(U\) the material properties or [change impact scopes][g-change-impact-scope] that remain unverified or indeterminate.

The last element is fundamental.

Correct completion of an agent operation does not require creating an appearance of certainty where none exists. If tests confirm the target behavior but effects on a particular external integration were not investigated automatically, that boundary must be passed to the next participant as part of the result.

The controlled transformation thereby becomes both verifiable and honest about its own limits.

### Controlled State Transformation

The discussion yields a final definition.

> **A [controlled state transformation][g-controlled-state-transformation] is a model of change in which an identifiable initial project state is moved through a bounded and semantically coherent transformation to a resulting state relative to a defined goal, authority, and preserved properties, after which the transition's admissibility is assessed by an [external verification loop][g-external-verification-loop].**

This representation differs substantially from a simple generation model.

An agent does more than produce new code. It acts **relative to an existing state**.

Its action has boundaries.

The change has a discoverable [change impact scope][g-change-impact-scope].

Some properties must be preserved.

The result is associated with [verification evidence][g-verification-evidence].

Uninvestigated properties do not disappear; they remain explicitly identified uncertainty.

The unit transferred between participants is therefore not a message saying “task complete,” but a reproducible transformation whose initial basis, change content, resulting state, and known degree of verification can be established.

This approach also reduces [context debt][g-context-debt]. The next agent does not have to reconstruct everything the previous executor did from conversation history. Much of that knowledge is materialized in the initial state, [change artifact][g-change-artifact], resulting state, and associated evidence.

The model also makes it easier to control the cost of agentic development. The broader the unrelated set of changes, the more context must be reanalyzed and the wider the [verification scope][g-verification-scope]. Constraining a transformation to a substantive goal reduces not only risk, but also the computational cost of subsequent stages.

Code finally ceases to be treated as text that an agent periodically rewrites in response to a person's instruction.

It becomes part of mutable state, and the agent becomes an executor of bounded transitions between such states.

Even a well-defined operation, however, assumes that the executor already has sufficient knowledge of system behavior. In real development, that condition often does not hold. Documentation may be incomplete, code ambiguous, and external-environment behavior unknown until actual interaction occurs.

In such a situation, an agent cannot rely only on reading preserved project representations.

It must be able to **acquire new knowledge about the system by observing its execution**.

The next section turns to execution as a means of investigating and understanding a software system.

[Back to contents](#contents)

## 9.8. Execution as a Way of Understanding Code

The preceding sections treated program execution mainly as part of result verification. When an expected system property has already been formulated, running a test, executing an analyzer, or applying another verification mechanism can produce external evidence of whether that property holds under specified conditions.

Execution also has another function.

Before a change begins, an executor often lacks enough knowledge of the system to formulate the right transformation. Code may be complex, documentation incomplete, the actual environment different from the assumed one, and an observed error open to several plausible explanations. Static reading of source code and [project memory][g-project-memory] may then be insufficient.

Executing the program becomes not only a way to test an existing claim, but also a way to **acquire new knowledge about the system**.

This distinction is fundamental.

In verification execution, the question is known in advance: does property \(P\) hold?

In [exploratory execution][g-exploratory-execution], the executor does not yet have a sufficient behavioral model and attempts to determine what happens in the system, which elements actually participate in the observed behavior, which conditions affect the result, and which of several hypotheses best fits actual execution.

Investigating programs through observed execution has a long history. A systematic review by Cornelissen et al. shows that dynamic analysis is widely used specifically to understand existing programs. The authors selected 176 studies of program comprehension through execution analysis and systematized methods in which actual-behavior data helps developers reconstruct a software system's organization [426].

This extends the earlier account of context.

Structural analysis shows which relationships and trajectories **may** exist according to the program's current organization. Observing a particular execution shows which actually appeared for the given system state and input.

Dynamic program slicing makes the distinction especially clear. Agrawal and Horgan contrast a static slice, which contains statements that could potentially affect a value, with a dynamic slice containing the statements that actually affected that value in a particular execution with a particular input [427].

Execution can thereby narrow the area of investigation dramatically.

Instead of analyzing every potential path, an agent can determine which functions were actually called, which branches executed, which values passed between components, and at which stage the state of interest arose.

This is especially important in human–agent development. A large volume of available code does not mean that all of it is equally relevant to the current problem. Actual execution data can select context in addition to the structural relationships discussed earlier.

Simply observing a system run does not exhaust the use of execution as a source of knowledge.

A stronger form appears when execution is used to test an investigative hypothesis.

Suppose an observed error has several possible explanations. The executor hypothesizes that a particular cache state, input value, or intermediate operation is responsible. Rather than immediately changing the production implementation, it can create controlled conditions, execute the system, and compare the observed behavior with the expected consequence of its hypothesis.

The program then becomes not only an object of reading, but an **object of experiment**.

Delta debugging is a classic example. Zeller and Hildebrandt proposed systematically changing the conditions under which a failure is reproduced and repeating execution, gradually reducing the set of factors necessary for the problem to occur [428]. In one example, a sequence of 95 user actions was automatically reduced to three actions that preserved the failure, while an 896-line HTML input was reduced to one line sufficient to reproduce the error.

What matters here is not the particular minimization algorithm, but the way knowledge is obtained.

A cause is not merely inferred by reading the program. The system is subjected to a series of controlled interventions, and differences between successful and unsuccessful runs are used to narrow the space of possible explanations.

In later work, Zeller applied similar reasoning to internal states of a running program. Systematically manipulating differences between successful and failing executions can isolate values and states associated with failure development and construct a causal chain from the initial condition to the observed error [429].

This approach is especially important for an agent executor because it counters one of the most dangerous automated-change strategies: fixing the first plausible explanation.

A large language model can form a hypothesis about an error's cause quickly. A plausible hypothesis, however, need not match the system's actual state.

If the first hypothesis is immediately turned into a code change, the change itself begins to act as an investigation. The agent modifies the system, runs it, observes the result, and uses that result to decide whether the original idea was right. This can sometimes be effective, but it mixes knowledge acquisition with a production state transformation.

CHLOYA prefers to distinguish these operations where the cost of an incorrect intervention is material.

The executor first forms a hypothesis.

Then, where possible and justified, it obtains an external observation capable of supporting, weakening, or refuting that hypothesis.

Only after material uncertainty has been reduced sufficiently is a production change formed.

The process can be represented as a repeated exploratory cycle:

$$
K_t \rightarrow H_t \rightarrow X_t \rightarrow O_t \rightarrow K_{t+1},
$$

where \(K_t\) denotes current knowledge of the system, \(H_t\) an investigative hypothesis, \(X_t\) the experiment performed, \(O_t\) the observation obtained, and \(K_{t+1}\) the refined state of knowledge.

The cycle may repeat several times.

An observation from the first execution may change the question rather than answer it. An agent suspects a storage-layer error, but a trace shows that the incorrect value appears before storage is accessed. The initial hypothesis is discarded, the investigation scope narrows, and a new hypothesis and experiment follow.

In this sense, execution is not only a source of answers, but a mechanism for **restructuring the working model of the system**.

Recent work on coding models already uses such cycles. LeDex uses actual execution feedback to train models to explain errors sequentially and refine previously created code. Execution results allow the model to move beyond its initial solution and continue iterative correction [430].

CodeTree develops a similar idea as managed search. Different strategies and candidate solutions are explored in sequence, while decisions to expand, refine, or stop the search use both model feedback and environment execution results [431].

The coding agent's interaction with a project thus ceases to be a one-way process of reading and writing files.

The environment begins to answer the executor through its own behavior.

Code provides structure and possible dependencies. The compiler reports formal violations. A test reveals a mismatch with an expectation. Execution provides traces, values, and errors. The agent's next action is determined not only by the initial textual instruction, but also by the system's observed response.

An industrial study of agentic program repair from failing tests also demonstrates the value of this combination. Maddila et al. describe an agent loop in which the model receives the initial failure and uses static-analysis and test-execution results as feedback while constructing and refining a repair [432].

Execution can therefore be treated as a mechanism for reducing uncertainty before a [controlled state transformation][g-controlled-state-transformation].

This possibility should not produce the opposite extreme, in which every lack of understanding is addressed automatically by running more experiments.

Execution also has a cost.

Running a project may require a build, environment preparation, a database, a virtual machine, external services, or a substantial test dataset. A complex integration check may cost far more than reading several related functions. In an agentic system, the cost of model analysis of the result is added to the cost of execution.

Static investigation and experimental execution are therefore complementary, not competing, ways of acquiring context.

In one situation, a few minutes examining structural dependencies provides a sufficiently strong basis for a decision.

In another, one short experiment can eliminate many plausible hypotheses whose static investigation would require far more context.

The choice of investigative action should therefore consider not the mere possibility of execution, but the expected value of the information obtained.

In practice, an experiment is especially justified when it can substantially reduce uncertainty about a decision at acceptable execution cost and risk.

This connects [exploratory execution][g-exploratory-execution] to the economics of agent work. [Context debt][g-context-debt] may force a model repeatedly to read and compare large portions of a project. In some cases, a small diagnostic run is a cheaper way to acquire missing knowledge. In others, preparing a complex environment costs more than targeted static analysis.

A mature agentic loop must therefore choose not only **what to investigate**, but also **which means of obtaining the required knowledge is justified**.

Data from one execution must not automatically become a universal claim about the system.

Dynamic analysis derives its strength from the specificity of the observed trajectory. The same specificity limits how far the result can be generalized.

If function \(A\) called \(B\) for one input while branch \(C\) did not execute, the reliable claim concerns that observed run. It does not establish that \(C\) is never used.

If event \(X\) was always observed before \(Y\) in one execution, that does not prove a general ordering unless program structure, a contract, or stronger analysis guarantees it.

This limitation is especially important in concurrent and distributed systems. Observed behavior may depend on thread scheduling, timing, network state, the sequence of external events, and other variables that are not reproduced completely on the next run.

CHLOYA therefore applies the rule:

> **execution provides evidence of observed behavior under particular conditions, not automatically a general claim about program behavior.**

This effectively extends the [verification scope][g-verification-scope] concept from 9.6 to exploratory knowledge acquisition.

Every observation has a scope of applicability.

It is determined by the program version, input data, environment state, configuration, execution time, and observation method. The further a subsequent conclusion extends beyond those conditions, the more additional grounds are needed to accept it.

There is another limitation: an observed execution trace is not necessarily a complete account of what occurred.

Logs, traces, telemetry, and other observability mechanisms have bounded visibility. Absence of an event from a log does not prove that the event did not occur when that part of the program was not logged at all. A truncated trace may hide a preceding state. A telemetry collection error may create a false account of event order.

Research on uncertainty in runtime verification shows that incomplete or imprecise traces are a problem in their own right: when events are missing or ambiguous, even a formal monitor may be unable to reach a reliable verdict [434].

An observation's instrumental provenance therefore does not make it absolute truth.

The **observability boundary** must be considered: which part of behavior could the mechanism actually see?

This extends CHLOYA's broader principle of trusted context. When a dynamic observation is transferred to the next participant, both the conclusion and the conditions under which it was obtained should be preserved when those conditions affect later decisions.

For example, the claim “the problem is reproduced only with an empty cache” is much stronger when the cache states actually investigated are known. The conclusion “the external service is not called” has limited value when based only on an incomplete local log.

[Exploratory execution][g-exploratory-execution] thus produces a new class of evidence that must be assessed under the same provenance and applicability requirements as other material project information.

The relationship between experimental execution and project state requires separate attention.

An agent sometimes has to change the environment temporarily in order to acquire knowledge. It may add diagnostic logging, replace a dependency with a test double, prepare special data, disable caching, add an observation point, or temporarily change configuration.

These actions need not form part of the production solution.

An exploratory transformation should therefore be separated from the resulting change discussed in 9.7.

Conceptually, there may be a temporary transition

$$
S_0 \rightarrow S_X,
$$

where \(S_X\) is an experimental state created solely to observe a property.

After the observation is obtained, the experimental change must either be removed, returning to the initial basis, or explicitly turned into an independent part of the final solution if preserving it receives separate justification.

Only after the exploratory cycle is complete is the production transformation formed:

$$
S_0 \xrightarrow{\Delta} S_1.
$$

This distinction prevents temporary diagnostic constructs from entering permanent project state unnoticed.

The danger is greater in agentic development than in manual work. A model can add instrumentation automatically and, after several iterations, lose track of which changes supported investigation and which belong to the target implementation. If the working environment records only current file contents, their provenance is easily lost.

Experimental state must therefore remain controlled and, where possible, reversible.

Reversibility is not the only issue.

Unlike reading a program, executing it is itself an action on an environment.

Code may modify files, access a network, write database data, send messages, execute operating-system commands, create external resources, or destroy existing ones. Permission to read code and permission to execute it are therefore not equivalent authority.

RedCode research demonstrates the relevance of this problem to coding agents. The benchmark specifically covers risky code-generation and execution scenarios and uses real environment interactions; its RedCode-Exec portion contains more than four thousand potentially unsafe execution scenarios [433].

CHLOYA therefore imposes a direct limitation:

> **the epistemic value of execution does not negate its operational risk.**

An investigative action must run within the minimum necessary trust domain and with minimally sufficient authority.

If a hypothesis can be tested in an isolated environment, running it in production creates no investigative value commensurate with the increased risk. If an experiment does not require external network access, granting that access expands the possible impact surface without need.

The particular isolation mechanism depends on the project. It may be a separate process, container, virtual machine, database copy, specialized test environment, or another controlled boundary. Methodologically, the principle is what matters: the experiment's [change impact scope][g-change-impact-scope] must correspond to the information that needs to be obtained.

[Exploratory execution][g-exploratory-execution] is therefore governed by the same minimally sufficient action rules as production transformations.

A wider impact cannot automatically be justified merely because its purpose is diagnostic.

In some situations, an experiment may be more dangerous than the intended correction. Merely executing a migration or infrastructure script diagnostically can cause an irreversible external action before the agent begins constructing a final solution.

The decision to execute is therefore a separate agent action requiring its own authority, reversibility assessment, and trust boundary.

Together, these points support the concept of **[exploratory execution][g-exploratory-execution]**.

> **[Exploratory execution][g-exploratory-execution] is controlled execution of a program or part of it whose primary purpose is to acquire new knowledge about system behavior and reduce material uncertainty before a decision or change.**

[Exploratory execution][g-exploratory-execution] differs from final verification primarily in the direction in which knowledge is acquired.

Verification starts with a predefined property for which evidence is required.

Investigation may start from an incomplete model, while the execution result may change the hypothesis itself and redirect further analysis.

The same technical action can sometimes perform both functions. Running a test may both confirm an expected property and reveal an unexpected trace that produces a new hypothesis. The methodological distinction is determined not by the command run, but by the result's role in the workflow.

This matters to CHLOYA because it separates the investigative phase from the transforming phase.

An agent need not know everything about a system before work begins. Such a requirement would be unrealistic for complex projects. Lack of knowledge, however, should not automatically be compensated for by guesswork and an immediate change to production state.

An exploratory cycle may exist between reading code and modifying it, allowing hypotheses to be tested against observed behavior.

The program thereby becomes an active part of the shared language of humans and AI.

Code communicates the system's potential structure.

[Project memory][g-project-memory] provides known context for its decisions.

Execution reveals actual behavior under particular conditions.

People and agents compare these representations and progressively refine their working model of the system.

None is an absolute source of truth by itself. Code may not reflect external state. Documentation may become outdated. One execution shows only one trajectory. An observation may be incomplete. Reliable understanding therefore emerges by reconciling several knowledge sources and preserving the limits of the conclusions explicitly.

This yields the section's central principle:

> **in CHLOYA, execution is not only a means of verifying a completed result, but also a tool for reducing uncertainty before a change: an agent should be able to formulate hypotheses about a system and test them through bounded, observable, and controlled experiments.**

This approach reduces premature changes, helps localize relevant context more quickly, and makes actual program behavior a source of external knowledge for the agentic loop.

The knowledge obtained is valuable only if the investigation's result does not disappear with the current executor session.

If the next participant must reconstruct the changed code's purpose, repeat completed experiments, and rediscover known constraints, the agentic system accumulates the same [context debt][g-context-debt] the preceding sections sought to reduce.

After investigation and system change, the next question is therefore: **in what state should code and related knowledge be left for the next participant, who lacks the current executor's internal context?**

The next section addresses that question.

[Back to contents](#contents)

## 9.9. Code for the Next Participant

The previous section treated execution as a way to acquire new knowledge about a system. An agent can do more than read code and [project memory][g-project-memory]: it can form hypotheses, conduct bounded experiments, observe actual behavior, and refine its model of the project. That knowledge is then used in a [controlled state transformation][g-controlled-state-transformation].

The understanding obtained does not by itself become a property of the project.

If the established cause of a defect, a discovered constraint, experimental results, or the limits of completed verification exist only in the current executor's internal context, they disappear with that executor. The next person or agent receives a changed codebase but must answer again questions that were already answered.

Part of the work performed is effectively lost.

For CHLOYA, change quality must therefore be assessed not only by how well the current executor solved the task, but also by the state in which the work is left for the next participant.

That participant need not be a new developer. It may be a change reviewer, another specialized agent, a more capable model, a person accepting the result, the original executor after losing its working context, or a developer returning to the same area after a substantial interval.

In every case, the same problem arises: the next participant lacks the previous worker's implicit knowledge.

Knowledge material to continuation must therefore exist outside a particular executor.

The problem is well known in traditional software engineering. Tao et al. studied how developers understand other people's code changes in an industrial setting. Among the most difficult information needs were determining a change's completeness and consistency and, especially, its potential effects on other components [435]. They also showed the value of presenting complex changes in parts corresponding to individual development tasks.

This finding connects directly to the [controlled state transformation][g-controlled-state-transformation] model from 9.7.

Given a transition

$$
S_0 \xrightarrow{\Delta} S_1,
$$

providing only \(S_1\) is insufficient for the next participant.

The resulting state alone does not always reveal quickly what goal \(\Delta\) served, which constraints were considered, which [change impact scope][g-change-impact-scope] was investigated, and which properties of the new state have already been confirmed by the [external verification loop][g-external-verification-loop].

A diff between versions does not solve the entire problem either. It shows **what changed** well, but often fails to explain **why this particular change forms one coherent transformation**.

Research on code review illustrates this boundary. Ram et al. showed that a change's reviewability is related to the quality of its description and to the size and coherence of its change history [269]. A reviewer must not only see the lines that differ from the previous state, but reconstruct a working model of the change's reason and boundaries.

Decomposition alone is insufficient. In a controlled experiment by di Biase et al., splitting a large change into internally coherent parts reduced incorrect review comments and influenced context-search strategy, but did not by itself improve understanding of the change rationale or the number of defects found [270].

A small, semantically coherent change makes work easier to transfer, but does not replace transfer of its meaning.

This raises a broader question: which state should the current executor leave so that the next participant need not repeat completed context-reconstruction work?

CHLOYA uses the concept of **[transferable state][g-transferable-state]**.

> **[Transferable state][g-transferable-state] is an externally represented state of a completed or incomplete work operation, sufficient for the next admissible participant to continue, verify, or accept the work without reconstructing a material part of the context already acquired by the previous executor.**

The key word is **“sufficient.”**

[Transferable state][g-transferable-state] must not contain everything the previous executor saw, thought, and did.

During a complex task, an agent may read dozens of files, test many hypotheses, perform several diagnostic runs, obtain unsuccessful results, return to the original architecture, and only then discover the real cause of a problem.

The complete history of such a trajectory may be useful for a separate process audit, but it should not automatically become the next participant's working context.

If the whole trajectory is transferred without curation, the previous agent's computational effort becomes a contextual burden on the next. The new participant must read not only the resulting knowledge, but also disproved hypotheses, intermediate solutions, and actions whose relevance ended within the preceding iteration.

The transfer object should therefore be not the process's entire past, but the **current state of the knowledge obtained**.

If the cause of a defect has been established, the result and the material basis for the conclusion should be preserved.

If a hypothesis was refuted and is likely to be reconsidered, preserving the fact that it was tested and the result may be useful.

If [verification evidence][g-verification-evidence] was obtained, it must remain connected to the state to which it applies.

If part of the system remains unexplored, that uncertainty must also be preserved.

The next participant then receives not a story about the previous executor's work, but a point from which continuing the work makes sense.

Empirical research on coding agents is beginning to show the cost of violating this property directly. In a 2026 study, KC and Budathoki examined interrupted-task handoffs between agents. They recorded intermediate repository state and compared continuation under different forms of context transfer. In their experiments, supplying information about prior work state rather than only the repository reduced the next agent's median action count by about 20–59% and total input-token volume by about 42–63%; the effect on eventual task resolution was smaller and depended on the model used [436]. Because the work is a preprint, these quantitative results should be treated as contemporary empirical evidence rather than a definitive universal relationship.

The authors call the resulting rediscovery cost *handoff debt*. CHLOYA need not introduce another independent kind of debt for it. The phenomenon is naturally a particular case of [context debt][g-context-debt]: knowledge existed for the previous participant but was not left in a form the next could recover cheaply.

At a handoff boundary, this debt becomes especially measurable.

The next participant first spends resources not on a new system change, but on returning to a knowledge state the previous executor had already reached.

For a person, this cost appears as time, project navigation, and cognitive effort. For an agent, it also includes file reads, searches, tool calls, repeated experimental executions, and consumption of model context.

CHLOYA calls this characteristic **[continuation cost][g-continuation-cost]**.

> **[Continuation cost][g-continuation-cost] is the additional effort the next participant spends reconstructing working context before it can perform new substantive work rather than repeat investigation of a state already established by the previous executor.**

This property has direct economic significance for agentic development.

A local optimization of one session may produce the opposite system-level result. An agent may save computation by not materializing knowledge it acquired, but later executors then repeat the same search. A small reduction in the current operation's cost becomes a recurring cost at every subsequent entry into the same project area.

The cost of agent work therefore cannot be assessed only by the tokens or tool actions consumed in the current invocation.

A project that routinely forces a new agent to reconstruct architecture, dependencies, and decision rationales may remain expensive to maintain even as the cost of an individual model call falls.

This does not mean that every executor should leave the most detailed possible account of its work.

Recent research on transferring trajectories between different models shows a more complex picture. In a 2026 preprint, Ganz et al. studied continuation of agent trajectories after switching between cheaper and more capable models. Transferring the full previous trajectory did not always produce the best result: the effect depended on the direction of transfer, and in some scenarios shortening or omitting part of the previous trajectory improved the next model's result [364].

This aligns with CHLOYA's broader reasoning.

**More context does not mean a better transferred state.**

The next executor needs not the maximum volume of the past, but minimally sufficient, reliably organized context from which it can recover the current work position.

The transfer task is therefore not to preserve a complete reasoning trajectory, but to **collapse it into persistent external state**.

Some information requires no separate description in this collapse. If a change is already expressed in code, it should not be rewritten at length in natural language. If a [verifiable property][g-verifiable-property] is fixed by a test, the transfer should point to the existing evidence rather than reproduce the test's meaning in a long report. If an architectural rationale already resides in [project memory][g-project-memory], a discoverable link to that record is enough.

[Transferable state][g-transferable-state] must not become another competing source of truth.

Its purpose is to **route the next participant to canonical artifacts and communicate only the temporary work state that cannot yet be recovered from them**.

This fundamentally distinguishes it from [project memory][g-project-memory], discussed in 9.5.

[Project memory][g-project-memory] is intended for long-term project knowledge. It preserves architectural rationales, material constraints, rejected alternatives, and other information that should remain available independently of a particular task.

[Transferable state][g-transferable-state] has a shorter lifecycle. It applies to the current work operation.

An explanation of why the system uses a particular architectural boundary may remain current for years and belongs in [project memory][g-project-memory].

The fact that a particular integration test could not yet run because a test environment is unavailable may be critical to the next participant today and cease to matter as soon as the check is completed.

The two layers must therefore not be merged into one permanent log.

[Project memory][g-project-memory] answers:

**what should the project remember?**

[Transferable state][g-transferable-state] answers a different question:

**what must be known to continue this work now?**

This separation prevents [project memory][g-project-memory] from gradually becoming a store of temporary notes and transferable state from duplicating documentation for the whole system.

When an operation is completed, temporary state should progressively disappear or move into more durable canonical representations.

If a discovered constraint has long-term importance, it moves into [project memory][g-project-memory] or is expressed through system structure.

If a discovered defect becomes a durable regression test, the corresponding knowledge is partly materialized in a verification artifact.

If an experimental hypothesis ceases to matter after the correction, it need not be preserved in permanent memory.

If a change is complete, its actual history remains in version control.

[Transferable state][g-transferable-state] can therefore be understood as a **temporary layer between the current executor's internal context and the project's persistent state**.

It is needed precisely where the work still contains a material remainder not materialized in other ways.

An important limitation follows: a fully completed and properly structured operation may require no separate extensive handoff document at all.

If code is comprehensible, the change is semantically coherent, checks have been run and remain available, necessary comments are current, long-term decisions have been entered into [project memory][g-project-memory], and no material unknown areas remain, the project itself already constitutes sufficiently good [transferable state][g-transferable-state].

A large additional report then does not reduce [context debt][g-context-debt], but creates new text that must later be maintained or ignored.

CHLOYA therefore imposes no mandatory handoff bureaucracy on every operation.

> **The best [transferable state][g-transferable-state] is achieved not through the maximum amount of accompanying text, but through maximum reliance on current canonical artifacts with the minimum additional temporary context.**

A separate state representation is especially important in the opposite cases: an incomplete task is interrupted, the executor changes, some areas remain unverified, some experiments cannot be performed, a temporary solution remains, or material uncertainty persists.

It is especially important here to transfer not only what is known, but also the **boundaries of what is known**.

Section 9.7 represented the result of a controlled transformation as

$$
R_{\Delta}=(S_0,\Delta,S_1,E,U),
$$

where \(E\) denotes the [verification evidence][g-verification-evidence] obtained and \(U\) the material unverified or indeterminate areas.

The meaning of \(U\) becomes especially clear at a handoff boundary.

If the previous agent did not verify a change's effect on a particular integration, that missing check does not disappear when its session ends. If the information is not transferred, the uncertainty merely becomes invisible to the next executor.

That is more dangerous than an explicitly known absence of verification.

The next agent may interpret silence as completion and base a later decision on a stronger assumption than the actual evidence supports.

Therefore:

> **[transferable state][g-transferable-state] must preserve not only acquired knowledge, but also the known boundaries of that knowledge.**

This extends the trusted-context rules from earlier CHLOYA chapters.

A previous executor's statement does not become more trustworthy merely because it was placed in handoff state.

If an agent reports that an error's cause was established experimentally, preserving a reproducible basis or a link to the observation is useful.

If it reports that tests passed, the actual [verification evidence][g-verification-evidence] is a stronger source.

If a constraint is expressed in an existing contract, [transferable state][g-transferable-state] should route the next participant to that contract rather than become another textual copy of the rule.

Handoff state is therefore not a source of truth, but a **navigation layer over sources of truth and the operation's temporary state**.

This also means that transferability cannot be created only in the last minute before a session ends.

If an agent retains all material knowledge solely in internal context throughout a long task and then attempts to reconstruct it in one final retelling, some information will inevitably be lost, distorted, or mixed with intermediate conclusions that are no longer current.

Transferability must be built as work proceeds.

A durable architectural decision moves into [project memory][g-project-memory] when it becomes sufficiently definite.

A reproducible defect is preserved in an appropriate verifiable form.

A new invariant is expressed, where possible, through a test, contract, type, or other canonical mechanism.

A material change remains visible in its [change artifact][g-change-artifact].

Evidence obtained is associated with the state it checked.

By the time the participant changes, most work already exists in the project and only residual temporary state requires a special handoff.

This is why it is useful to speak not only of [transferable state][g-transferable-state] as an artifact, but of **[state transferability][g-state-transferability]** as a quality of the working system itself.

> **[State transferability][g-state-transferability] is a property of work state whereby another admissible participant can reconstruct the required working context and continue the operation with a bounded cost of repeated investigation.**

This property applies equally to human-to-human, human-to-AI, AI-to-human, and AI-to-AI interaction.

A good review request must be transferable to a reviewer.

Incomplete work must be transferable to a replacement executor.

An autonomous agent's result must be transferable to the person making the decision.

A person's work must leave a sufficiently formalized state for the agent that continues it later.

The [shared working surface][g-shared-working-surface] from 9.1 appears here again.

Participants may understand a program differently and have different capacities for processing context, but continuity of work must not depend on the existence of one particular internal model.

Code for the next participant therefore does not mean special “code for AI” or an implementation commented in maximum detail.

It means a system in which knowledge critical to continuation does not remain solely with the author of the latest change.

There is nevertheless a fundamental limit to such transfer.

As Naur showed [372], programming involves a developer forming a theory of the program that cannot be reduced completely to source text and documentation. No process can guarantee that every subsequent participant instantly acquires the same understanding formed by a person or agent through extended investigation.

CHLOYA does not attempt to eliminate this fundamental limitation.

Its goal is different: to reduce the amount of **required hidden knowledge** whose loss forces the next participant pointlessly to repeat work already performed.

The section's central principle can therefore be stated as follows:

> **a previous participant should leave not the maximum description of its work, but minimally sufficient external state that allows the next participant to continue without reconstructing material knowledge that has already been acquired.**

This principle also changes the criterion of completed work quality.

A result is good not only when it solves the current task and passes the required checks. It must leave the system in a state from which the next substantive operation can begin without an expensive reconstruction of the previous executor's hidden context.

Maintenance cost thereby includes not only the cost of a change, but also the cost of the next participant entering the changed system.

In human–agent development, this acquires a direct economic dimension. If every new agent spends a substantial share of its computational budget rediscovering facts already known to the project, the system remains inefficient regardless of how quickly code itself can be generated.

Transferability allows part of this cost to be paid once: knowledge is materialized in an appropriate artifact and becomes available to later participants through a predictable context structure.

Even a well-organized handoff does not solve every problem of a shared language for humans and AI.

Not all intent can be expressed in code. Not every quality has an unambiguous test. Not all human understanding can be reduced to a formal artifact. [Project memory][g-project-memory] inevitably requires selection and interpretation, while execution observations are always limited by the conditions of a particular experiment.

After considering the mechanisms that make code a [shared working surface][g-shared-working-surface], the limits of this model must therefore be established.

The next section examines **where the capabilities of [code as a shared language][g-code-shared-language] end and which kinds of meaning require other forms of human–AI interaction**.

[Back to contents](#contents)

## 9.10. The Limits of Code as a Shared Language

The preceding sections progressively expanded the role of code in human–agent development. Code was treated as a shared representation of state available to humans, AI, and computing systems; program structure as a way to convey meaning and constrain interpretation; tests and other verification mechanisms as sources of external evidence; [project memory][g-project-memory] as a way to preserve knowledge not expressed directly by implementation; execution as a means of acquiring new knowledge; and [state transferability][g-state-transferability] as a condition for continuing work without reconstructing already discovered context.

It is easy to draw a further but excessively strong conclusion: if code, contracts, tests, [project memory][g-project-memory], and handoff mechanisms are progressively improved, all material meaning in a software project can eventually be embodied in formal and [machine-interpretable artifacts][g-machine-interpretable-artifact].

For CHLOYA, that assumption would be wrong.

Code can indeed become a [shared working surface][g-shared-working-surface] for different participants, but this does not make it a universal carrier of human intent and all knowledge associated with a software system.

This limit predates modern AI.

In analyzing software-engineering complexity, Brooks distinguished difficulties arising from the technical means used from difficulties inherent in the software system being created [437]. A material part of the work consists not merely of translating a finished solution into syntactically valid code, but of forming the conceptual construct: deciding which entities exist in the system, how they relate, and which behavior should emerge from their interaction.

Modern generative models can substantially reduce the cost of producing program text. They accelerate the creation of standard constructs, transformation of existing code, information search, and many other operations that previously required direct developer labor. Making implementation cheaper, however, does not answer **which implementation should be created at all**.

Under some conditions, this makes the conceptual part of the task relatively more important rather than less.

If several technically workable variants can be generated quickly, the main difficulty shifts from the ability to write each one to choosing which variant fits the actual goal, constraints, and future development of the system.

A capable executor therefore does not eliminate the need to define intent.

### Code Appears After Deciding What Matters

Code always describes a model of some domain.

Even when a program interacts directly with physical devices, financial operations, people, or organizational processes, it does not operate on reality in its entirety, but on selected representations of that reality.

Before a type, function, database table, or programming interface appears, someone must decide which concepts matter, which distinctions must be preserved, and which may be discarded.

Zave and Jackson's work on requirements engineering demonstrates this boundary particularly well. They distinguish the environment in which the problem exists, requirements for the desired state of that environment, and a specification of the machine's behavior [438]. The levels are related but are not the same representation.

A requirement may concern the real world:

an employee must access only the data they are permitted to access.

The implementation operates on more specific concepts:

an account, role, permission set, resource identifier, and authorization rules.

Before those entities became code, someone had to decide that they represented the real requirement well enough.

Code can check the internal consistency of the chosen model, but cannot automatically establish that the original domain model was chosen correctly.

A program's conformity to its own specification and a system's conformity to a real need are therefore different claims.

A completely consistent implementation of a mistaken understanding can be built.

An exhaustive test suite can be written for an incorrectly selected model.

Properties can be proved of a program that flawlessly does something other than what the user actually needs.

Therefore:

> **the formal definiteness of an artifact does not compensate for uncertainty or error in the original intent.**

This limitation supplements the conclusions of 9.6.

[Verification evidence][g-verification-evidence] shows that a formulated property holds within its [verification scope][g-verification-scope]. A prior question remains: is that property an adequate representation of the real intent?

### Natural Language Remains Part of the Engineering Environment

Section 9.2 showed that material requirements should be moved into machine-interpretable form when this can be done without losing important meaning.

It does not follow that natural language is merely a temporary, imperfect stage that mature engineering should eliminate completely.

Franch et al. studied requirements-specification practice in twelve companies and found that natural language remains the primary medium for requirements, usually supplemented by other forms and tools [440]. Ambiguity, inconsistency, and incompleteness in natural-language requirements also remain among the most common practical problems.

This situation reflects more than a shortcoming of formalization methods.

In a project's early stages, intent itself is often not yet sufficiently definite.

Stakeholders may understand the same concept differently. They may have conflicting goals. A material constraint may emerge only after the first working version exists. A user may recognize that an interface is unsatisfactory without yet having an exact formal account of what it should become.

In such situations, ambiguity cannot be eliminated merely by translating text into a stricter form.

If the underlying decision has not yet been made, formalization can only **fix one possible option and give it the appearance of greater certainty**.

[Sufficient formalization][g-sufficient-formalization] in CHLOYA therefore does not mean formalizing every uncertainty as early as possible.

What should be formalized is what is already sufficiently determined for machine application or verification. Where meaning itself remains subject to investigation or agreement, that uncertainty must remain visible.

Otherwise, a formal artifact becomes a way to conceal ambiguity rather than reduce it.

### Not All Material Knowledge Resides in Artifacts

The limits of code as a carrier of knowledge remain visible after a system exists.

Naur [372] treated programming as the construction of a theory of the program in a developer's mind. Source text is an important outcome of this process, but does not exhaust the understanding of why a system has its particular structure or how it should change when new requirements appear.

The preceding CHLOYA sections reduced much of this problem through [structural context][g-structural-context], [project memory][g-project-memory], verification evidence, and [transferable state][g-transferable-state].

Reducing dependence on implicit knowledge is not the same as eliminating it completely.

Ryan and O'Connor studied the acquisition and sharing of tacit knowledge in development teams and showed its substantial role in team work [439]. Such knowledge forms through experience and social interaction and does not always exist in a form a participant can immediately articulate in full.

An experienced specialist may notice a suspicious combination of symptoms before being able to state a precise diagnostic rule.

A developer may sense that a proposed abstraction conflicts with project architecture before formulating the exact violation.

A domain specialist may reject a technically consistent solution because it does not fit a real workflow, part of which was never reflected in the requirements.

Some of this information can later be materialized.

A diagnostic observation may become a verifiable rule.

An architectural judgment may become an explicitly stated principle.

Domain knowledge may become a new requirement.

A recurring constraint may become a contract or test.

Such materialization is separate work and does not occur automatically.

CHLOYA uses the concept of an **[interpretation remainder][g-interpretation-remainder]** to describe this boundary.

> **An [interpretation remainder][g-interpretation-remainder] is the part of meaning material to a decision that, in the project's current state, is not represented sufficiently completely in persistent formalized or otherwise unambiguously interpretable artifacts and therefore requires contextual judgment by a person or agent.**

The word “current” is fundamental.

An [interpretation remainder][g-interpretation-remainder] is not declared inherently impossible to formalize.

Its boundary can move.

Something that requires human discussion today may become a precise rule tomorrow and be transferred to an agent. A recurring manual decision may reveal its stable structure and become machine-interpretable.

At every particular moment, however, some meaning remains for which that transition has not yet occurred.

CHLOYA must make its existence visible rather than deny it.

### Not Every Decision Is a Question of Technical Truth

The limits of code representation are especially clear in tasks that require choosing between more than a technically correct and an erroneous state.

Software systems implement decisions about privacy, accessibility, usability, acceptable risk, distribution of authority, and many other properties affecting people.

Shahin et al. systematized 51 studies on incorporating human values into software engineering and showed that translating such values into concrete engineering decisions is a complex task in its own right [441]. Much of the existing work concerns requirements elicitation and design—the stages preceding direct implementation.

This supports an important distinction between **operationalizing a decision** and **choosing the decision itself**.

Suppose a rule has been adopted that particular user data is deleted after thirty days.

Engineering can then do much. The period can be represented in configuration, automatic deletion can be implemented, a check can be created, and actual compliance can be monitored.

The question of why thirty days was judged acceptable may depend on law, the nature of the data, user needs, business processes, and a trade-off between several values.

The selected rule can be formalized.

The choice itself is not necessarily derived from program semantics.

A machine-verifiable criterion can therefore enforce an adopted normative decision reliably, but does not automatically provide the grounds for **why that particular decision should be adopted**.

This is one area in which the human role cannot be explained solely by the model's current intellectual limitations.

Even an executor with perfect reasoning ability needs a basis for choosing between conflicting human goals. If the system does not provide such a basis, the problem is not the executor's insufficient ability but the absence of a defined decision criterion.

### A Verification Criterion Is a Model of the Goal

The same boundary exists in more technical tasks.

Section 9.6 showed that passing a test does not imply complete program correctness. Section 9.10 supports a more general form of the problem.

Every operational criterion represents only one aspect of the actual intent.

If an agent optimizes a solution against that criterion, it may find a state that fully satisfies the formal condition while diverging from the result the person intended.

In research on intelligent systems, this problem appears in various forms of optimization against an incomplete specification or evaluation signal. A recent survey by Morampudi et al. treats reward hacking in large-language-model agent systems as a class of situations in which an agent exploits properties of an evaluation function, verification mechanism, or other signal rather than achieving the intended goal [444].

For software engineering, whether such behavior constitutes “deception” is not the main question.

The problem arises earlier.

Whenever a formal criterion does not fully coincide with actual intent, optimizing against it creates the possibility of an undesirable result that formally passes the check.

An agent may change a test instead of correcting an implementation.

It may remove an analyzer warning in a way that conceals the problem.

It may satisfy a locally stated criterion while violating a broader architectural expectation.

It may create technically valid behavior that conflicts with the user's workflow.

Such actions do not necessarily require an intention to circumvent the system. They may follow naturally from rational optimization against an incomplete representation of the goal.

Therefore:

> **a verifiable criterion must be treated as a formalized model of intent, not automatically as a complete substitute for intent.**

The more autonomous the executor, the more important this distinction becomes.

When a person directly controls each intermediate step, they may detect a divergence between a formally admissible action and the expected meaning before work is complete.

An autonomous agent may follow a much longer trajectory while consistently optimizing a misformulated goal.

Greater autonomy therefore raises requirements not only for the agent's ability to perform a task, but also for the quality of external goals, constraints, escalation, and verification bases.

### Even a Fully Formalized Question Does Not Always Have a Universal Automatic Check

Even when a property can be stated with complete precision, there need not be a general algorithm capable of deciding automatically whether an arbitrary program has that property.

Rice's classic result establishes the undecidability of every nontrivial semantic property of the function computed by a program for a general class of programs [442].

For engineering practice, this does not mean that programs cannot be verified at all.

Practical tools successfully verify many useful properties precisely because they work with restricted languages, defined models, particular classes of states, or incomplete analysis.

Brain and Polgreen's modern presentation of different schools of formal verification likewise emphasizes that verification methods have different strengths, assumptions, and practical areas of application [443].

Even within the formalized part of a project, therefore, no universal mechanism can answer every question about the behavior of an arbitrary system automatically and exhaustively.

This conclusion is fully consistent with the [verification scope][g-verification-scope] introduced earlier.

The stronger the required guarantee, the more often the investigated model must be restricted, the cost of analysis increased, or additional human reasoning introduced.

The theoretical limits of automated analysis are therefore not an argument against formal methods.

On the contrary:

> **the limits of formalization are grounds for stating the applicability of formal tools more precisely, not for abandoning them.**

CHLOYA does not require a choice between complete formalization and unconstrained human interpretation.

The goal is to move into machine-interpretable and verifiable form those parts of knowledge for which doing so genuinely reduces risk, the cost of repeated understanding, and dependence on hidden context.

Remaining uncertainty must be preserved as uncertainty rather than disguised in an artificially precise form.

### A Real System Is Larger Than Its Codebase

There is another limit, already touched on in the discussion of project state in 9.7.

A software system does not exist only in source code.

Its actual behavior is influenced by data, users, external services, hardware, networks, organizational processes, regulatory constraints, and many other elements of its environment.

Some may be represented in a project by schemas, configurations, test doubles, and other artifacts. Those representations are again models of external reality, not reality itself.

Code conformity to requirements therefore cannot automatically be equated with successfully solving a human problem.

A system may pass every test and still be difficult to use.

It may satisfy a functional specification while creating unacceptable operational load.

It may implement an established rule correctly after external law has made that rule wrong.

It may work technically while people do not use it as its designers expected.

The relationship between a program and its environment must therefore remain part of engineering reasoning.

Code is a powerful representation of the machine, but the meaning of the machine's existence is determined outside it.

### Correct Agent Work Is Broader Than Correct Resulting Code

Recent research on professional coding agents shows a similar shift.

Dong, Shi, Sampath, and Macvean analyzed 91 rule sets developers had defined for coding agents and validated the resulting classification through interviews with 15 experienced developers. Expectations of an effective agent included not only code quality and reliability, but also compliance with processes and standards, effective problem solving, and collaboration with the developer [445].

This is especially important to CHLOYA.

An agent may create functionally correct code while performing a poor agent operation.

It may exceed its authority, conceal material uncertainty, violate an established architectural boundary, change a verification criterion together with an implementation without sufficient grounds, or perform an irreversible action where human confirmation was required.

No unit test of the resulting function detects all such violations by itself.

Agent quality therefore cannot be assessed only from the resulting program text.

The **character of the transition** through which the state was obtained must also be assessed.

This returns to the controlled-transformation model from 9.7 and to the roles, authority, and trust boundaries in earlier CHLOYA chapters.

Code is the central object of interaction, but does not replace governance of the action process.

### Interpretation Remainder as an Autonomy Boundary

The limitations considered above support an important conclusion for agent-system architecture.

An [interpretation remainder][g-interpretation-remainder] exists in almost every nontrivial task. This alone does not require immediately transferring a decision to a person. Both people and agents routinely work with incomplete information and must interpret context.

What matters is not interpretation itself, but the **cost of an interpretive error and the authority to make the corresponding decision**.

When an agent chooses a local-variable name, the [interpretation remainder][g-interpretation-remainder] may be substantial while the risk of error is low.

When it decides which user data may be deleted, chooses an irreversible migration, or independently interprets an ambiguous security-relevant requirement, the same uncertainty has a different level of consequence.

Escalation should therefore not be tied to abstract “model confidence.”

Probabilistic confidence alone poorly describes the kind of error and its consequences.

A more substantive basis arises when a required decision simultaneously extends beyond the available formalized basis, materially affects the result, and concerns an area in which the agent has no authority to determine the missing meaning independently.

The [interpretation remainder][g-interpretation-remainder] then becomes a **visible authority boundary**.

This provides a more durable basis for human involvement than the claim that present-day models are not intelligent enough.

As AI capabilities increase, part of the former [interpretation remainder][g-interpretation-remainder] will shrink.

Models will reconstruct domain context, investigate systems, assess alternatives, and formalize requirements more effectively.

Increasing an executor's capability, however, does not itself create an absent external choice criterion.

When several options are technically admissible and the choice depends on organizational goals or human values, an agent's intelligence helps analyze consequences but does not automatically authorize it to decide which value takes priority.

The human–agent boundary is therefore dynamic, but cannot be reduced to comparing their intellectual capabilities.

It is also determined by the provenance of the goal, authority, and the nature of the decision.

### Not Every Ambiguity Requires Immediate Elimination

The preceding sections repeatedly emphasized reducing the space of interpretation. Section 9.10 must clarify the scope of that principle.

What should primarily be reduced is **unnecessary and risky ambiguity** that forces subsequent participants to guess again at a decision already made.

In some tasks, however, the decision has not yet been made.

The requirement “make the interface calmer and more professional” is much less formal than a numerical API response-time limit. Immediately replacing it with a large set of quantitative metrics may not bring the system closer to the user's actual intent.

A better strategy may be to create several variants, have a person assess them, refine preferences, and progressively turn part of the subjective intent into persistent project decisions.

Interpretation in such a process is not a defect, but a way to form knowledge that does not yet exist.

This demonstrates a limit of the idea of “specification before implementation.”

In exploratory and creative tasks, implementation itself may help discover requirements. A prototype allows a user to discover a preference that could not be stated before a concrete object of comparison existed.

CHLOYA must therefore permit iteration between intent and artifact.

[Sufficient formalization][g-sufficient-formalization] does not require all meaning to be known before work begins. It requires that, as material decisions stabilize, repeated interpretation be replaced by a more persistent external representation where economically and technically justified.

### The Limit of the Shared Working Surface

Code therefore does occupy a special position in human–agent development.

People can read it meaningfully.

AI can analyze and transform it.

A computing system can execute it and verify many of its properties instrumentally.

Code persists between sessions and executors.

Its structure can express relationships, constraints, and context.

Related tests, contracts, [project memory][g-project-memory], and execution results extend this surface and allow far more knowledge to be materialized than source text alone.

A [shared working surface][g-shared-working-surface], however, is not shared completeness of knowledge.

It contains the part of state that has already acquired a sufficiently persistent external representation.

Outside it remain unformulated requirements, tacit domain knowledge, value decisions, incomplete models of the external environment, new observations, and other elements of the [interpretation remainder][g-interpretation-remainder].

The boundary between these areas moves.

Good engineering can progressively move recurring and material knowledge into the [shared working surface][g-shared-working-surface].

Pretending that the external area does not exist does not make a system more formal. It merely conceals its real assumptions.

[Code as a shared language][g-code-shared-language] must therefore be understood within limits.

It does not mean that humans, AI, and computing systems have the same model of the world.

It does not mean that every human task can be reduced to program text.

It does not mean that every material property can be verified automatically.

Nor does it mean that a formally successful result is automatically desirable.

The strength of the model lies elsewhere.

Code and related artifacts create a space in which many decisions can become external, observable, verifiable, and transferable between different participants.

The more material knowledge is correctly moved into this space, the less the system depends on the hidden context of a particular person or agent.

This transfer must not replace a decision that has not yet been made with a formally precise accident.

The [sufficient formalization][g-sufficient-formalization] principle introduced in 9.2 must therefore also be understood as a limiting principle:

> **formalization should reduce ambiguity and verification cost where it preserves the task's material meaning; it must not turn unresolved uncertainty or a value choice into a formally precise approximation mistakenly treated as the original intent.**

This boundary avoids two extremes.

On the one hand, there is no need to leave a machine-verifiable rule in human memory merely because the entire system cannot be formalized completely.

On the other, the existence of a formal rule cannot be taken to eliminate the need for a human decision where the rule itself remains subject to choice.

The limit of [code as a shared language][g-code-shared-language] therefore does not weaken the chapter's central proposition.

It makes it more precise.

Code is a [shared working surface][g-shared-working-surface] for humans, AI, and the computing system **within the part of project state that can already be materialized with sufficient unambiguity**.

The remaining meaning must retain explicit connections to sources of intent, domain knowledge, uncertainty, and the participants authorized to make the corresponding decisions.

With this boundary established, the chapter's results can be assembled.

The next section treats code as a [shared working surface][g-shared-working-surface] not as an isolated metaphor, but as the final architectural model of interaction among people, AI, software tools, and the project's external state.

[Back to contents](#contents)

## 9.11. Code as a Shared Working Surface

At the beginning of this chapter, code was considered as a possible shared language for humans, AI, and computing systems. This formulation moved beyond the traditional view in which source text is primarily the result of a programmer's work and an instruction to a machine. In human–agent development, code simultaneously becomes an object of reading, transformation, execution, verification, and transfer between different participants.

The successive examination of context, structure, [project memory][g-project-memory], verification, state transformations, [exploratory execution][g-exploratory-execution], and the limits of formalization nevertheless supports a more precise conclusion.

The concept of **language** describes only part of what occurs.

Code does more than communicate messages between participants. It preserves state between individual acts of interaction. One participant can leave a work result in it; another can discover that result, compare it with the previous state, change it, verify it, and pass it on. Code is surrounded by related tests, contracts, schemas, configurations, [project memory][g-project-memory], [verification evidence][g-verification-evidence], and other artifacts that together form a persistent external environment for activity.

The chapter's final concept is therefore the **[shared working surface][g-shared-working-surface]**.

> **A [shared working surface][g-shared-working-surface] is a persistent external representation of system state and related knowledge through which different participants can recover sufficient context, perform admissible transformations, observe and verify their consequences, and transfer state to the next participant.**

This definition does not require every participant to understand the system in the same way.

A person can connect a software solution to the domain, organizational goals, and value constraints. A large language model can compare many representations, form hypotheses, transform software artifacts, and use environmental feedback. A compiler processes code according to the programming language's formally defined semantics. A testing system observes particular execution properties. Version control represents differences between states.

These forms of interaction cannot be reduced to one kind of “understanding.”

The working surface is shared in a different sense: participants address **one external state**, although they extract different kinds of information from it and have different means of affecting it.

The analogy with [boundary artifacts][g-boundary-object] introduced in 9.1 is therefore useful but must retain its qualifications. Star and Griesemer's classic [boundary object][g-boundary-object] concept [376] described coordination between social groups, not interaction between a person and a computational model. Modern research on [boundary artifacts][g-boundary-object] in software engineering likewise focuses primarily on collaboration among different professional and organizational participants [377].

The functional similarity is nevertheless significant.

The same software artifact retains a sufficiently stable identity for different participants to use it for different purposes without fully sharing one another's internal representations.

A function remains the same function for a developer, agent, analyzer, and version-control system, although each works with different properties of it.

A contract may simultaneously explain an admissible form of interaction to a person, constrain an agent's scope of action, and provide a formal basis for a software tool.

A test may serve as an example of expected behavior for a person, a machine-interpretable constraint for an agent, and an executable check for a computing system.

Collaborative activity thereby becomes possible not because internal models match completely, but because a sufficiently persistent external basis exists.

Research on common ground in human–agent interaction provides additional theoretical support for the distinction. In a systematic review of 38 studies, Tolzin and Janson treat the formation of *common ground* as one mechanism of successful coordination between a person and a conversational agent [446]. CHLOYA does not import the entire conversational-interaction model into software engineering. The relevant general conclusion is that effective interaction requires some shared basis against which participants can coordinate subsequent actions.

A codebase and its related artifacts can perform precisely this operational function.

**Common ground must not be equated with common understanding.**

Participants need only be able to refer unambiguously to one state, interface, verification result, or change and act coherently in relation to it. Their internal representations of the system's reasons, goals, and organization may differ substantially.

This is especially important for AI.

Trying to achieve durable development by permanently preserving identical internal context between a person and a model is unrealistic. Sessions end. Context windows are bounded. A model may be replaced by another version. A different agent may search and reason differently. People also forget details and reconstruct much of the context again months later.

Continuity of development must therefore not depend on continuity of one participant's internal state.

It must be transferred into the project's external state.

This is one fundamental consequence of the [shared working surface][g-shared-working-surface]:

> **participants may change while material working state retains continuity.**

An agent receives the project's existing state, reconstructs [required context][g-required-context], investigates the system, performs a bounded change, and leaves the result in a form available to the next participant.

The next executor need not possess its predecessor's internal history. It receives the changed working surface and continues from there.

This model differs from an approach that treats AI as a long-term carrier of project knowledge.

In CHLOYA, AI may actively use memory and current context, but **must not be the only place where material project state exists**.

The same rule applies to people. An architecture that remains viable only while one particular developer remembers the reason for every decision is equally fragile.

The problem becomes technically more acute in an agentic environment because a model's internal context has an especially clear lifecycle limit.

Therefore:

> **AI should consume and produce project state, but should not be its sole carrier.**

A model's internal context in such a system resembles working memory more than a long-term project store.

It may contain temporary hypotheses, intermediate plans, and local-analysis results. While they are needed only for the current action, externalizing them may provide no value.

When a result must influence a future participant, however, it must leave internal context and acquire an appropriate external representation.

An architectural decision moves into [project memory][g-project-memory].

A new durable constraint acquires a structural or formalized representation wherever possible.

A verifiable expectation is materialized in a test, contract, or other verification artifact.

A completed change remains in state history.

A material unverified area is transferred to the next participant as known uncertainty.

Internal reasoning thereby ceases to be the only place where the result of intellectual work exists.

This connects Chapter 9 directly to the context-governance rules discussed in Chapter 8.

Project state must not only be external, but reliable enough to transfer. The provenance, verification status, scope, and known uncertainty of material claims must not disappear when the executor changes.

The [shared working surface][g-shared-working-surface] therefore consists of more than code.

Code remains its core because much of the system's computational behavior is materialized there. Real collaboration, however, requires a broader set of related representations.

Types and interfaces express structural boundaries.

Contracts and tests materialize some requirements.

[Project memory][g-project-memory] preserves reasons and constraints that have no natural representation in code.

[Change artifacts][g-change-artifact] show transitions between states.

[Verification evidence][g-verification-evidence] connects claims about results to observed outputs of external mechanisms.

[Transferable state][g-transferable-state] preserves the temporary boundary of incomplete work.

Execution data helps refine the working model of the system.

These artifacts should not mechanically duplicate one another. Their value arises precisely from separated responsibilities.

Code shows implemented state.

Code structure makes part of its meaning discoverable.

[Project memory][g-project-memory] preserves the long-term basis of decisions that cannot be recovered reliably from implementation alone.

The [external verification loop][g-external-verification-loop] establishes particular properties of state.

Change history preserves the transformation trajectory.

Handoff state communicates the material remainder of current work that has not yet acquired another canonical representation.

A [shared working surface][g-shared-working-surface] is therefore not one universal document, but a **connected system of artifacts with different semantics**.

This fundamentally distinguishes it from attempts to solve the context problem with one large instruction file.

Research on persistent context files for coding agents already shows that such documents become complex, evolving maintenance objects in their own right [392]. If all project information is moved into them, [context debt][g-context-debt] does not disappear; it becomes concentrated in a new place.

A [shared working surface][g-shared-working-surface] must work differently.

Knowledge is located where it has a natural and maintainable representation, while links allow a participant to discover required neighboring elements as work proceeds.

The [contextual self-sufficiency][g-context-self-sufficiency] principle from 9.3 thereby extends to the entire project model.

A participant need not load the whole system into working context. It must receive a bounded area sufficient for the particular operation and have a discoverable path to the next level of knowledge when the initial area is insufficient.

This applies to humans and AI alike.

A large context window does not eliminate the need to design such structure. It merely increases the volume of information that can technically be supplied to an executor.

If relevant constraints remain hidden, outdated, or mixed with substantial noise, expanding available context may only increase the cost of selecting material information.

The quality of a [shared working surface][g-shared-working-surface] is therefore not determined by the volume of data it stores.

A more useful criterion is the **cost of safe action based on it**.

If a person or agent must reconstruct much of the architecture, search a long history for decision rationales, and repeat earlier experiments before making a local change, the surface performs its coordinating function poorly.

If required state can be discovered through a bounded number of predictable relationships and material properties have accessible verification bases, the next participant can begin new substantive work much sooner.

[Contextual self-sufficiency][g-context-self-sufficiency], [context debt][g-context-debt], and [continuation cost][g-continuation-cost] thus become not isolated concepts but quality characteristics of the [shared working surface][g-shared-working-surface].

This has a direct economic consequence in agentic development.

Much of a model's computational expenditure is associated not with creating the required change itself, but with acquiring context: reading files, searching dependencies, reconstructing history, repeating exploratory execution, and comparing many representations.

If the result of that investigation disappears when the session ends, the project pays for it again at the next similar entry point.

If material knowledge acquires a persistent external representation, part of the completed intellectual work becomes a reusable resource.

In this sense, externally materializing knowledge has an economic function.

It converts part of the one-time cost of human analysis or AI computation into state that reduces the cost of later operations.

This saving arises only through curation.

Preserving the entire reasoning stream does not automatically turn it into a useful asset. As 9.9 showed, excessive context transfer can itself increase [continuation cost][g-continuation-cost] [442–443].

What is capitalized is therefore not the amount of preserved text, but the **quality of materialized knowledge**.

This reasoning also casts the role of an agent in a new light.

An agent in CHLOYA is not simply a code generator.

It is a temporary executor of operations on the [shared working surface][g-shared-working-surface].

Before acting, it reconstructs sufficient context from external representations.

When knowledge is lacking, it may use [exploratory execution][g-exploratory-execution] to test hypotheses.

It then constructs a [controlled state transformation][g-controlled-state-transformation].

The resulting state passes through the available [external verification loop][g-external-verification-loop].

Material work results are embodied in the appropriate artifacts.

The agent can then be replaced by another executor without preserving continuity of its internal state.

The unit of organization becomes not “an agent that knows the project,” but an **operation on project state**.

This is fundamental to an agent-modular architecture.

The less the system depends on one executor's unique hidden state, the easier it is to change models, distribute roles, connect specialized agents, and return control of particular decisions to a person.

This does not make every participant interchangeable.

A [shared working surface][g-shared-working-surface] provides coordination, not identical authority.

One participant may only read state.

Another may propose a transformation.

A third may perform verification.

A person may make decisions where the [interpretation remainder][g-interpretation-remainder] is material or the cost of error requires separate authority.

The role separation discussed earlier in CHLOYA thereby receives a shared technical basis: different roles interact with one project state while performing different admissible operations on it.

This is especially clear in the [controlled state transformation][g-controlled-state-transformation] from 9.7.

When a project is in state \(S_0\), an agent does not receive an abstract right to “write code.” It receives the ability to perform a bounded transformation \(\Delta\), producing state \(S_1\).

The transformation itself has a goal, boundaries, and expected properties.

The [external verification loop][g-external-verification-loop] produces evidence for \(S_1\).

The new state is then transferred to the next participant.

The shared work cycle can therefore be represented as a repeated sequence:

$$
S_n
\xrightarrow{\text{context recovery}}
K_n
\xrightarrow{\text{investigation and decision}}
\Delta_n
\xrightarrow{\text{application}}
S_{n+1}
\xrightarrow{\text{verification}}
E_{n+1},
$$

after which \(S_{n+1}\), together with its material related external artifacts, becomes the initial state of the next operation.

The participant may change between any two operations in this model.

Continuity is provided not by personal memory, but by preservation of the working surface.

The working surface is not a closed system, however.

Section 9.10 showed that a project is always connected to an area of meaning that has not yet acquired a sufficient external representation.

User goals, domain knowledge, normative decisions, human values, and new observations may create an **[interpretation remainder][g-interpretation-remainder]** that cannot safely be replaced by existing code or an automated criterion.

The final model therefore cannot be a fully autonomous artifact-transformation cycle.

A more complete picture is:

$$
\text{intent and external reality}
\rightarrow
\text{[sufficient formalization][g-sufficient-formalization]}
\rightarrow
\text{[shared working surface][g-shared-working-surface]}
\rightarrow
\text{execution and observation}
\rightarrow
\text{refinement of knowledge and intent}.
$$

This cycle can repeat.

A new execution reveals a previously unknown constraint.

A person refines the requirement.

An agent constructs a new artifact.

Verification reveals a mismatch.

Part of the [interpretation remainder][g-interpretation-remainder] acquires a persistent representation and moves inside the working surface.

At the same time, a change in the external environment creates new questions.

The boundary of formalization therefore moves continuously.

This makes CHLOYA not a system for describing a project completely in advance, but a system for **progressively materializing knowledge as it is formed**.

[Sufficient formalization][g-sufficient-formalization] performs two opposing functions in this model.

It must move into persistent machine-interpretable state those decisions whose repeated interpretation creates unnecessary cost and risk.

At the same time, it must not conceal, under an appearance of formal precision, questions that have not received a real decision.

The shared language of humans and AI therefore cannot be reduced to programming syntax alone.

Natural language remains necessary for discussing intent that has not yet been formalized.

Domain models connect the system to external reality.

[Project memory][g-project-memory] preserves decision rationales.

Code materializes computational state.

Execution returns observable behavior.

What is shared is not one form of representation, but a **coherent transition between representations**, with software-system state as its central persistent point.

The chapter's title can now be interpreted more precisely.

**“[Code as a shared language][g-code-shared-language] for humans and AI”** is the initial methodological metaphor.

It emphasizes that code is simultaneously available to people, models, and computing systems and can therefore serve as a much stronger mediator than ordinary natural-language dialogue.

The chapter's final meaning is broader:

> **code is not only a language of communication among participants, but the core of a persistent [shared working surface][g-shared-working-surface] on which their actions acquire external state, observable consequences, and the ability to be continued by another participant.**

This representation differs fundamentally from the model

$$
\text{human} \rightarrow \text{prompt} \rightarrow \text{AI} \rightarrow \text{code}.
$$

That model focuses on one act of generation and makes the model's internal state the central mediator between intent and result.

CHLOYA favors another loop:

$$
\text{human} \leftrightarrow
\text{[shared working surface][g-shared-working-surface]}
\leftrightarrow \text{AI},
$$

while the working surface itself is connected to execution and verification tools:

$$
\text{[shared working surface][g-shared-working-surface]}
\leftrightarrow
\text{computing environment}.
$$

People can address the artifacts directly.

AI can address the same artifacts directly.

Engineering tools receive their own access to the formalizable part.

Neither the person nor AI must therefore serve as the sole translator of system state for every other participant.

This reduces dependence on retelling.

When a compiler has produced a report, a model should not be the only source of a claim about the compilation result.

When a change exists in version control, a person can inspect the change itself rather than only the agent's description.

When an architectural decision is recorded in [project memory][g-project-memory], a new model can access it directly rather than requiring the previous model to retell its understanding.

When a user changes a requirement, it can enter the shared loop as new input and change the project's subsequent state.

The [shared working surface][g-shared-working-surface] therefore distributes knowledge and control among participants rather than concentrating them inside one mediator.

This is especially important as agent autonomy grows.

The longer the trajectory of autonomous work, the more dangerous the project's dependence on the executor's hidden internal state becomes.

High autonomy should therefore increase rather than reduce the role of external state.

An agent may perform far more steps independently, but material transitions between them must leave enough observable state for another participant to reconstruct the work from its results when necessary rather than from inaccessible internal reasoning.

This is where the [shared working surface][g-shared-working-surface] becomes trust infrastructure.

It does not guarantee that every decision is correct.

It does make decisions observable, changes bounded, properties verifiable, provenance traceable, and uncertainty transferable.

Trust is consequently built neither on the assumption that an agent always acts correctly nor on requiring a person to repeat every action manually.

It is built on material activity leaving external traces available to independent verification and subsequent participants.

This yields the chapter's final principle:

> **In CHLOYA, code and related artifacts should be designed as a durable [shared working surface][g-shared-working-surface] on which different participants can reconstruct sufficient context, perform bounded transformations, observe and verify their consequences, and transfer state onward without depending on the previous executor's hidden context.**

This principle operates together with the limitation established in 9.10:

> **a [shared working surface][g-shared-working-surface] does not replace human intent or automatically contain all project meaning; it materializes the part that can already be expressed persistently enough, connected to external grounds, and used jointly by different participants.**

Together, these propositions define the role of code in an agent-modular approach.

Code ceases to be only the product of development.

It becomes persistent state of collaborative activity.

AI ceases to be only a generator of program text.

It becomes a temporary participant in controlled transformations of that state.

A person ceases to be only a source of prompts.

The person remains a participant on the shared surface, defining and refining intent, working with the [interpretation remainder][g-interpretation-remainder], and making decisions within their authority.

Engineering tools cease to be merely auxiliary utilities.

They become independent participants in the external observation and verification loop.

Continuity of development is then determined not by continuity of a particular developer, agent, or model, but by the project's ability to preserve its working state between them.

In this sense, code becomes a shared language for humans and AI not because it eliminates their differences, but because it creates a persistent external environment in which those differences no longer prevent collaboration.

[Back to contents](#contents)

## Chapter 9 Conclusion

This chapter began from the idea that code can be regarded as a shared language for humans and AI. The analysis progressively refined that formulation. Code can indeed perform a communicative function, but its significance for agent-modular development is much broader. Together with related [machine-interpretable artifacts][g-machine-interpretable-artifact], it forms a persistent [shared working surface][g-shared-working-surface] through which different participants access project state, change it, observe consequences, verify properties, and transfer the result to further work. A shared surface does not imply that people, AI, and computing tools understand the system identically. It means that a persistent external state exists against which they can coordinate different actions.

This changes the unit of software work itself. In the traditional view, a result is associated primarily with an author: a developer wrote code. A simplified model of generative AI replaces that formula with another: an agent generated code. Both are insufficient for CHLOYA. The material unit becomes a controlled transformation of a known project state in which a participant reconstructs [required context][g-required-context], performs a bounded change, obtains a new state, and leaves external grounds on which the result can be verified and work continued. The center of gravity therefore moves from author to state, from generation to transformation, from a model response to a persistent artifact, and from an individual session to project continuity.

This representation directly extends the rules for governing context and trust. Material project state should not exist primarily in conversation history, a model's internal context, or one specialist's memory. When knowledge becomes stable and important enough for later work, it should acquire an appropriate external representation. Implemented behavior is fixed in code, structural relationships in types and interfaces, verifiable expectations in tests and contracts, long-term decision rationales in [project memory][g-project-memory], instrumental-check results in [verification evidence][g-verification-evidence], and the incomplete state of a particular operation in a form that lets the next participant continue without reconstructing context already acquired.

One CHLOYA objective is therefore not to create an agent capable of retaining an entire project in internal memory, but to create a project capable of giving the next executor minimally sufficient and reliably recoverable working state. The model, role, or person may change. That should not automatically mean the loss of accumulated understanding. In such an architecture, an agent consumes and produces project state but is not its sole carrier. The greater the executor's autonomy, the more important this boundary becomes: a long internal trajectory has limited value if its material outcome leaves no external state available to an independent participant.

This also gives context architecture an economic dimension. Much of the cost of complex development arises not only from creating a change directly, but from acquiring the necessary understanding: finding relationships, reading files, reconstructing decision rationales, performing exploratory execution, and testing hypotheses. If the result of that analysis disappears with a particular session, later participants must pay for the same intellectual work again. [Contextual self-sufficiency][g-context-self-sufficiency], [project memory][g-project-memory], and [state transferability][g-state-transferability] turn part of completed analysis into a reusable project resource. The quality of a working surface is therefore determined not by the amount of preserved text or the size of a context window, but by the cost of a safe subsequent action based on it.

The chapter also establishes the limit of this approach. Not all meaning in a software project already exists in a form that can be placed unambiguously in code, a contract, a test, or another [machine-interpretable artifact][g-machine-interpretable-artifact]. Requirements may be refined during work, domain knowledge may remain partly tacit, and some decisions may depend on human values, organizational goals, and a choice among several technically admissible options. CHLOYA's task is therefore not to eliminate interpretation as such. It is to avoid forcing subsequent participants to reinterpret what has already become sufficiently definite and can be materialized without materially losing meaning.

The human role also changes in this model. It should not be justified solely by the current limitations of AI, because that basis will inevitably become outdated as models improve. Human involvement is especially important where the criterion of correctness still needs to be defined: in forming intent, working with domain meaning, choosing between competing values, determining acceptable risk, and resolving a material [interpretation remainder][g-interpretation-remainder]. As individual decisions stabilize and acquire external representations, some work can move to agents and engineering tools. The human–AI boundary thereby becomes movable, but is determined not only by the executor's intellectual ability, but also by the goal's provenance, authority, and the nature of the decision.

Chapter 9 ultimately moves code from the category of a programming product into the category of collaboration infrastructure. In CHLOYA, code and related artifacts form a persistent working surface on which intent progressively acquires a machine-interpretable representation, changes are performed as controlled state transitions, properties receive external verification bases, and material knowledge is preserved between changing participants. Code becomes a shared language not because it eliminates differences between humans, AI, and computing systems, but because it gives them a sufficiently persistent external basis for working together.

The goal of this approach is neither to transfer all human knowledge into code nor to create a fully autonomous formal system. It is to ensure that knowledge already obtained and sufficiently determined does not remain hidden inside one person, model, or session.

**Executors may change; the project's material working state must remain.**

[Back to contents](#contents)

[g-adr]: ../../research/GLOSSARY.en.md#architecture-decision-record
[g-boundary-object]: ../../research/GLOSSARY.en.md#boundary-object
[g-change-artifact]: ../../research/GLOSSARY.en.md#change-artifact
[g-change-contract]: ../../research/GLOSSARY.en.md#change-contract
[g-change-impact-scope]: ../../research/GLOSSARY.en.md#change-impact-scope
[g-code-shared-language]: ../../research/GLOSSARY.en.md#code-as-a-shared-language
[g-context-debt]: ../../research/GLOSSARY.en.md#context-debt
[g-context-self-sufficiency]: ../../research/GLOSSARY.en.md#contextual-self-sufficiency
[g-continuation-cost]: ../../research/GLOSSARY.en.md#continuation-cost
[g-controlled-state-transformation]: ../../research/GLOSSARY.en.md#controlled-state-transformation
[g-current-state-history-separation]: ../../research/GLOSSARY.en.md#principle-of-separating-current-state-from-history
[g-delocalized-plan]: ../../research/GLOSSARY.en.md#delocalized-plan
[g-executable-artifact]: ../../research/GLOSSARY.en.md#executable-artifact
[g-exploratory-execution]: ../../research/GLOSSARY.en.md#exploratory-execution
[g-external-verification-loop]: ../../research/GLOSSARY.en.md#external-verification-loop
[g-interpretation-remainder]: ../../research/GLOSSARY.en.md#interpretation-remainder
[g-llm]: ../../research/GLOSSARY.en.md#llm
[g-locally-necessary-knowledge]: ../../research/GLOSSARY.en.md#locally-necessary-knowledge
[g-machine-interpretable-artifact]: ../../research/GLOSSARY.en.md#machine-interpretable-artifact
[g-machine-readable-artifact]: ../../research/GLOSSARY.en.md#machine-readable-artifact
[g-minimally-sufficient-change]: ../../research/GLOSSARY.en.md#principle-of-minimally-sufficient-change
[g-project-memory]: ../../research/GLOSSARY.en.md#project-memory
[g-required-context]: ../../research/GLOSSARY.en.md#required-context
[g-shared-working-surface]: ../../research/GLOSSARY.en.md#shared-working-surface
[g-state-transferability]: ../../research/GLOSSARY.en.md#state-transferability
[g-structural-context]: ../../research/GLOSSARY.en.md#structural-context
[g-structural-explicitness]: ../../research/GLOSSARY.en.md#principle-of-structural-explicitness
[g-sufficient-formalization]: ../../research/GLOSSARY.en.md#sufficient-formalization
[g-transferable-state]: ../../research/GLOSSARY.en.md#transferable-state
[g-verifiable-property]: ../../research/GLOSSARY.en.md#verifiable-property
[g-verification-evidence]: ../../research/GLOSSARY.en.md#verification-evidence
[g-verification-scope]: ../../research/GLOSSARY.en.md#verification-scope
