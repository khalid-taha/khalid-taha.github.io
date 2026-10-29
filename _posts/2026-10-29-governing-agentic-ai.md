---
layout: post
title: "Governing Agentic AI: Architectural Principles for Control, Evidence and Accountability"
date: 2026-10-29
author: "Khalid Taha"
permalink: /2026/10/29/governing-agentic-ai.html
---
# Governing Agentic AI: Architectural Principles for Control, Evidence and Accountability

*Moving from trusting AI agents to designing systems in which their actions are authorised, constrained and independently verifiable.*

**Khalid Taha — revised 29 October 2026**

## 1. Introduction: The Autonomy Challenge

Ask an AI agent to prepare a briefing for a delivery partner. It may search internal records, extract facts, consult a model and produce a document. It may then try to send it.

Each step raises different questions. Which records may it read? Which services may process them? What may the partner receive? What evidence will show what happened?

Here, an agent means a system combining a model with a harness: the surrounding tools and execution loop that pursue a goal. Conventional software can also act autonomously. Agents sharpen the governance problem because their chosen routes can change with the information they encounter.

The central question is how we delegate execution without surrendering control. My argument is that authority must be explicit, actions constrained during execution, information handling governed, and conduct assessable independently of the agent's own account.

The contribution proposed here is an architectural synthesis. Established security principles remain essential. The further task is to connect authority over an agent with restrictions on the information it handles, while keeping context selection, execution and verification distinct. These responsibilities apply across organisational work; they do not prescribe a product or a finished implementation.

## 2. From Trust to Enforceable Governance

Instructions explain a task and guide behaviour. They are insufficient controls when compliance depends entirely on the agent interpreting and following them.

Telling a reviewer agent not to edit files leaves that possibility open if it holds unrestricted editing tools. Withholding those capabilities can prevent direct edits through those routes. It cannot guarantee that the review itself is thoughtful or correct.

Established security principles provide foundations: least privilege limits authority; fail-safe defaults require permission; complete mediation requires checking access to protected objects. Applying them to changing agent workflows requires attention to every relevant route. [Saltzer and Schroeder, 1975](https://web.mit.edu/Saltzer/www/publications/protection/Basic.html).

My published *AI-SDLC v1.0 Spec* sets out explicit intent, enforceable constraints, evidence from observed behaviour and named human accountability. These are design requirements, not evidence that a deployment has satisfied them. This essay extends that concern beyond software delivery without importing the specification's entire workflow. [Taha, 2025](https://khalid-taha.github.io/2025/12/27/AI-SDLC-Spec-v1.html).

Prevention and detection also support different claims. Blocking a transfer can prevent disclosure; recording it afterwards supports investigation. Moving controls outside the model still leaves us dependent on the harness, enforcing services, rules and administrators. We must identify those dependencies before claiming independent control.

## 3. Authority, Permissions and Delegation

An objective describes a desired result. Authority defines the actions permitted in pursuing it.

An agent may be permitted to read a confidential report as part of their work on an internal draft. That permission in itself does not give them the right to send the report to an external model service or a partner. Those disclosures must be covered by the applicable authorisation controls, which may establish permissions in advance or evaluate them at execution. Some actions may be permitted automatically; others may require approval. The system must enforce those decisions wherever it accesses, processes or releases information.

Authorisation determines whether an operation is permitted. Human approval is one possible requirement for authorisation. An authorised person may approve an exception only within their own authority. A routine operation can be authorised automatically under established rules.

Five permission questions matter:

- **Access:** may the actor retrieve this information?
- **Use:** may they process it for this purpose?
- **Disclosure:** may they make it available to this recipient or service?
- **Modification:** may they change this resource or authoritative record?
- **Delegation:** may they pass this work and bounded authority to another actor?

These questions overlap. Sending data to a model service can involve both use and disclosure. Distinguishing them does not require five approval stages.

Relevant facts include identity, task, operation, resource, destination and current conditions. Attribute-based access control provides an established basis for evaluating such facts against policy. It does not establish that an agent's claimed purpose is genuine. [NIST SP 800-162](https://csrc.nist.gov/pubs/sp/800/162/upd2/final).

Purpose should connect to an authorised task. Delegated authority needs a defined scope, duration and means of withdrawal. Passing work to another agent cannot create permission the delegator lacked. It may also disclose information to a different role or processing environment, even within the same organisation.

## 4. Separation of Architectural Responsibilities

Three responsibilities make the architecture easier to reason about:

- **Governance** determines what is permitted and under which conditions.
- **Context engineering** selects and assembles useful information, subject to those constraints.
- **Runtime execution** performs operations through tools and services within enforced boundaries.

These are logical responsibilities, not necessarily separate components. Orchestration coordinates work; data and tool responsibilities provide controlled access; verification assesses evidence. Combining responsibilities in one component does not remove their distinct purposes.

Consider retrieval. Context engineering identifies information that could help. Governance establishes whether access and intended use are permitted. The retrieval path enforces the applicable restrictions. Context engineering assembles the returned material, and runtime execution invokes permitted tools. Evidence records support later assessment of those decisions and effects.

This account describes dependencies, not a mandatory sequence of approval stages. Some permissions and restrictions can be established for the task in advance. Others depend on current information at execution. Different controls may enforce different restrictions at different points.

Separately considering access, processing and disclosure does not require a separate human or automated approval gate for each LLM prompt. Task permissions, data-access controls and permitted tool operations must collectively address the applicable restrictions. Whether a particular arrangement does so needs assessment; removing a prompt approval stage does not itself answer that question.

Context engineering therefore cannot turn relevance into permission. Equally, governance does not decide which permitted facts best explain the task. Runtime execution must respect the applicable decisions, while verification examines evidence without granting new authority.

Retrieved content also cannot confer authority merely by containing instructions. A document being analysed and a trusted instruction governing execution have different roles.

This separation helps locate failures. Poor context selection, an incorrect authorisation decision and an execution path that ignores a restriction require different remedies. Section 5 connects the relevant constraints; Section 6 examines what happens when the information changes form.

## 5. Integrating Information Governance and Agent Governance

Agent-centred governance starts with an actor's mandate, scope, tools and permitted actions. Information-centred governance starts with material and its permitted access, uses, transformations and recipients. Neither perspective replaces the other.

This is not an entirely new security problem. Park and Sandhu's usage-control model extends access control to authorisations, obligations, conditions and ongoing controls. It provides useful foundations, although its core model leaves administration and delegation for further work. [Park and Sandhu, 2004](https://profsandhu.com/journals/tissec/p128-park.pdf).

Mike McClain's AEGIS writing highlights protection after information leaves its original environment. He describes controls and evidence travelling with documents. That is his stated approach, not independently verified evidence of control over every copy, transformation or destination. [McClain, “Your Security Protects the Room, Not the Document”](https://www.linkedin.com/posts/mikemcclain_datasecurity-aigovernance-selfprotectingdata-activity-7497708202466099200-PVdP).

My proposed synthesis is that an operation must satisfy both the applicable agent authority and information-handling constraints. Permission to use a summarisation tool does not establish permission to send confidential information to its service. A confidentiality label also provides little protection if an available export route ignores it.

The responsibilities need to exchange enough reliable information to make their controls consistent:

| Responsibility | Information it contributes | What that enables |
|---|---|---|
| Task and agent governance | Actor, task, purpose, scope and delegated authority | Assessment of whether this actor may perform the operation |
| Information governance | Source identity, applicable restrictions and authority to change them | Assessment of permitted processing, recipients and subsequent handling |
| Context engineering | Proposed sources, transformations and intended use | Selection of useful material within those constraints |
| Runtime and enforcing services | Actual operation, destination, conditions and observed outcome | Enforcement and evidence of what occurred |
| Verification and audit | Relevant decisions, records, discrepancies and evidence limits | Assessment without conferring permission |

The table defines logical relationships, not a central service or compulsory approval sequence. A source service might restrict retrieval while a tool boundary limits processing destinations and a release control checks the recipient. Their combined effect must satisfy the applicable constraints. Where decisions depend on shared facts, those facts must remain consistent across the controls.

Restrictions also need an authoritative origin. The organisation must establish who can issue, interpret and change each relevant rule. A label supplied by an agent is not sufficient authority. The system needs a trustworthy association between the information, its restrictions and any authorised change. This principle leaves policy ownership and technical representation to the deployment.

Conditions require careful handling. A prerequisite, such as an authorised recipient, must hold before the operation. A continuing duty, such as restricted retention, needs an accountable owner and a credible means of fulfilment and checking. It cannot be declared complete when processing starts. If it cannot be met, the affected operation needs refusal or an authorised alternative.

Conflicts cannot always be resolved by following the “strictest” rule. Retention and deletion requirements may contradict one another. The agent must not treat unresolved authority as permission, but this does not prescribe a universal conflict hierarchy or halt every unrelated activity. Who may resolve the conflict, and what work may continue, require explicit decisions.

Finally, controls must consider relevant cumulative effects. Several permitted disclosures may reveal a protected fact together. Delegation must preserve the information needed to assess the receiving actor and environment. Attaching restrictions alone cannot establish that the receiver will enforce them.

## 6. Information Provenance and Derived Content

A report becomes notes, notes enter a prompt, and a response becomes a briefing. Meaning may survive while visible source markings disappear.

Provenance records origins and transformations. W3C PROV describes relationships among entities, activities and actors. These can connect source versions, processing steps and resulting artefacts. Provenance does not itself grant authority or enforce policy. [W3C PROV-Overview](https://www.w3.org/TR/prov-overview/).

The governance question concerns what the resulting information exposes. A summary may omit a confidential figure yet preserve other figures from which it can be calculated. Information-flow security has long distinguished permission to access inputs from restrictions on what outputs reveal. Its established methods do not, by themselves, demonstrate control over arbitrary language-model transformations. [Sabelfeld and Myers, 2003](https://www.cs.cornell.edu/andru/papers/jsac/sm-jsac03.pdf).

I propose a cautious default: where derived material exposes protected facts, continue to apply the relevant confidentiality restrictions unless a justified, authorised reassessment supports different handling. Where that exposure is uncertain, do not assume that paraphrasing or shortening makes release permissible.

This is not a universal inheritance rule. Every source restriction need not apply to every derivative. A restriction may concern a particular record, purpose, recipient or period. Reassessment must consider its meaning and authority, rather than automatically combining every source policy forever.

The record should link the derivative to known sources, applicable rules and the basis for any changed treatment. It should also state uncertainty. Missing labels or source links do not establish unrestricted use. Recording model inputs does not show exactly how each input influenced each sentence, nor prove that all relevant sources were captured.

These limits apply to intermediate files, caches, embeddings, logs and agent memory. Source revocation can prevent later retrieval without recovering existing copies or removing their influence from earlier outputs. Provenance helps investigate those relationships; it does not erase them.

## 7. Runtime Enforcement and Control Points

A preventive control must act before the protected effect occurs. Retrieval controls limit incoming records; tool controls constrain processing routes; storage controls govern retained material; release controls restrict recipients. Delegation controls constrain another actor's authority and information access.

Some restrictions can be enforced through capabilities fixed in advance. Others need current facts. Being inside an organisation's network does not itself establish permission. NIST's zero trust architecture similarly rejects implicit trust based solely on network location or ownership. [NIST SP 800-207](https://csrc.nist.gov/pubs/sp/800/207/final).

Coverage determines the strength of the claim. A controlled export tool offers limited protection if an unrestricted browser, shared credential or background process can disclose the same material. The architecture must identify its boundaries and assess bypass routes.

Decisions must remain connected to the actual operation. Permission for one document and recipient cannot justify a materially changed version or destination. Retries must remain within the authorised scope.

Where required authority cannot be established, the affected operation should not proceed. Any reduced operating mode needs defined limits and authority established beforehand. This does not mean an entire system must stop whenever one task encounters a missing decision.

Effective enforcement therefore requires a bounded claim: which actors, routes, resources and effects are covered, and under what assumptions? Coverage must be reassessed when tools, credentials or workflows change.

## 8. Independent Evidence, Verification and Assurance

An agent's account can explain its work. It should not be the sole evidence of compliance.

Three claims need different support:

- **Authorisation:** the operation was permitted under the applicable authority.
- **Correctness:** the result was accurate and suitable for its purpose.
- **Traceability:** relevant events and their relationships can be reconstructed.

A permission record does not prove correctness. A correct result does not prove permission. A detailed history may still omit consequential events.

My article on controlled AI-assisted development argues for explicit scope and review of actual changes. Those practices motivate scrutiny beyond an agent's success report; they do not prove that tests or human review detect every error. [Taha, 2026](https://khalid-taha.github.io/2026/05/30/Building_Software_with_AI_Under_Control.html).

Independence needs a stated reference point. A tool receipt may be independent of the model's narrative while remaining controlled by the same harness or operator. Evidence is stronger against a particular failure when that actor cannot silently alter or suppress it. Another model reviewing the work does not automatically create that separation.

Execution evidence should distinguish an operation being **attempted**, **completed** or having an **unknown outcome**. Its authorisation status is a separate question. Completion does not establish permission, and a missing receipt does not establish that nothing happened.

For a consequential operation with an unknown outcome, reconcile the evidence or use an authorised recovery procedure before repeating it. Otherwise a retry may duplicate an external effect. This is a design requirement, not a prescribed logging mechanism or state machine.

McClain's second *Provable* issue discusses independent capture and missing required records, crediting Brian Long's contribution on non-issuance. Expected evidence must be defined beyond the worker's discretion if omissions are to be detectable. [McClain, 3 September 2026](https://quantaviable.beehiiv.com/p/provable-issue-2).

An expected release receipt can expose an unresolved event within the observed workflow. It cannot establish that every possible disclosure route was observed. Tamper-evident records address alteration after capture, not complete capture or truth. Evidence also needs its own access and retention controls because it may contain protected information.

## 9. Risk, Reversibility and Human Accountability

Controls should reflect consequences, scale, uncertainty and the people affected. NIST's AI Risk Management Framework offers a broader basis for managing risk across a system's lifecycle. [NIST AI RMF 1.0](https://doi.org/10.6028/NIST.AI.100-1).

Some actions can be undone; others require compensation. Some effects cannot be recovered. Deleting a sent document does not remove what its recipient has learned.

McClain's third *Provable* issue discusses reversibility in relation to an action and its recovery window, crediting exchanges with Brad Wolfe. [McClain, 15 September 2026](https://quantaviable.beehiiv.com/p/provable-issue-3). The architectural implication is practical: detection, decision and containment must fit within that window. An available rollback is of little use after the damage has spread.

Human oversight should concentrate where judgement and consequences justify it. Routine actions can proceed under bounded permissions. Higher-risk actions may require a person to review the actual proposal, information and recipient.

Review competence and authority are distinct. Someone may identify a disclosure risk without authority to waive the restriction. One person may hold both responsibilities, but the authority must be explicit.

Accountability continues after execution. Someone must own investigation, containment and recovery, with practical means to intervene. A named owner who cannot observe failures or stop continuing effects provides little effective control.

## 10. Bringing the Principles Together: A Worked Example

Consider an agent preparing a project briefing for an external delivery partner. Sources include a confidential commercial report and an approved partner fact sheet. Its task permits an internal draft; release requires a separate decision.

This hypothetical example assumes three capabilities. Existing task, data-access and tool controls permit the specified sources to be processed through the chosen model service. An authorised human disclosure reviewer and controlled release route are available. The workflow can restrict the information available during regeneration. These are assumptions for the walkthrough, not demonstrated implementation capabilities.

**Establish authority and retrieve.** The task records its requester, purpose, audience and scope. The source service checks access and returns permitted records. Evidence identifies the actor, source versions and applicable restrictions. Context engineering selects useful facts; it cannot enlarge the task's authority or remove information restrictions.

**Prepare the internal draft.** Runtime execution uses the permitted processing route. The example assumes that the existing controls address both tool authority and the source information's handling requirements, including the service relationship. It introduces no separate prompt-exposure approval gate. Whether a deployment can meet that assumption must be assessed before relying on it.

**Assess correctness and disclosure.** The draft accurately reports a £100,000 contract value and £80,000 delivery cost. It omits the margin, which the scenario's policy protects from disclosure to this partner. The reviewer notices that the partner could calculate the £20,000 difference and 20% margin from the draft.

This establishes a problem in this example, not a general ability to detect sensitive inferences. Accuracy does not make the disclosure permissible. The reviewer records the finding, and release remains blocked under the scenario's rules. The review finding does not itself authorise an exception.

**Regenerate with restricted inputs.** The permitted alternative in this scenario is to prepare a new draft from the partner fact sheet, the task and non-sensitive drafting instructions. The new drafting context excludes the confidential source, previous draft, extracted notes and other retained material that could reintroduce those facts. Available retrieval and memory routes must respect that restriction too.

This narrows the information available for regeneration. It does not erase earlier records, provider retention or information potentially held elsewhere. Evidence needed for audit remains protected. If the workflow cannot establish the assumed separation of inputs, it cannot claim that regeneration avoided the restricted material. The new draft still requires disclosure review.

The narrower task is an explicitly permitted alternative within this scenario. It does not settle who should decide whether other tasks continue, narrow or stop when useful context is unavailable.

**Authorise and record release.** The responsible authority permits a specified version for the named recipient after the required review. The release control checks that those are the version and recipient actually used. Evidence links the task, source history, restriction, review, release decision and observed outcome. If the send result is unknown, the workflow records uncertainty and investigates before repeating the operation.

The example connects the responsibilities. Information governance supplies handling limits; agent governance bounds the task and tools; context engineering selects within those limits; runtime controls constrain the actions; verification assesses evidence. No single component has to perform all five roles.

## 11. Limits, Trade-offs and Open Questions

Several decisions remain open. Who resolves conflicting rules? Who decides whether a task proceeds, narrows or stops when necessary context is unavailable? The worked example assumes answers for its own scenario; it does not establish a general allocation of authority.

Derived information remains difficult. We need defensible ways to assess what protected facts a recipient could infer, when restrictions remain relevant, and who may change them. Provenance and human review provide evidence without guaranteeing complete answers.

Distributed controls also face changing facts, delayed updates and incomplete observations. Continuing obligations need accountable handling after the initial operation. Their fulfilment cannot be inferred from an initial permission record.

More checks can increase delay and complexity. Review can become a bottleneck or a formality. More evidence can help investigation while increasing privacy and security exposure. These trade-offs need explicit treatment.

The principles therefore support bounded assurance: identify what the architecture aims to control, what has been tested, which assumptions remain, and who accepts residual risk. This essay proposes responsibilities and relationships. It does not claim complete enforcement, comprehensive inference detection or independently verified implementation.

## 12. Conclusion: Autonomy Without Abandoning Control

Useful autonomy depends on a clear relationship between delegated work and retained authority. An operation must satisfy both the actor's authority and the restrictions on the information involved.

Distinct governance decisions need consistent enforcement, without requiring one decision service or an approval stage for every step. Context selection must work within those boundaries. Evidence must distinguish permission, outcome and correctness, while making uncertainty visible.

People remain accountable for rules, exceptions and consequences. The architectural test is whether we can explain what an agent was authorised to do, how its actions were constrained, and where our evidence and control end.

## References and source notes

Public sources were checked on 29 October 2026. The cited security literature supplies established foundations. The integration proposed here is the author's architectural synthesis. The worked example is hypothetical. Neither the author's publications nor contributors' descriptions are treated as independent implementation audits.

- **Saltzer, Jerome H., and Michael D. Schroeder. 1975.** *The Protection of Information in Computer Systems*, section I.A.3, “Design Principles”. [MIT-hosted text](https://web.mit.edu/Saltzer/www/publications/protection/Basic.html). Supports least privilege, fail-safe defaults and complete mediation.
- **Hu, Vincent C., et al. 2014, updated 2019.** *Guide to Attribute Based Access Control (ABAC) Definition and Considerations*. NIST SP 800-162. [Official publication](https://csrc.nist.gov/pubs/sp/800/162/upd2/final). Supports evaluating subject, object, operation and environmental attributes against policy.
- **Park, Jaehong, and Ravi Sandhu. 2004.** “The UCONABC Usage Control Model”. *ACM Transactions on Information and System Security*, 7(1), 128–174. [Author-hosted paper](https://profsandhu.com/journals/tissec/p128-park.pdf). Supports the discussion of authorisations, obligations, conditions and ongoing usage control; it does not establish the proposed agent architecture.
- **Sabelfeld, Andrei, and Andrew C. Myers. 2003.** “Language-Based Information-Flow Security”. *IEEE Journal on Selected Areas in Communications*, 21(1), 5–19. [Author-hosted paper](https://www.cs.cornell.edu/andru/papers/jsac/sm-jsac03.pdf). Supports the distinction between access control and confidentiality of information revealed through outputs.
- **Groth, Paul, and Luc Moreau, editors. 2013.** *PROV-Overview: An Overview of the PROV Family of Documents*. W3C Working Group Note, 30 April. [W3C text](https://www.w3.org/TR/prov-overview/). Supplies provenance concepts, not an enforcement guarantee.
- **Rose, Scott, Oliver Borchert, Stu Mitchell and Sean Connelly. 2020.** *Zero Trust Architecture*. NIST SP 800-207. [Official publication](https://csrc.nist.gov/pubs/sp/800/207/final).
- **Tabassi, Elham. 2023.** *Artificial Intelligence Risk Management Framework (AI RMF 1.0)*. NIST AI 100-1. [Published edition](https://doi.org/10.6028/NIST.AI.100-1). This essay uses the 2023 edition for general risk-management principles.
- **Taha, Khalid. 2025.** “AI-SDLC v1.0 Spec”, 27 December, especially sections 5–6. [Published specification](https://khalid-taha.github.io/2025/12/27/AI-SDLC-Spec-v1.html). Cited for explicit intent, enforceable constraints, observed evidence and human accountability. These are stated requirements, not evidence of deployment performance.
- **Taha, Khalid. 2026.** “With AI, the hard part is no longer speed”, 30 May. [Published article](https://khalid-taha.github.io/2026/05/30/Building_Software_with_AI_Under_Control.html). Cited for explicit scope and scrutiny of actual changes, without adopting absolute claims about what tests or review prove.
- **McClain, Mike.** LinkedIn post beginning “Your Security Protects the Room, Not the Document”. [Original post](https://www.linkedin.com/posts/mikemcclain_datasecurity-aigovernance-selfprotectingdata-activity-7497708202466099200-PVdP). Publication date not independently established. Cited for his stated AEGIS approach; capabilities are not independently verified here.
- **McClain, Mike. 2026.** “Provable — Issue #2: The week a comment section rebuilt my argument”, 3 September. [Original article](https://quantaviable.beehiiv.com/p/provable-issue-2). Supports attribution of the discussion about independent capture and absent evidence, including Brian Long's contribution on non-issuance. Its claims about implementation maturity are not adopted as independently verified facts.
- **McClain, Mike. 2026.** “Provable — Issue #3: Reversibility Is a Verb”, 15 September. [Original article](https://quantaviable.beehiiv.com/p/provable-issue-3). Attributes the action-and-time distinction to exchanges with Brad Wolfe.
