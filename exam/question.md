​# CCAR-P Practice Quiz: All 120 Questions with Answers and Chapter Tags

Source of questions: `CCAR-P_Interactive_Quiz (1).html.md`. The question text, options, correct answers and explanations below are copied verbatim from that file (extracted programmatically, not retyped).

**What I added**: a chapter tag per question linking it to the book chapter(s) in [book/chapters/](../book/chapters/) that cover the concept. The first chapter listed is the primary one; "also" lists secondary chapters. These tags are my judgement based on the coverage map ([95-coverage-map.md](../book/chapters/95-coverage-map.md)) and the chapter content. The domain number is from the source file.

Questions marked **(Select N)** in the text have multiple correct answers.

## Index by chapter (primary tag)

| Chapter | Questions |
|---|---|
| [Ch 1: What You Are Actually Being Asked to Decide](../book/chapters/01-what-you-are-being-asked-to-decide.md) | Q34, Q41, Q71, Q72, Q74 (5) |
| [Ch 2: Discovery Is Elicitation](../book/chapters/02-discovery-is-elicitation.md) | Q11, Q16, Q40, Q70 (4) |
| [Ch 3: Sizing, Scoping, and the Feasibility Verdict](../book/chapters/03-sizing-scoping-feasibility.md) | Q6, Q32, Q56, Q80, Q113, Q115 (6) |
| [Ch 4: Augmented Call, Workflow, Agent](../book/chapters/04-augmented-call-workflow-agent.md) | Q1, Q27, Q33, Q68, Q75, Q77, Q78, Q83 (8) |
| [Ch 5: When a Second Agent Is a Liability](../book/chapters/05-when-a-second-agent-is-a-liability.md) | Q21, Q29, Q76, Q79 (4) |
| [Ch 6: Reference Architectures and Live State](../book/chapters/06-reference-architectures-and-live-state.md) | Q18, Q73, Q91 (3) |
| [Ch 7: Model, Context Window, Context Strategy](../book/chapters/07-model-context-window-context-strategy.md) | Q7, Q17, Q35, Q47, Q48, Q84, Q85, Q93, Q94 (9) |
| [Ch 8: Prompts as Architecture](../book/chapters/08-prompts-as-architecture.md) | Q10, Q23, Q59, Q60, Q65, Q81, Q82, Q86 (8) |
| [Ch 9: Chunking, Indexing, Retrieval](../book/chapters/09-chunking-indexing-retrieval.md) | Q20, Q89, Q90, Q92 (4) |
| [Ch 10: Entry Points, Routes, Integration](../book/chapters/10-entry-points-routes-integration.md) | Q12, Q25, Q39, Q44, Q45, Q46, Q58, Q64 (8) |
| [Ch 11: The Numbers Before You Build](../book/chapters/11-the-numbers-before-you-build.md) | Q14, Q26, Q37, Q53, Q95, Q98 (6) |
| [Ch 12: Observability at Scale](../book/chapters/12-observability-at-scale.md) | Q3, Q57, Q87, Q88, Q101, Q102 (6) |
| [Ch 13: Evals as Acceptance Criteria](../book/chapters/13-evals-as-acceptance-criteria.md) | Q30, Q31, Q43, Q67, Q96, Q97 (6) |
| [Ch 14: A/B, Shadow, and Not Overclaiming](../book/chapters/14-ab-shadow-and-not-overclaiming.md) | Q8, Q28, Q50, Q63, Q66, Q99, Q100 (7) |
| [Ch 15: The Safety Stack and Guardrail Placement](../book/chapters/15-the-safety-stack-and-guardrail-placement.md) | Q42, Q61, Q103, Q105, Q106, Q108 (6) |
| [Ch 16: Human Review by Stakes](../book/chapters/16-human-review-by-stakes.md) | Q9, Q54, Q104, Q109 (4) |
| [Ch 17: Proving It to Someone Who Was Not There](../book/chapters/17-proving-it-to-someone-who-was-not-there.md) | Q4, Q19, Q22, Q24, Q55, Q107, Q110 (7) |
| [Ch 18: Defending the Design](../book/chapters/18-defending-the-design.md) | Q2, Q49 (2) |
| [Ch 19: Feedback Loops and SLAs](../book/chapters/19-feedback-loops-and-slas.md) | Q36, Q52, Q116, Q117 (4) |
| [Ch 20: Documentation That Survives](../book/chapters/20-documentation-that-survives.md) | Q51, Q62, Q111, Q112, Q114 (5) |
| [Ch 21: Team Enablement and Debugging](../book/chapters/21-team-enablement-and-debugging.md) | Q5, Q13, Q15, Q38, Q69, Q118, Q119, Q120 (8) |

---

## Q1 (Mock Q1)

**Chapter tag**: Ch 4 (Augmented Call, Workflow, Agent) · **Domain 1**: Solution Design & Architecture

**Question**: You are comparing patterns for a batch document-classification job that follows fixed steps: extract metadata, classify, summarize, and persist. Which pattern is the best fit and why?

- **A.** A workflow pattern, because the steps are well-defined and predictable per-request token cost is preferred over flexibility.
- **B.** An agentic pattern, because agents tend to be more accurate than workflows, so this is a reasonable default choice for most classification tasks.
- **C.** An agentic pattern, because the open-ended planning capability of agents produces more consistent structured outputs than a fixed workflow graph on classification tasks.
- **D.** A workflow pattern, because agentic patterns generally cost more per request than a workflow graph, regardless of the task's structure.

**Correct answer**: A

**Explanation**: The steps are fixed and known in advance, so a workflow (predefined code path) fits: per-request cost is predictable and each stage can be audited and retried. Agents are not inherently more accurate or consistent (B, C). D picks the right pattern for the wrong reason: the choice should follow the task's structure, not a blanket cost rule.

---

## Q2 (Mock Q2)

**Chapter tag**: Ch 18 (Defending the Design) · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: An architect at an organization is reviewing two draft communication packages for the same architectural decision. Package 1 contains a threat model, residual-risk register, and control-mapping table. Package 2 contains a list of capabilities delivered and feature-level roadmap dependencies. Which two audiences are correctly matched to these packages? (Select two.)

- **A.** Package 2 → executive sponsor
- **B.** Package 2 → product manager owning the roadmap
- **C.** Package 1 → security and compliance reviewer
- **D.** Package 1 → engineering implementation team
- **E.** Package 2 → security and compliance reviewer

**Correct answers**: B, C

**Explanation**: Package 1 (threat model, residual-risk register, control mapping) is what a security and compliance reviewer needs. Package 2 (capabilities delivered and roadmap dependencies) serves the product manager who owns the roadmap. An executive sponsor needs outcomes, risk and trade-offs rather than a feature list, and the engineering team needs implementation detail rather than a risk register as its primary package.

---

## Q3 (Mock Q3)

**Chapter tag**: Ch 12 (Observability at Scale) · **Domain 3**: Integration

**Question**: You are reviewing instrumentation in a multi-agent system. Which two findings constitute valid observability gaps in the instrumentation? (Select two.) Each correct answer presents a complete solution.

- **A.** Tool-call payloads and outcomes are recorded with redaction applied to known sensitive fields.
- **B.** Request-scoped correlation identifiers do not propagate across agent and tool calls.
- **C.** Latency and token usage on every span are emitted to the central metrics pipeline.
- **D.** Model identity and version on each turn are not recorded with the turn artifacts.
- **E.** Trace spans for each agent step are exported to the shared distributed-tracing backend.

**Correct answers**: B, D

**Explanation**: Without request-scoped correlation IDs you cannot follow one request across agents and tools, and without the model identity and version per turn you cannot attribute a regression to a model change. Options A, C and E describe controls that are already in place (good practice), so they are not gaps.

---

## Q4 (Mock Q4)

**Chapter tag**: Ch 17 (Proving It to Someone Who Was Not There) · **Domain 5**: Governance, Safety & Risk Management

**Question**: You are defining transparency practices for a customer-facing assistant whose responses are materially shaped by AI. Which transparency practice most directly supports responsible deployment?

- **A.** Disclose AI involvement to end users in line with the organization's transparency policy and provide a documented path to reach a human when needed.
- **B.** Disclose AI involvement only to internal staff and operators while withholding that information from the end users whose interactions are materially shaped by the AI system.
- **C.** Disclose AI involvement in the terms of service at signup and rely on that single notice to cover all subsequent interactions.
- **D.** Refuse to answer any user question about how the responses were produced or whether AI was involved, treating the AI's role as confidential operational information.

**Correct answer**: A

**Explanation**: Responsible deployment means telling the people whose interactions are shaped by AI, in line with policy, and giving them a documented route to a human. Hiding it from end users (B), relying on a single sign-up notice (C) or refusing to explain (D) all undermine transparency.

---

## Q5 (Mock Q5)

**Chapter tag**: Ch 21 (Team Enablement and Debugging) · **Domain 7**: Developer Productivity & Operational Enablement

**Question**: You are integrating AI-assisted tooling into the team's documentation workflow. The team wants generated documentation that stays grounded in code. Which integration approach best fits this requirement?

- **A.** Configure subagents that read the relevant code files and draft documentation, then have a single reviewer skim only the summary section before publication.
- **B.** Configure subagents that read the relevant code files and generate documentation, then publish it directly to the team's shared documentation site.
- **C.** Configure subagents that read the relevant code files via filesystem and code-search tools, generate the documentation, and emit changes through the team's normal review workflow.
- **D.** Configure subagents that read a small sample of the repository's files and generate documentation for the whole codebase from the sample, then route it through review.

**Correct answer**: C

**Explanation**: Documentation stays grounded when subagents read the actual code through filesystem and code-search tools and their changes go through the team's normal review. A skim of the summary (A) or direct publishing (B) skips real verification, and a small sample (D) cannot ground documentation for the whole codebase.

---

## Q6 (Mock Q6)

**Chapter tag**: Ch 3 (Sizing, Scoping, and the Feasibility Verdict) · **Domain 1**: Solution Design & Architecture

**Question**: A solutions architect is analyzing stakeholder feedback collected after the first quarter of a Claude-powered procurement automation deployment. The feedback includes four statements: (1) 'Our procurement team is processing 3x more purchase orders per analyst per day.' (2) 'We have eliminated manual data entry role entirely and redeployed those staff to vendor relationship management.' (3) 'The API integration costs are running 40% over projected per-transaction budget.' (4) 'Response latency during end-of-month batch runs is averaging 11 seconds, against our committed 5-second response SLA.' Which of the following correctly identifies the primary business value pillar each stakeholder statement represents?

- **A.** Statement 1: Efficiency; Statement 2: Transformation; Statement 3: Solution Cost; Statement 4: Performance SLA
- **B.** Statement 1: Productivity; Statement 2: Efficiency; Statement 3: Solution Cost; Statement 4: Performance SLA
- **C.** Statement 1: Efficiency; Statement 2: Productivity; Statement 3: Performance SLA; Statement 4: Solution Cost
- **D.** Statement 1: Transformation; Statement 2: Productivity; Statement 3: Solution Cost; Statement 4: Efficiency

**Correct answer**: A

**Explanation**: Processing 3x more orders per analyst is an efficiency gain (more throughput for the same effort). Eliminating a role and redeploying staff to new work changes the operating model, so it is transformation. Running 40% over the per-transaction budget is solution cost. Missing the committed 5-second latency is a performance SLA issue.

---

## Q7 (Mock Q7)

**Chapter tag**: Ch 7 (Model, Context Window, Context Strategy) · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: You are selecting a model for a new production workload and must complete the upstream steps before testing candidate models. Which two steps must be completed BEFORE running a representative sample on a candidate model? (Select two.) Each correct answer presents part of the solution.

- **A.** Select the lightest model that consistently meets the quality bar across the sample.
- **B.** Choose a candidate model based on the requirements profile and known capabilities.
- **C.** Define the quality bar, latency tolerance, and expected volume for the workload.
- **D.** Sign off the production rollout plan with the platform and security teams.
- **E.** Retest the model choice when a new model version becomes available.

**Correct answers**: B, C

**Explanation**: Model selection starts by defining the requirements profile (quality bar, latency tolerance, volume) and then choosing a candidate model from that profile and known capabilities; only then do you run a representative sample. Picking the lightest model that meets the bar (A) happens after testing, production sign-off (D) comes later, and retesting on new versions (E) is an ongoing lifecycle step.

---

## Q8 (Mock Q8)

**Chapter tag**: Ch 14 (A/B, Shadow, and Not Overclaiming) · also Ch 1 · **Domain 4**: Evaluation, Testing & Optimization

**Question**: A research summarization assistant has been deployed for six months. A user has flagged that a generated summary contained a fabricated citation. The product team has asked whether the incident requires architectural action or whether it is an isolated case. Which two Diligence-competency actions should you take? (Select two.) Each correct answer presents part of the solution.

- **A.** Lower the model's sampling temperature across the pipeline in response to the incident.
- **B.** Sample recent summaries to estimate the fabrication frequency across the population.
- **C.** Review whether citation grounding controls exist anywhere in the current generation pipeline.
- **D.** Communicate to users that the assistant does not fabricate output as a matter of design.
- **E.** Disable the assistant immediately for all current users without any prior diagnostic analysis.

**Correct answers**: B, C

**Explanation**: Diligence means measuring before acting: sample recent summaries to estimate how often fabrication happens, and check whether citation-grounding controls exist in the pipeline. Lowering temperature (A) does not fix missing grounding, claiming the assistant never fabricates (D) is false, and disabling it without any diagnosis (E) is a disproportionate reaction.

---

## Q9 (Mock Q9)

**Chapter tag**: Ch 16 (Human Review by Stakes) · also Ch 1 · **Domain 5**: Governance, Safety & Risk Management

**Question**: A customer support team has proposed delegating customer refund decisions to a Claude-driven workflow with no human review for less expensive refunds. The team's reasoning is that small refunds are low-risk and human review would erase the efficiency gain. Which Delegation-competency principle should guide your response?

- **A.** A delegation scope should include human review on every decision the workflow produces, regardless of transaction size.
- **B.** A delegation scope should be set primarily by maximizing efficiency gains across the workflow.
- **C.** Delegation should be avoided in most cases wherever financial transactions occur in the workflow.
- **D.** Delegation should generally include human review on decisions the workflow produces, independent of how small the transaction is.

**Correct answer**: A

**Explanation**: Transaction size is not a reliable proxy for risk: many small refunds add up and are easy to abuse, and accountability for financial decisions must stay with people. The delegation scope should keep human review on these decisions. Optimising purely for efficiency (B) or avoiding delegation entirely (C) are both wrong, and D is a hedged version ('generally') that leaves the gap open.

---

## Q10 (Mock Q10)

**Chapter tag**: Ch 8 (Prompts as Architecture) · also Ch 7, Ch 11 · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: A document analysis service processes legal filings averaging 80,000 tokens each. Each filing is queried by attorneys an average of 14 times during the life of a case. The current architecture sends the full filing on every query. The CFO has asked you to reduce per-query costs while preserving response quality. The security officer requires that filing contents not be stored outside the organization's tenancy. Which optimization approach should you recommend?

- **A.** Move the workload to a smaller Claude model to reduce the per-token cost paid.
- **B.** Cache the filing as the prompt prefix for reuse across the 14 queries per case.
- **C.** Summarize each filing once at intake and run all subsequent queries against the summary.
- **D.** Index filings in a vector store and retrieve only the relevant passages per query.

**Correct answer**: B

**Explanation**: Each 80,000-token filing is re-sent about 14 times, so caching it as the prompt prefix removes most of the repeated input cost and latency while the model still sees the full filing, which preserves quality. A smaller model (A) or a one-time summary (C) risks answer quality. A vector store (D) creates another persistent copy of the filings to govern and can miss passages that a query needs.

---

## Q11 (Mock Q11)

**Chapter tag**: Ch 2 (Discovery Is Elicitation) · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: You are running a discovery session with a business sponsor who asks for "an AI system to fix our customer escalations." Which approach best yields actionable requirements?

- **A.** Defer the discovery session on the grounds that the sponsor must fully specify the system before the architect can ask clarifying or scoping questions.
- **B.** Accept the sponsor's original phrasing as a complete and final requirement and proceed directly to design.
- **C.** Assume the requirement matches the architect's previous engagement in a different industry and proceed with that context.
- **D.** Decompose the request by asking targeted questions about who escalates, what triggers escalation, what good resolution looks like, and which constraints (latency, cost, audit, data sensitivity) apply.

**Correct answer**: D

**Explanation**: Vague asks become actionable requirements when you decompose them with targeted questions: who escalates, what triggers an escalation, what a good resolution looks like, and which constraints apply (latency, cost, audit, data sensitivity). Refusing discovery (A), accepting the phrase as final (B) or reusing assumptions from another industry (C) all skip real requirement gathering.

---

## Q12 (Mock Q12)

**Chapter tag**: Ch 10 (Entry Points, Routes, Integration) · **Domain 3**: Integration

**Question**: You are selecting a protocol for a single low-latency stateless tool call from a Claude-based assistant to an internal pricing service that already exposes a stable HTTP API. Which integration mechanism is the most appropriate?

- **A.** a direct API call to the existing endpoint with the appropriate scoped credentials
- **B.** a bespoke streaming protocol layered over an unrelated asynchronous message bus
- **C.** an agent-to-agent handoff that introduces another Claude-based agent in front of the pricing service
- **D.** a long-lived stateful session protocol maintained between the assistant and the pricing service

**Correct answer**: A

**Explanation**: A single, stateless, latency-sensitive call to a service that already has a stable HTTP API is best served by a direct API call with scoped credentials. A bespoke streaming protocol (B), an extra agent in front of the service (C) or a long-lived stateful session (D) add latency, cost and complexity without any benefit.

---

## Q13 (Mock Q13)

**Chapter tag**: Ch 21 (Team Enablement and Debugging) · also Ch 16 · **Domain 7**: Developer Productivity & Operational Enablement

**Question**: An engineering organization is adopting Claude Code across 200 developers. A team lead has proposed that AI-generated pull requests bypass the standard code review process for changes under 50 lines, on the grounds that small changes are low-risk and review capacity is constrained. Which two Diligence-competency objections should you raise? (Select two.) Each correct answer presents part of the solution.

- **A.** AI-generated pull requests should be rejected as a default policy across the engineering organization.
- **B.** Code review capacity should be expanded to handle every code change submitted across the team.
- **C.** Line count is a poor proxy for the actual risk a code change introduces into the system.
- **D.** The 50-line threshold should be raised to 200 lines instead to capture more changes overall.
- **E.** Removing review removes the verification mechanism that AI-generated output requires across the workflow.

**Correct answers**: C, E

**Explanation**: Line count says little about risk: a two-line change to authentication can be far more dangerous than a 500-line refactor. And AI-generated code needs verification, so removing review removes the main control. Rejecting all AI pull requests (A) or reviewing literally everything with more people (B) are not the objection, and moving the threshold (D) keeps the flawed premise.

---

## Q14 (Mock Q14)

**Chapter tag**: Ch 11 (The Numbers Before You Build) · **Domain 3**: Integration

**Question**: You are operating an interactive assistant whose dominant performance constraint is per-turn latency. Quality on routine turns is already acceptable. Which configuration adjustment most directly improves latency without disproportionately damaging quality?

- **A.** Precompute and cache retrieval embeddings offline, keeping retrieval depth and model tier unchanged.
- **B.** Cache the full corpus in memory ahead of each request.
- **C.** Switch to a smaller model for every turn in place of prompt caching.
- **D.** Reduce retrieval depth to the top-k passages that historically cover the answer, and cache stable system-prompt content.

**Correct answer**: D

**Explanation**: When latency is the dominant constraint and routine quality is already fine, the most direct lever is to send fewer tokens per turn: limit retrieval to the top-k passages that historically contain the answer, and cache the stable system-prompt content. Precomputing embeddings offline (A) is normally already done and barely changes per-turn latency, loading the full corpus (B) does not help, and a smaller model on every turn (C) risks quality and drops caching.

---

## Q15 (Mock Q15)

**Chapter tag**: Ch 21 (Team Enablement and Debugging) · also Ch 7, Ch 10 · **Domain 7**: Developer Productivity & Operational Enablement

**Question**: You are supporting a team whose Claude Code sessions consistently load 60 or more MCP tools from many servers, exhausting context budget before the session begins. Which adjustment most directly addresses this issue without removing capability?

- **A.** Split the workflow across more sessions, each connecting to a smaller subset of servers, so no single session loads every tool definition.
- **B.** Automate the review of the server list before each session and disable servers the engineer thinks are unneeded for that day's task.
- **C.** Raise the session's context window to a larger model tier so all tool definitions fit within the available budget.
- **D.** Enable Tool Search so tool definitions are deferred and discovered on demand rather than loaded into context upfront.

**Correct answer**: D

**Explanation**: Tool Search defers tool definitions and discovers them on demand, so the context is not consumed up front and every tool is still available. Splitting sessions (A) or disabling servers (B) removes capability, and a larger context window (C) still wastes tokens and cost on definitions that are rarely used.

---

## Q16 (Mock Q16)

**Chapter tag**: Ch 2 (Discovery Is Elicitation) · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: You are distinguishing functional from non-functional requirements during discovery. Which item is a non-functional requirement?

- **A.** The system must respond at p95 latency under 800 milliseconds at the expected request volume.
- **B.** The system must produce a draft response that a human reviewer can edit before sending.
- **C.** The system must extract a defined set of specific fields from invoice attachments and populate a downstream data record.
- **D.** The system must classify inbound tickets into a defined set of categories and route each to the owning team.

**Correct answer**: A

**Explanation**: A p95 latency target at an expected volume describes how well the system must perform, so it is a non-functional (quality) requirement. Drafting editable responses, extracting invoice fields and classifying/routing tickets describe what the system does, so they are functional requirements.

---

## Q17 (Mock Q17)

**Chapter tag**: Ch 7 (Model, Context Window, Context Strategy) · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: You are evaluating model-selection claims used by a peer team. For each statement, select yes if the statement is generally true. Otherwise, select no. Select every statement whose answer is "Yes".

- **A.** Heavier-reasoning models typically consume more of the rate limit and run more slowly than lighter models on the same input.
- **B.** A representative-sample evaluation on the target workload is the right basis for confirming a model selection.
- **C.** The most capable model is always the right choice regardless of the workload profile.
- **D.** Tiered routing can serve routine traffic with a lighter model while reserving a heavier model for traffic that needs its capability.
- **E.** Selecting a model based on which version was most recently announced is the right basis for production decisions.

**Correct answers**: A, B, D

**Explanation**: Yes: heavier models use more rate limit and run slower; a representative sample on the real workload is the right basis for confirming a choice; tiered routing sends routine traffic to a lighter model and reserves a heavier one for hard cases. No: the most capable model is not always right (cost, latency and volume matter), and 'most recently announced' is not a selection criterion.

---

## Q18 (Mock Q18)

**Chapter tag**: Ch 6 (Reference Architectures and Live State) · also Ch 9 · **Domain 3**: Integration

**Question**: You are evaluating retrieval-strategy claims used by a peer team. For each claim, select yes if the statement is generally accurate. Otherwise, select no. Select every statement whose answer is "Yes".

- **A.** Dense vector retrieval is well suited to recovering paraphrased intent against unstructured text.
- **B.** Sparse term-matching retrieval recovers exact terms (such as identifiers and rare tokens) more reliably than dense alone.
- **C.** Structured query retrieval is the right fit for filter-and-aggregate workloads against a relational store with schema and indexes.
- **D.** Hybrid retrieval is identical to dense-only retrieval and shares the same recall characteristics.
- **E.** Random sampling of a data store is a sound retrieval strategy for production Q&A.

**Correct answers**: A, B, C

**Explanation**: Yes: dense retrieval handles paraphrased intent in unstructured text; sparse term matching finds exact identifiers and rare tokens more reliably; structured queries fit filter-and-aggregate questions on relational data. No: hybrid retrieval combines dense and sparse and has different (usually better) recall than dense alone, and random sampling is not a retrieval strategy.

---

## Q19 (Mock Q19)

**Chapter tag**: Ch 17 (Proving It to Someone Who Was Not There) · **Domain 5**: Governance, Safety & Risk Management

**Question**: A loan pre-qualification assistant shows 94 percent approval recommendations that match the human underwriter decision. The fairness team reviewed approval rate parity across protected groups and reported no significant difference. A board member has asked whether this evidence is sufficient to declare the assistant fair. Which two Discernment-competency findings should you report? (Select two.) Each correct answer presents part of the solution.

- **A.** Match with human underwriters does not establish freedom from underwriter-introduced bias.
- **B.** A larger sample is needed before any meaningful fairness claim can be made about the model.
- **C.** Approval rate parity does not by itself assess error rate parity across protected groups.
- **D.** The fairness team's review process likely missed at least some of the protected groups studied.
- **E.** The 94 percent match rate is sufficient evidence of fairness for the assistant's decisions.

**Correct answers**: A, C

**Explanation**: Matching human underwriters 94% of the time can simply reproduce the underwriters' own bias, so it does not prove fairness. And equal approval rates across groups say nothing about whether error rates (wrong approvals or wrong denials) are equal. Options B and D are speculation without evidence, and E repeats the flawed claim.

---

## Q20 (Mock Q20)

**Chapter tag**: Ch 9 (Chunking, Indexing, Retrieval) · **Domain 3**: Integration

**Question**: You are designing a retrieval-augmented generation (RAG) pipeline over long technical policy manuals in which answers frequently depend on a section heading and the clauses beneath it. Users report that retrieved passages are often fragments that omit the governing section context. Which chunking strategy most directly addresses this issue?

- **A.** Split documents into fixed 256-token chunks with no overlap to maximize the number of indexed passages.
- **B.** Chunk along the document's structural boundaries (sections and clauses) and prepend the section heading path to each chunk before embedding.
- **C.** Embed each entire manual as a single vector so that no section context is ever lost at retrieval time.
- **D.** Increase top-k retrieval from 5 to 50 so that neighboring fragments are more likely to be returned together.

**Correct answer**: B

**Explanation**: Answers depend on a section heading and the clauses beneath it, so chunks must follow the document's structure and carry the heading path as context before they are embedded. Fixed-size chunks (A) cut through that structure, one vector per manual (C) destroys retrieval precision, and a huge top-k (D) adds noise and cost without guaranteeing the right context.

---

## Q21 (Mock Q21)

**Chapter tag**: Ch 5 (When a Second Agent Is a Liability) · **Domain 1**: Solution Design & Architecture

**Question**: A company is building a research workflow in which a lead agent breaks a market-analysis request into independent sub-questions, assigns them to specialized subagents, and synthesizes the results. Early tests show subagents duplicating each other's work and the lead agent's context filling up with raw search output. Which two design changes should you recommend? (Select two.) Each correct answer presents part of the solution.

- **A.** Have the lead agent give each subagent an explicit objective, output format, and boundary of what is out of scope for its sub-question.
- **B.** Have subagents return condensed findings to the lead agent rather than passing their full raw tool output into its context.
- **C.** Replace the subagents with a single agent that runs every sub-question sequentially in one shared context.
- **D.** Allow every subagent to spawn further subagents without limit so that coverage of each sub-question increases.
- **E.** Give every subagent the full tool set and the complete conversation history of the lead agent by default.

**Correct answers**: A, B

**Explanation**: Duplicated work is fixed by giving each subagent a clear objective, output format and scope boundary. A flooded lead-agent context is fixed by having subagents return condensed findings instead of raw tool output. One sequential agent (C) loses parallelism and context isolation, unlimited spawning (D) multiplies cost and duplication, and giving everyone every tool and the full history (E) causes bloat.

---

## Q22 (Mock Q22)

**Chapter tag**: Ch 17 (Proving It to Someone Who Was Not There) · **Domain 5**: Governance, Safety & Risk Management

**Question**: A European retailer plans to use Claude to analyze customer support transcripts that contain the names, email addresses, and order histories of EU residents. The data protection officer asks what must be in place before processing begins. Which approach best aligns with GDPR obligations?

- **A.** Proceed with processing because the transcripts were collected through the retailer's own support channel.
- **B.** Establish a lawful basis and documented purpose, minimize and pseudonymize personal data before it reaches the model, and confirm the data processing agreement and retention settings with the provider.
- **C.** Remove only the email addresses and send the remaining transcript content unchanged to the model.
- **D.** Instruct the model in the system prompt not to remember any personal data contained in the transcripts.

**Correct answer**: B

**Explanation**: GDPR requires a lawful basis and a documented purpose, data minimisation (for example pseudonymising before the data reaches the model), and a data processing agreement and retention settings with the provider. Owning the channel (A) is not a lawful basis, removing only emails (C) leaves names and order histories, and a prompt instruction (D) is not a data-protection control.

---

## Q23 (Mock Q23)

**Chapter tag**: Ch 8 (Prompts as Architecture) · also Ch 7 · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: A contract-analysis assistant sends a 120,000-token agreement and a short user question on each request. The current prompt places the question first, followed by the full agreement as unstructured text, and answers about clauses deep in the document are frequently incomplete. Which prompt-structure change is most appropriate as the first adjustment?

- **A.** Place the agreement at the top of the prompt wrapped in descriptive XML tags, put the question at the end, and ask the model to quote the relevant clauses before answering.
- **B.** Repeat the user question three times throughout the prompt so that it stays close to every part of the agreement.
- **C.** Split the agreement into separate requests per page and concatenate the individual answers without a synthesis step.
- **D.** Move the agreement into the system prompt as plain text and raise the sampling temperature to encourage broader coverage.

**Correct answer**: A

**Explanation**: For long documents, place the document first in clearly tagged blocks, put the question at the end, and ask the model to quote the relevant clauses before answering; this improves recall of content deep in the document. Repeating the question (B) is noise, per-page requests without synthesis (C) break cross-references, and raising temperature (D) reduces reliability.

---

## Q24 (Mock Q24)

**Chapter tag**: Ch 17 (Proving It to Someone Who Was Not There) · **Domain 5**: Governance, Safety & Risk Management

**Question**: You are building an ethics review checklist for deployments supported by artificial intelligence (AI). Which two checks belong on the list? (Select two.) Each correct answer presents a complete solution.

- **A.** Restrict the ethics review to outputs that exceed a defined model-confidence threshold.
- **B.** Confirm that vendor licensing terms permit the planned production use of the model.
- **C.** Verify that outputs do not rely on generalizations about people that the underlying data does not support.
- **D.** Confirm that high-impact decisions retain human accountability rather than being attributed to the model.
- **E.** Confirm that latency and throughput remain consistent across regions and user populations.

**Correct answers**: C, D

**Explanation**: An ethics checklist should verify that outputs do not rely on generalisations about people that the data does not support, and that high-impact decisions keep human accountability. A confidence threshold (A) leaves low-confidence harms unchecked, licensing (B) is a legal/procurement check, and latency consistency (E) is an operational concern.

---

## Q25 (Mock Q25)

**Chapter tag**: Ch 10 (Entry Points, Routes, Integration) · **Domain 3**: Integration

**Question**: You are reviewing a customer-support agent's configuration. Each candidate tool falls into one of four categories: (1) frequently used and reduces hand-offs, (2) occasionally used to complete a defined task, (3) speculative future utility, (4) never used for any of the agent's defined tasks. Which categories should typically remain in the agent configuration?

- **A.** Category 1 only, because least privilege means the minimal set that completes defined tasks.
- **B.** All 4 categories, because broader tool access tends to help agent performance, whether or not a tool maps to a defined task.
- **C.** Categories 1 and 2 only, because they map to defined tasks and the agent's regular hand-offs.
- **D.** Categories 1, 2, and 3, because retaining occasionally useful tools avoids reconfiguring the agent when new requests arrive.

**Correct answer**: C

**Explanation**: Least privilege keeps the tools needed for the agent's defined tasks, including ones used only occasionally (categories 1 and 2), and removes speculative and unused tools. Keeping only category 1 (A) breaks defined tasks that run occasionally, while keeping everything (B) or speculative tools (D) causes capability bloat and widens the attack surface.

---

## Q26 (Mock Q26)

**Chapter tag**: Ch 11 (The Numbers Before You Build) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: A revenue projection assistant has missed its monthly cost target by 38 percent. Profiling shows three contributors: a 6,000-token policy preamble repeated on every call (45 percent of cost), retrieval of historical sales chunks averaging 3,000 tokens per call (30 percent), and inference on a flagship tier model (25 percent). Stakeholders require that projection accuracy remain unchanged. Which two optimizations should you sequence first to reduce cost without affecting accuracy? (Select two.)

- **A.** Truncate the policy preamble to remove non-essential clauses from the prompt.
- **B.** Cache common retrieved sales chunks accessed across many of the daily queries.
- **C.** Reduce the number of historical sales chunks retrieved across each query run.
- **D.** Enable prompt caching on the static policy preamble across the recurring calls.
- **E.** Switch the workload to a smaller, faster Claude model tier across all queries.

**Correct answers**: B, D

**Explanation**: The constraint is 'no change to accuracy', so start with optimisations that do not alter what the model sees: prompt caching for the static 6,000-token preamble (the largest cost) and caching sales chunks that are retrieved again and again. Truncating the preamble (A), retrieving fewer chunks (C) or a smaller model (E) can all reduce accuracy.

---

## Q27 (Mock Q27)

**Chapter tag**: Ch 4 (Augmented Call, Workflow, Agent) · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: You are designing the prompt for a ticket-triage classifier with thirty well-defined categories and clear category descriptions in the prompt. Which technique is most appropriate as the starting point?

- **A.** a zero-shot prompt that specifies the categories with their descriptions and the required output format
- **B.** a chain-of-thought prompt for a routing decision that does not require multi-step reasoning
- **C.** a prompt with no category descriptions, expecting the model to infer the category set
- **D.** a prompt-chaining setup that routes each ticket through a coarse grouping step before selecting the final category

**Correct answer**: A

**Explanation**: With thirty well-defined categories and clear descriptions in the prompt, a zero-shot prompt that lists them and fixes the output format is the right starting point. Chain-of-thought (B) adds tokens for a decision that needs no multi-step reasoning, removing descriptions (C) hurts accuracy, and a two-step chain (D) adds latency and complexity before you know you need it.

---

## Q28 (Mock Q28)

**Chapter tag**: Ch 14 (A/B, Shadow, and Not Overclaiming) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: A Claude architect observes that after a recent model-version upgrade, grounded responses began including claims not supported by the retrieved source documents. Which mitigation is most directly targeted at this failure mode?

- **A.** scoring each new model version against a stable adversarial evaluation set before promoting it to production
- **B.** treating retrieved passages as untrusted input and screening them with classifiers before they enter the prompt context
- **C.** tightening the retrieval configuration so fewer, higher-relevance passages are returned for each incoming user query
- **D.** constraining responses to source-supported content combined with required citations and a verification step

**Correct answer**: D

**Explanation**: The failure is claims that the retrieved sources do not support. The direct mitigation is to constrain answers to source-supported content, require citations and add a verification step. An adversarial eval gate (A) helps catch future regressions but does not fix this one, screening for injected content (B) targets a different threat, and fewer passages (C) does not stop unsupported additions.

---

## Q29 (Mock Q29)

**Chapter tag**: Ch 5 (When a Second Agent Is a Liability) · also Ch 10 · **Domain 1**: Solution Design & Architecture

**Question**: A managed agent deployment for claims triage has grown from 6 tools to 34 tools over 18 months as product teams added capabilities. Triage accuracy has declined from 91 percent to 78 percent, and average tool selection latency has increased by 2.3 seconds. A junior engineer has proposed adding a tool router agent in front of the current agent to filter the tool list per request. Which two findings should you present to justify capability decomposition before adding the router? (Select two.)

- **A.** Tool descriptions overlap across multiple claim categories within the agent's tool set.
- **B.** The 34 tools serve four distinct claim workflow domains within the triage scope.
- **C.** The proposed router introduces an additional model call on every incoming request.
- **D.** Several tools have not been invoked across the most recent 90 days of traffic.
- **E.** The router pattern is well-documented across publicly available agent literature.

**Correct answers**: A, B

**Explanation**: Overlapping tool descriptions across claim categories and four distinct workflow domains inside one agent are direct evidence that the capability should be decomposed (for example one agent per domain) before you add a router. The router's extra model call (C) is a cost argument, unused tools (D) argue for pruning rather than decomposition, and the popularity of the pattern (E) is not evidence.

---

## Q30 (Mock Q30)

**Chapter tag**: Ch 13 (Evals as Acceptance Criteria) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: You are building an evaluation pipeline for a Claude-based deployment and must complete the specification steps before running the deployment against the dataset. Which two steps must be completed BEFORE running the deployment against the evaluation dataset? (Select two.) Each correct answer presents part of the solution.

- **A.** Review failure cases with subject matter experts to refine the scoring rubric.
- **B.** Define the metrics and slices the framework will report across representative, edge, and adversarial cases.
- **C.** Score the deployment outputs against the reference labels and aggregate the metrics.
- **D.** Curate and label the evaluation dataset to match the defined slices.
- **E.** Publish the aggregated metrics to a dashboard and gate releases on threshold checks.

**Correct answers**: B, D

**Explanation**: Before running the deployment against the dataset you must define the metrics and slices to report, and curate and label a dataset that matches those slices. Scoring (C), reviewing failures with SMEs (A) and publishing dashboards and release gates (E) all come after the run.

---

## Q31 (Mock Q31)

**Chapter tag**: Ch 13 (Evals as Acceptance Criteria) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: You are designing a test strategy for a Claude-based pipeline that handles sensitive financial data. Which two test types should be prioritized to cover both safety-under-attack and cross-component correctness? (Select two.)

- **A.** regression tests against a stable reference set of previously known good outputs
- **B.** adversarial tests using prompt-injection and malformed-input cases
- **C.** integration tests that verify end-to-end pipeline behavior across all components
- **D.** unit tests targeting individual prompt-template rendering logic only
- **E.** smoke tests to verify core paths after each deployment

**Correct answers**: B, C

**Explanation**: Safety under attack calls for adversarial tests (prompt injection, malformed input), and cross-component correctness calls for end-to-end integration tests. Regression tests (A) protect known-good behaviour, unit tests on template rendering (D) are too narrow, and smoke tests (E) only check core paths after a deploy.

---

## Q32 (Mock Q32)

**Chapter tag**: Ch 3 (Sizing, Scoping, and the Feasibility Verdict) · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: You are compiling continuity practices that span the deployment lifecycle. Which two practices belong on the list? (Select two.) Each correct answer presents a complete solution.

- **A.** Maintain a stakeholder register and notify the listed parties at every phase transition event.
- **B.** Carry the evaluation framework and reference set forward across iterations rather than rebuilding each time.
- **C.** Capture lessons learned at the end of each phase and surface them as inputs to the next phase.
- **D.** Archive every phase deliverable in long-term storage to preserve a record of what was produced.
- **E.** Lock decisions made in early phases to prevent revisiting them as later phases begin.

**Correct answers**: B, C

**Explanation**: Continuity across the lifecycle comes from carrying the evaluation framework and reference set forward instead of rebuilding them, and from capturing lessons learned at the end of each phase as input to the next. Notifying everyone at every transition (A) and archiving everything (D) are record-keeping, and locking early decisions (E) blocks learning.

---

## Q33 (Mock Q33)

**Chapter tag**: Ch 4 (Augmented Call, Workflow, Agent) · **Domain 1**: Solution Design & Architecture

**Question**: You are sequencing decomposed components in an invoice-processing pipeline. For each of the decomposed components, select the execution layer it belongs to: 'Pre-Processing', 'Model Stage', or 'Post-Processing'. Which option assigns every item correctly?

- **A.** Claude-based classification of invoice type → Post-Processing; persistence of validated records to the system of record → Model Stage; schema validation of the extracted fields → Post-Processing; Claude-based extraction of structured invoice fields → Model Stage; PII redaction on extracted text prior to model invocation → Pre-Processing; optical character recognition on scanned invoice images → Pre-Processing
- **B.** Claude-based classification of invoice type → Model Stage; persistence of validated records to the system of record → Post-Processing; schema validation of the extracted fields → Post-Processing; Claude-based extraction of structured invoice fields → Model Stage; PII redaction on extracted text prior to model invocation → Pre-Processing; optical character recognition on scanned invoice images → Pre-Processing
- **C.** Claude-based classification of invoice type → Model Stage; persistence of validated records to the system of record → Pre-Processing; schema validation of the extracted fields → Post-Processing; Claude-based extraction of structured invoice fields → Model Stage; PII redaction on extracted text prior to model invocation → Pre-Processing; optical character recognition on scanned invoice images → Post-Processing
- **D.** Claude-based classification of invoice type → Model Stage; persistence of validated records to the system of record → Post-Processing; schema validation of the extracted fields → Post-Processing; Claude-based extraction of structured invoice fields → Pre-Processing; PII redaction on extracted text prior to model invocation → Pre-Processing; optical character recognition on scanned invoice images → Model Stage

**Correct answer**: B

**Explanation**: Pre-Processing happens before the model: OCR on scanned images and PII redaction before invocation. The Model Stage is where Claude works: classifying the invoice type and extracting structured fields. Post-Processing handles the model's output: schema validation of extracted fields and persisting validated records to the system of record.

---

## Q34 (Mock Q34)

**Chapter tag**: Ch 1 (What You Are Actually Being Asked to Decide) · **Domain 1**: Solution Design & Architecture

**Question**: You are reviewing a peer's end-to-end design for a Claude-based platform expected to scale to thousands of concurrent users. For each statement, indicate yes if the statement reflects a sound architectural practice. Otherwise, select no. Select every statement whose answer is "Yes".

- **A.** Authentication and authorization run before retrieval so retrieval can filter by identity.
- **B.** An asynchronous queue absorbs bursty traffic between intake and the model invocation layer.
- **C.** Tax computation is encoded directly in the system prompt rather than in code.
- **D.** Conversation logs include unredacted government identifiers to maximize signal for tuning.

**Correct answers**: A, B

**Explanation**: Sound: authenticate and authorise before retrieval so results can be filtered by identity, and use an asynchronous queue to absorb bursty traffic before model invocation. Not sound: deterministic logic such as tax computation belongs in code, not in a system prompt, and logs must never keep unredacted government identifiers.

---

## Q35 (Mock Q35)

**Chapter tag**: Ch 7 (Model, Context Window, Context Strategy) · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: You are designing a content moderation classifier that processes high volumes of user-generated comments under a tight per-message latency budget using well-defined classification labels. Which model selection best aligns with the workload?

- **A.** Fable
- **B.** Sonnet
- **C.** Haiku
- **D.** Opus

**Correct answer**: C

**Explanation**: High volume, a tight per-message latency budget and well-defined labels describe the profile of the fastest, most cost-efficient tier, Haiku. Sonnet and Opus (and other flagship tiers) add reasoning capacity this task does not need, at higher latency and cost.

---

## Q36 (Mock Q36)

**Chapter tag**: Ch 19 (Feedback Loops and SLAs) · also Ch 1 · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: A pilot AI assistant for procurement specialists shows 89 percent first-response acceptance, but follow-up surveys reveal that specialists frequently override the assistant's vendor recommendations after consulting unrelated criteria the assistant did not consider. The pilot owner wants to ship the assistant as is, given the strong acceptance rate. Which two discernment-competency observations should you raise BEFORE approving the launch? (Select two.) Each correct answer presents part of the solution.

- **A.** The pilot duration was likely too short to establish reliability across the full year.
- **B.** The unconsidered criteria represent a scope gap in the assistant's input space directly.
- **C.** The survey response rate may not be statistically representative of all the specialists.
- **D.** Acceptance does not measure whether recommendations are right after specialist review.
- **E.** The acceptance rate, combined with the pilot's sample size, is enough evidence to proceed without further review.

**Correct answers**: B, D

**Explanation**: Specialists overriding recommendations because of criteria the assistant never saw is a scope gap in its inputs. And first-response acceptance does not show that the recommendations were correct after review. Options A and C are speculative without evidence, and E repeats the flawed argument for launching.

---

## Q37 (Mock Q37)

**Chapter tag**: Ch 11 (The Numbers Before You Build) · **Domain 3**: Integration

**Question**: You are comparing two configurations for an internal compliance Q&A assistant. Configuration X reduces top-k retrieval and serves with a lighter model, lowering p95 latency by 38 percent at a measured 2 percent drop on the accuracy benchmark. Configuration Y keeps top-k and the heavier model, with p95 latency unchanged and no measurable accuracy change. The deployment's stated priorities are accuracy first and latency second. Which configuration is the better recommendation?

- **A.** Configuration X, because lower latency generally matters more than accuracy, independent of this deployment's stated priorities.
- **B.** Configuration X, because a 38 percent latency improvement outweighs a 2 percent accuracy reduction as a general rule across compliance deployments.
- **C.** Configuration Y, because the deployment's stated priority is accuracy first, and Configuration X reduces measured accuracy.
- **D.** Configuration X, because the 2 percent accuracy reduction falls within normal benchmark variance and is not a meaningful regression here.

**Correct answer**: C

**Explanation**: The deployment's stated priorities are accuracy first and latency second, and Configuration X measurably lowers accuracy, so Configuration Y wins. A and B apply generic rules that ignore the stated priorities, and D dismisses a measured regression without evidence that it is noise.

---

## Q38 (Mock Q38)

**Chapter tag**: Ch 21 (Team Enablement and Debugging) · also Ch 10 · **Domain 7**: Developer Productivity & Operational Enablement

**Question**: You are reviewing a peer's Claude Code permission rules for an enterprise rollout. The rules grant unrestricted Bash access to all projects across all developers. Which response is most appropriate?

- **A.** Allow-list Bash to the specific commands the workflows require, relying on the allow-list's implicit default-deny.
- **B.** Replace unrestricted Bash with narrowly-scoped tool patterns that allow only the specific commands the workflows require, and add explicit deny rules for sensitive operations.
- **C.** Replace unrestricted Bash access with narrowly-scoped tool patterns, but apply the same scoped patterns identically across every project regardless of each project's actual workflow needs.
- **D.** Approve the rules as written, treating Bash scoping as a matter for each project team to tighten later.

**Correct answer**: B

**Explanation**: Replace unrestricted Bash with narrowly scoped patterns that allow only the commands the workflows require, and add explicit deny rules for sensitive operations. Relying only on an implicit default-deny (A) leaves dangerous patterns unguarded, identical patterns for every project (C) ignore real needs, and approving as written (D) accepts the risk.

---

## Q39 (Mock Q39)

**Chapter tag**: Ch 10 (Entry Points, Routes, Integration) · **Domain 3**: Integration

**Question**: You are reviewing an integration specification for security gaps. Which two findings constitute valid security gaps in the specification? (Select two.) Each correct answer presents a complete solution.

- **A.** Tool inputs and outputs are encrypted in transit using transport layer security between services.
- **B.** Service credentials are placed in the prompt context where they can leak into logs and traces.
- **C.** Tool calls execute server-side under a least-privilege service principal scoped to the requested action.
- **D.** Role-based access control (RBAC) is enforced only at the response-rendering layer after the model accesses restricted data.
- **E.** Per-user OAuth tokens are exchanged with scope-restricted permissions and refreshed within the active session.

**Correct answers**: B, D

**Explanation**: Credentials placed in the prompt context can leak into logs and traces, and enforcing RBAC only when rendering the response means the model has already read restricted data. TLS in transit (A), least-privilege server-side execution (C) and per-user scoped OAuth (E) are good controls, not gaps.

---

## Q40 (Mock Q40)

**Chapter tag**: Ch 2 (Discovery Is Elicitation) · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: A Claude architect is leading the discovery phase for a new AI-powered customer service solution. Which two activities are characteristic of structured discovery and requirement gathering for a Claude-based deployment? (Select two.) Each correct answer presents a complete solution.

- **A.** facilitating stakeholder workshops to surface latency, accuracy, and compliance constraints before scoping begins
- **B.** deferring constraint documentation until the integration design phase to avoid scope creep
- **C.** generating an initial prototype and iterating based on user reaction
- **D.** documenting explicit success criteria and failure thresholds that will gate production deployment
- **E.** selecting the Claude model tier based on the architect's prior project experience before stakeholder input is collected

**Correct answers**: A, D

**Explanation**: Structured discovery facilitates stakeholder workshops that surface latency, accuracy and compliance constraints before scoping, and documents explicit success criteria and failure thresholds that gate production. Deferring constraints (B), prototyping first and iterating on reactions (C) or choosing a model tier before stakeholder input (E) skip structured discovery.

---

## Q41 (Mock Q41)

**Chapter tag**: Ch 1 (What You Are Actually Being Asked to Decide) · **Domain 1**: Solution Design & Architecture

**Question**: You are a solution architect evaluating candidate use cases for a Claude-based program. For each scenario, select yes if Claude is appropriate as the primary solution at the architectural level. Otherwise, select no. Select every statement whose answer is "Yes".

- **A.** drafting first-pass investigative reports from semi-structured incident logs for analyst review
- **B.** computing real-time fraud scores at sub-50-millisecond latency on a streaming pipeline
- **C.** long-context contract review with structured clause extraction and deviation flagging
- **D.** replacing a vector index for semantic retrieval over a multi-million-document corpus
- **E.** routing inbound support tickets into 30 categories with reasoning for the chosen routing

**Correct answers**: A, C, E

**Explanation**: Yes: drafting first-pass reports from semi-structured logs for analyst review, long-context contract review with clause extraction, and routing tickets into 30 categories with reasoning all play to Claude's language and reasoning strengths. No: sub-50-millisecond streaming fraud scoring needs a specialised low-latency model, and replacing a vector index over millions of documents is a retrieval-infrastructure job, not an LLM job.

---

## Q42 (Mock Q42)

**Chapter tag**: Ch 15 (The Safety Stack and Guardrail Placement) · **Domain 5**: Governance, Safety & Risk Management

**Question**: You are compiling guardrail tactics for a customer-facing assistant. Which two tactics belong on the guardrail list? Each correct answer presents a complete solution. (Select two.)

- **A.** Embed approved override phrases that let trusted users relax guardrails on demand.
- **B.** Validate the model output against a structured schema before downstream actions are taken.
- **C.** Lower sampling temperature globally to reduce the chance of off-policy completions.
- **D.** Layer prompt-level guardrails with runtime content checks rather than relying on either alone.
- **E.** Rely on a single hardened system prompt that enumerates every disallowed behavior.

**Correct answers**: B, D

**Explanation**: Validating output against a structured schema before downstream actions, and layering prompt-level guardrails with runtime content checks, are real guardrails. Override phrases (A) create a bypass, temperature (C) is not a safety control, and relying on a single 'hardened' system prompt (E) is a single point of failure.

---

## Q43 (Mock Q43)

**Chapter tag**: Ch 13 (Evals as Acceptance Criteria) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: You are evaluating an evaluation set used to score a Claude-based hiring-support tool. The set is drawn from one geographic region and one tenure band, while the tool will serve candidates across many regions and tenure bands. Which response is most appropriate?

- **A.** Continue using the narrow evaluation set drawn from one region and one tenure band because the existing benchmark scores are already high on that subset.
- **B.** Expand the evaluation set to cover the geographic regions and tenure bands the tool will serve, and rescore the system on the expanded set before broader release.
- **C.** Replace quantitative evaluation with qualitative impressions from a small pilot group.
- **D.** Narrow the evaluation set to a single demographic subgroup to simplify score interpretation.

**Correct answer**: B

**Explanation**: An evaluation set drawn from one region and one tenure band cannot show how a hiring tool behaves for the populations it will serve. Expand it to the regions and tenure bands in scope and rescore before a broader release. High scores on a narrow subset (A), anecdotal impressions (C) or an even narrower set (D) hide fairness and quality risks.

---

## Q44 (Mock Q44)

**Chapter tag**: Ch 10 (Entry Points, Routes, Integration) · **Domain 3**: Integration

**Question**: You are compiling factors that should drive the choice between Model Context Protocol (MCP), direct API integration, and agent-to-agent handoff. Which two factors belong on the list? (Select two.) Each correct answer presents a complete solution.

- **A.** whether the integration must be portable across multiple AI clients in the ecosystem
- **B.** whether the interaction is stateless and latency-sensitive or stateful and longer-running
- **C.** whether the underlying transport supports encryption in transit between the integrated services
- **D.** whether the organization has a documented naming convention for internal API endpoints
- **E.** whether the team has prior implementation experience with any of the candidate protocols

**Correct answers**: A, B

**Explanation**: Choosing between MCP, a direct API and agent-to-agent handoff depends on whether the integration must be portable across several AI clients (favours MCP) and on whether the interaction is stateless and latency-sensitive (direct API) or stateful and long-running (agent-to-agent). Encryption (C) is required for every option, and naming conventions (D) or prior team experience (E) do not decide the architecture.

---

## Q45 (Mock Q45)

**Chapter tag**: Ch 10 (Entry Points, Routes, Integration) · also Ch 2 · **Domain 3**: Integration

**Question**: A platform team operates a self-hosted multi-agent system on Kubernetes that orchestrates seven specialized agents for invoice processing over an internal message bus. Leadership is evaluating a migration to managed agents, and the security team requires that invoice data never leave the organization's network boundary. Which factor should most heavily influence your recommendation?

- **A.** whether managed agents reduce per-invoice token costs across the existing processing volume
- **B.** whether managed agents support the current bus topology used by the platform team
- **C.** whether the current seven agents map cleanly to the patterns supported by managed agents
- **D.** whether managed agent data handling satisfies the network boundary required by security

**Correct answer**: D

**Explanation**: The security team's network-boundary requirement is a hard constraint: if managed-agent data handling cannot satisfy it, nothing else matters. Token cost (A), bus-topology support (B) and how cleanly the agents map to managed patterns (C) are secondary considerations to evaluate only after the constraint is met.

---

## Q46 (Mock Q46)

**Chapter tag**: Ch 10 (Entry Points, Routes, Integration) · **Domain 3**: Integration

**Question**: You are auditing a procurement-assistant agent whose defined responsibility is to draft purchase requests for review. For each tool currently configured on the agent, select yes if the tool should remain after a least-privilege audit. Otherwise, select no if it should be removed. Select every statement whose answer is "Yes".

- **A.** a read-only catalog lookup tool that returns vendor and SKU information
- **B.** an inbox-send tool that emails purchase requests to vendors directly
- **C.** a draft-write tool that creates purchase-request drafts in the review queue
- **D.** a production-database admin tool unrelated to procurement
- **E.** a read-only policy-document tool that returns the relevant procurement policies

**Correct answers**: A, C, E

**Explanation**: Keep: the read-only catalog lookup, the draft-write tool that puts drafts into the review queue, and the read-only policy-document tool, because they serve the agent's job of drafting purchase requests for review. Remove: the inbox-send tool, which bypasses review by emailing vendors directly, and the unrelated production-database admin tool.

---

## Q47 (Mock Q47)

**Chapter tag**: Ch 7 (Model, Context Window, Context Strategy) · **Domain 3**: Integration

**Question**: You are a solution architect designing a Claude-based assistant with access to 60 internal tools across multiple business domains. Loading every tool definition on every request increases token usage and time to first response. Which design pattern best addresses this issue without sacrificing capability breadth?

- **A.** Use a separate model call to condense all 60 tool definitions into a compact index that is prepended to each user turn for tool selection.
- **B.** Increase the maximum context length so all 60 tool definitions fit within a single request without exceeding the limit.
- **C.** Apply progressive tool discovery so a curated initial subset is exposed and additional tools are loaded on demand based on the task.
- **D.** Group the 60 tools into five fixed categories and load one category per request based on a static mapping of task type to category.

**Correct answer**: C

**Explanation**: Progressive tool discovery exposes a curated initial subset and loads more tools on demand, which cuts tokens and time to first response without losing breadth. Condensing definitions with an extra model call (A) adds latency and still loads everything, a larger context (B) keeps the waste, and fixed static categories (D) break tasks that span domains.

---

## Q48 (Mock Q48)

**Chapter tag**: Ch 7 (Model, Context Window, Context Strategy) · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: You are classifying token-management tactics by where in the request lifecycle each tactic applies: 'Input Preparation', 'Prompt Construction', or 'Output Handling'. Which option assigns every item correctly?

- **A.** Persist the validated output for downstream consumption and audit. → Output Handling; Order the prompt sections so cacheable content sits before per-request content. → Prompt Construction; Summarize prior conversation history when full history is no longer needed. → Input Preparation; Validate the model's structured output against the expected schema. → Output Handling; Move stable repeated content into a cacheable prefix at the head of the prompt. → Prompt Construction; Trim retrieved passages to spans relevant to the user's question. → Input Preparation
- **B.** Persist the validated output for downstream consumption and audit. → Prompt Construction; Order the prompt sections so cacheable content sits before per-request content. → Output Handling; Summarize prior conversation history when full history is no longer needed. → Input Preparation; Validate the model's structured output against the expected schema. → Output Handling; Move stable repeated content into a cacheable prefix at the head of the prompt. → Prompt Construction; Trim retrieved passages to spans relevant to the user's question. → Input Preparation
- **C.** Persist the validated output for downstream consumption and audit. → Output Handling; Order the prompt sections so cacheable content sits before per-request content. → Input Preparation; Summarize prior conversation history when full history is no longer needed. → Input Preparation; Validate the model's structured output against the expected schema. → Output Handling; Move stable repeated content into a cacheable prefix at the head of the prompt. → Prompt Construction; Trim retrieved passages to spans relevant to the user's question. → Prompt Construction
- **D.** Persist the validated output for downstream consumption and audit. → Output Handling; Order the prompt sections so cacheable content sits before per-request content. → Prompt Construction; Summarize prior conversation history when full history is no longer needed. → Input Preparation; Validate the model's structured output against the expected schema. → Output Handling; Move stable repeated content into a cacheable prefix at the head of the prompt. → Input Preparation; Trim retrieved passages to spans relevant to the user's question. → Prompt Construction

**Correct answer**: A

**Explanation**: Input Preparation shapes what goes in: summarising old history and trimming retrieved passages to relevant spans. Prompt Construction arranges the prompt: putting cacheable content before per-request content and moving stable repeated content into a cacheable prefix. Output Handling deals with the result: validating structured output against the schema and persisting validated output for downstream use and audit.

---

## Q49 (Mock Q49)

**Chapter tag**: Ch 18 (Defending the Design) · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: You are presenting an architectural decision to a mixed audience that includes an executive sponsor and the engineering leads who will implement the decision. Which presentation strategy best serves both audiences?

- **A.** Open with a deep technical dive into implementation details for the engineering leads.
- **B.** Announce the chosen decision and move directly to implementation planning.
- **C.** Lead with the decision, the business outcomes it serves, and the trade-offs accepted; follow with the technical rationale, alternatives, and implementation implications for the engineering audience.
- **D.** Present a single undifferentiated narrative that addresses technical and business concerns with equal weight throughout, treating both audiences as requiring the same depth on every section.

**Correct answer**: C

**Explanation**: Mixed audiences are best served by leading with the decision, the business outcomes and the trade-offs accepted (for the executive), then following with the technical rationale, alternatives and implementation implications (for engineering). Opening with deep technical detail (A), announcing without rationale (B) or giving everyone the same depth on every point (D) serves neither group well.

---

## Q50 (Mock Q50)

**Chapter tag**: Ch 14 (A/B, Shadow, and Not Overclaiming) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: A Claude-based research assistant begins producing responses that confidently contradict its retrieved source documents despite no change to the retrieval pipeline. Which two diagnostic actions most directly identify the root cause of this behavior? (Select two.)

- **A.** Switch the retrieval index to a denser embedding model to improve chunk relevance scores.
- **B.** Isolate whether the failure reproduces on the previous model version to test for model mismatch.
- **C.** Increase the context window size to allow more retrieved chunks per query.
- **D.** Inspect system-prompt grounding instructions to determine whether citation constraints remain intact.
- **E.** Reduce the temperature setting to lower response variance across all query types.

**Correct answers**: B, D

**Explanation**: When answers contradict the retrieved sources and retrieval has not changed, test for model mismatch by checking whether the failure reproduces on the previous model version, and inspect whether the system prompt's grounding and citation constraints are still intact. A new embedding model (A), more chunks (C) or lower temperature (E) do not target the root cause.

---

## Q51 (Mock Q51)

**Chapter tag**: Ch 20 (Documentation That Survives) · also Ch 3 · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: You are selecting the documentation set that should accompany a Claude-based deployment at handoff. Which set is most complete?

- **A.** a project retrospective document, a lessons-learned summary, and a list of contributors
- **B.** architecture overview, ADRs, component-level diagrams, runbooks for common operations, on-call playbook, and a list of known limitations
- **C.** the original design proposal, its review comments, meeting notes from design sessions, and the approved requirements document
- **D.** user-facing release notes, a marketing one-pager describing the deployment, and a customer FAQ

**Correct answer**: B

**Explanation**: A complete handoff set lets another team operate the system: architecture overview, ADRs, component diagrams, runbooks for common operations, an on-call playbook and known limitations. Retrospectives (A), design-history artefacts (C) and marketing or user-facing material (D) do not support operation.

---

## Q52 (Mock Q52)

**Chapter tag**: Ch 19 (Feedback Loops and SLAs) · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: You are responding to a stakeholder request that adds significant scope to a deployment already in flight. Which response best aligns expectations while respecting the stakeholder's underlying need?

- **A.** Acknowledge the request, name the scope and timeline implications transparently, and propose options for the stakeholder to choose.
- **B.** Acknowledge the request, explain that the current release is locked, and offer to revisit it once the deployment has shipped.
- **C.** Acknowledge the request, add it to the backlog with a note on its origin, and confirm that it will be considered in the next planning cycle.
- **D.** Accept the additional scope into the current release, extend the timeline to absorb it, and notify the affected teams of the new date.

**Correct answer**: A

**Explanation**: Acknowledge the request, state the scope and timeline implications transparently, and offer options so the stakeholder chooses the trade-off. Refusing because the release is locked (B) or quietly backlogging it (C) ignores the underlying need, and accepting it unilaterally (D) moves dates without the stakeholder making the trade-off.

---

## Q53 (Mock Q53)

**Chapter tag**: Ch 11 (The Numbers Before You Build) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: You are identifying the highest-impact optimization for a deployment whose token cost is dominated by a long, repeated system prompt and a large retrieved context per request. Which optimization most directly targets the dominant cost driver?

- **A.** Batch requests so that several queries share a single call and the system prompt is transmitted once for the whole group.
- **B.** Route simpler requests to a smaller model and reserve the larger model for cases that a lightweight classifier flags as complex.
- **C.** Compress the system prompt by rewriting its instructions more concisely and removing examples that overlap with one another.
- **D.** Move the long, repeated system prompt into a cacheable prefix and trim retrieved context to the spans relevant to each query.

**Correct answer**: D

**Explanation**: The dominant cost drivers are a long repeated system prompt and large retrieved context, so cache the repeated prompt as a prefix and trim retrieval to the relevant spans. Batching (A) does not remove per-query context, routing (B) targets model price rather than the drivers, and compressing the prompt (C) gives smaller savings than caching and may lose instructions.

---

## Q54 (Mock Q54)

**Chapter tag**: Ch 16 (Human Review by Stakes) · **Domain 5**: Governance, Safety & Risk Management

**Question**: You are defining where human review must remain in a planned automated pipeline. Which placement reflects sound human-in-the-loop design?

- **A.** Place a human reviewer between each incoming request and the model so inputs are checked before generation.
- **B.** Place a human reviewer between the model's output and every action, regardless of impact or reversibility.
- **C.** Place a human reviewer between the model's output and any action a confidence score marks as uncertain.
- **D.** Place a human reviewer between the model's output and any high-impact, irreversible action.

**Correct answer**: D

**Explanation**: Human review belongs between model output and actions that are high-impact or irreversible. Reviewing every input (A) or every action (B) destroys the value of automation without adding proportional safety, and a confidence score alone (C) misses confident but wrong high-impact outputs.

---

## Q55 (Mock Q55)

**Chapter tag**: Ch 17 (Proving It to Someone Who Was Not There) · **Domain 5**: Governance, Safety & Risk Management

**Question**: You are preparing a HIPAA-eligible deployment for a healthcare customer. Which configuration supports HIPAA compliance using Anthropic-offered tools?

- **A.** Claude Team with a signed Business Associate Agreement but Zero Data Retention left disabled and audit logging not yet configured for the deployment.
- **B.** Claude Pro with no signed Business Associate Agreement, since a paid consumer subscription is assumed to meet HIPAA requirements out of the box.
- **C.** an ad-hoc personal Claude account used by individual clinicians for PHI-related tasks, with no Business Associate Agreement, no Zero Data Retention, and no audit logging configured
- **D.** Claude Enterprise with a signed Business Associate Agreement, Zero Data Retention enabled, and audit logging configured for compliance tracking

**Correct answer**: D

**Explanation**: Only option D combines everything a HIPAA-eligible deployment needs: a signed Business Associate Agreement on an enterprise offering, a data-retention configuration suited to PHI (Zero Data Retention or the provider's HIPAA-ready setup) and audit logging. Leaving retention and audit logging unconfigured (A), using a consumer plan without a BAA (B) or using personal accounts for PHI (C) do not meet the requirements. In practice, always confirm in the provider's current documentation and your BAA which products and features are covered.

---

## Q56 (Mock Q56)

**Chapter tag**: Ch 3 (Sizing, Scoping, and the Feasibility Verdict) · **Domain 1**: Solution Design & Architecture

**Question**: A healthcare organization is evaluating two Claude-powered AI architectures for a clinical documentation assistant. Architecture X produces higher output quality scores but costs $0.18 per documentation session and averages 4.2 seconds per response. Architecture Y scores slightly lower on quality metric but costs $0.09 per session and averages 2.1 seconds per response. The stated SLA requires responses under 3 seconds, and the annual volume is projected at 2 million documentation sessions. Which evaluation approach correctly applies business value pillar analysis to this decision?

- **A.** Eliminate Architecture X on SLA grounds, then evaluate Architecture Y against the efficiency and solution cost pillars by calculating annual cost difference and assessing whether the quality delta materially impacts clinical workflow productivity.
- **B.** Select Architecture Y based solely on the 50% cost reduction, since solution cost is the most important value pillar in healthcare budget-constrained environments.
- **C.** Recommend a hybrid approach using Architecture X for complex cases and Architecture Y for routine cases, without additional analysis, since this preserves quality where it matters most.
- **D.** Select Architecture X because the higher quality scores justify the cost premium, and any SLA gap can be addressed through infrastructure optimization after deployment.

**Correct answer**: A

**Explanation**: Architecture X averages 4.2 seconds and breaks the 3-second SLA, so it is eliminated first. Architecture Y is then evaluated on solution cost (the annual saving across 2 million sessions) and on whether its slightly lower quality materially affects clinical workflow productivity. Cost-only selection (B), an unanalysed hybrid (C) or ignoring the SLA (D) misapply the value pillars.

---

## Q57 (Mock Q57)

**Chapter tag**: Ch 12 (Observability at Scale) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: You are rolling out monitoring for a Claude-based deployment and must complete the specification steps before instrumenting the deployment to emit metrics and traces. Which two steps must be completed BEFORE instrumenting the deployment? (Select two.) Each correct answer presents part of the solution.

- **A.** Document the dashboards, alerts, and runbooks for the on-call rotation that will respond.
- **B.** Define the metrics and slices the deployment will monitor across normal and adversarial traffic.
- **C.** Tune the alert thresholds based on observed normal-state distributions to reduce false positives.
- **D.** Define the service-level objectives (SLOs) and the error budgets the deployment will be held to.
- **E.** Build the dashboards that surface metrics across slices at the cadence the team operates on.

**Correct answers**: B, D

**Explanation**: Before instrumenting you must define what to measure and the targets: the metrics and slices across normal and adversarial traffic, and the SLOs and error budgets the deployment is held to. Dashboards (E), runbooks (A) and alert tuning based on observed baselines (C) come after the instrumentation exists.

---

## Q58 (Mock Q58)

**Chapter tag**: Ch 10 (Entry Points, Routes, Integration) · **Domain 3**: Integration

**Question**: A security audit uncovers two issues: (1) all end users share a single API key, and (2) tool calls are executed without logging the initiating user identity. Which two mitigations directly address these specific findings? (Select two.)

- **A.** Move credentials out of the prompt context and resolve them from a server-side secret store.
- **B.** Enforce RBAC at the retrieval layer before content enters the model context.
- **C.** Replace the shared API key with per-user OAuth tokens carrying scope-restricted permissions.
- **D.** Add actor attribution to tool-call logs so each call records the initiating user identity.
- **E.** Validate structured outputs against a schema before downstream actions are executed.

**Correct answers**: C, D

**Explanation**: A shared API key is fixed by per-user OAuth tokens with scope-restricted permissions, and missing user identity in tool-call logs is fixed by adding actor attribution to each call. Moving credentials out of the prompt (A), RBAC at retrieval (B) and schema validation (E) are good practices but do not address these two findings.

---

## Q59 (Mock Q59)

**Chapter tag**: Ch 8 (Prompts as Architecture) · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: The compliance team has authored a regulatory disclosure procedure that must be applied identically across customer service, sales, and onboarding workflows. The procedure changes when regulators issue updates, currently four to six times per year. You are designing how the procedure will be packaged for use by Claude across all three workflows. Which two design decisions should you include? (Select two.) Each correct answer presents part of the solution.

- **A.** Package the procedure as a Claude Skill owned by the compliance team directly.
- **B.** Have each workflow team rewrite the procedure for that team's specific context.
- **C.** Embed the procedure text into each workflow's system prompt at integration time.
- **D.** Reference the same Claude Skill from all three of the workflow integrations directly.
- **E.** Store the procedure in a shared retrieval corpus accessed by all three workflows.

**Correct answers**: A, D

**Explanation**: A procedure that must be applied identically in three workflows and changes 4-6 times a year belongs in one Claude Skill owned by the compliance team and referenced by all three workflows, so each update happens in one place. Per-team rewrites (B) and copies embedded in each system prompt (C) drift apart, and a retrieval corpus (E) does not guarantee that the full procedure is applied consistently.

---

## Q60 (Mock Q60)

**Chapter tag**: Ch 8 (Prompts as Architecture) · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: You are reviewing a peer's draft system prompt that contains contradictory instructions: one section says to never speculate beyond the supplied source text and another says to confidently fill in any gaps. Which response is most appropriate?

- **A.** Add a priority-ordering instruction that tells the model to evaluate all available instructions and apply the most contextually appropriate one on each request.
- **B.** Resolve the contradiction by removing or rewording the gap-filling instruction so the prompt consistently constrains the model to source-supported content.
- **C.** Keep both contradictory instructions in place and rely on the model to select which one to follow on each individual request, accepting inconsistent behavior as a result.
- **D.** Keep both contradictory instructions in place and add a third instruction telling the model to use its best judgment based on the query's context.

**Correct answer**: B

**Explanation**: Contradictory instructions make behaviour unpredictable. Resolve the conflict in the prompt itself by removing or rewording the gap-filling instruction so the model stays within the source text. Asking the model to pick the 'most appropriate' instruction (A), accepting inconsistency (C) or adding a 'use judgment' rule (D) leaves the contradiction in place.

---

## Q61 (Mock Q61)

**Chapter tag**: Ch 15 (The Safety Stack and Guardrail Placement) · **Domain 5**: Governance, Safety & Risk Management

**Question**: A Claude architect is implementing safety controls for a customer-facing advice assistant that must never provide regulated investment recommendations. Which two guardrail implementations most directly enforce this constraint? (Select two.)

- **A.** Increase response temperature to introduce variability that reduces the likelihood of specific recommendations.
- **B.** Log all model responses to a SIEM and route flagged records to a compliance reviewer.
- **C.** Add an output classifier that detects and blocks responses containing regulated investment-recommendation language.
- **D.** Define explicit out-of-scope categories in the system prompt with fixed refusal phrasing for investment advice requests.
- **E.** Limit session length to reduce the volume of queries processed per user per day.

**Correct answers**: C, D

**Explanation**: Enforce the constraint directly: an output classifier that detects and blocks regulated investment-recommendation language, plus explicit out-of-scope categories with fixed refusal phrasing in the system prompt. Higher temperature (A) increases unpredictability, logging to a SIEM (B) only detects after the fact, and shorter sessions (E) do not prevent the advice.

---

## Q62 (Mock Q62)

**Chapter tag**: Ch 20 (Documentation That Survives) · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: You are reviewing a peer's draft ADR. The ADR states the decision and the technical detail but does not state the alternatives considered or the trade-offs accepted. Which response is most appropriate?

- **A.** Approve the ADR as written since the decision is documented, treating the missing alternatives and trade-offs as unnecessary detail.
- **B.** Ask the author to add the alternatives considered and the trade-offs accepted before publishing the ADR.
- **C.** Ask the author to link the design-discussion thread in place of a written alternatives section.
- **D.** Publish the ADR as written and open a follow-up task to add alternatives in a later revision.

**Correct answer**: B

**Explanation**: An ADR exists to record why a decision was made, so it must state the alternatives considered and the trade-offs accepted before it is published. Approving it as is (A), linking a discussion thread instead (C) or deferring the missing sections (D) leaves the record incomplete.

---

## Q63 (Mock Q63)

**Chapter tag**: Ch 14 (A/B, Shadow, and Not Overclaiming) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: You are running a controlled experiment to compare two prompts and must complete the design steps before executing the experiment with random assignment. Which two steps must be completed BEFORE executing the experiment? (Select two.) Each correct answer presents part of the solution.

- **A.** Decide whether to promote, reject, or iterate the candidate based on the analysis.
- **B.** Determine the minimum detectable effect size and the sample size needed for power.
- **C.** Define the hypothesis and the primary success metric for the comparison.
- **D.** Monitor interim metrics daily during the experiment and stop as soon as one prompt appears ahead.
- **E.** Document the recommendation, the trade-offs accepted, and the alternatives considered.

**Correct answers**: B, C

**Explanation**: Experiment design comes before execution: define the hypothesis and primary success metric, then determine the minimum detectable effect and the sample size for adequate power. The promotion decision (A) and the write-up (E) come afterwards, and stopping as soon as one prompt looks ahead (D) invalidates the statistics.

---

## Q64 (Exam Guide Sample 1)

**Chapter tag**: Ch 10 (Entry Points, Routes, Integration) · **Domain 3**: Integration

**Question**: A team exposes a customer-support agent that can read tickets, draft replies, issue refunds and delete user accounts. Support staff only ever need to read tickets and draft replies. Applying least-privilege principles, which change best reduces risk?

- **A.** Add audit logging to the refund and delete tools so misuse can be investigated later.
- **B.** Remove the refund and delete tools from the agent configuration entirely.
- **C.** Keep every tool but require a confirmation prompt before refunds and deletions.
- **D.** Move the agent to a larger model that follows instructions more reliably.

**Correct answer**: B

**Explanation**: Least privilege removes capabilities the role does not need, which eliminates the attack surface. Logging (A) and confirmations (C) are detective or compensating controls that leave the capability in place, and model size (D) has nothing to do with authorization scope.

---

## Q65 (Exam Guide Sample 2)

**Chapter tag**: Ch 8 (Prompts as Architecture) · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: An application sends the same 8,000-token system prompt and policy document on every request, followed by a short user message that changes each time. Latency and cost both matter. Which optimization addresses both most directly?

- **A.** Truncate the policy document to its first 1,000 tokens.
- **B.** Switch to the smallest available model regardless of task fit.
- **C.** Put the static system prompt and policy before the dynamic content and enable prompt caching.
- **D.** Move the policy document into a block of few-shot examples.

**Correct answer**: C

**Explanation**: With stable content first, the repeated prefix can be cached and reused, cutting both time to first token and per-request cost without dropping required context. Truncation (A) loses policy, a blind downsize (B) risks quality, and few-shot examples (D) do not create a reusable cached prefix.

---

## Q66 (Exam Guide Sample 3)

**Chapter tag**: Ch 14 (A/B, Shadow, and Not Overclaiming) · also Ch 9 · **Domain 4**: Evaluation, Testing & Optimization

**Question**: A RAG system suddenly returns confident but incorrect answers right after a document refresh. Latency and the model version are unchanged. Where should you investigate first?

- **A.** A silent change to the model weights.
- **B.** The retrieval and indexing step returning stale or irrelevant chunks.
- **C.** A sampling temperature that is set too low.
- **D.** A context window that has become smaller.

**Correct answer**: B

**Explanation**: Only the documents changed, so retrieval is the prime suspect: a broken re-index or mismatched embeddings feed the model poor context. The model and latency are unchanged, and temperature or context size would not be triggered by a document refresh.

---

## Q67 (Community sample (contract review))

**Chapter tag**: Ch 13 (Evals as Acceptance Criteria) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: A contract-review assistant will replace a manual first review. The client requires at least 95% accuracy on each of its five contract types, measured before go-live. On 1,000 contracts already reviewed by lawyers, overall accuracy is 96%. What should the team do next?

- **A.** Go live, because 96% overall accuracy exceeds the 95% requirement.
- **B.** Measure accuracy separately for each contract type and fix any type below 95% before go-live.
- **C.** Switch to the most capable model to raise accuracy further, then go live.
- **D.** Go live and track complaints from the client's lawyers to find weak contract types.

**Correct answer**: B

**Explanation**: The requirement is per contract type, and a 96% aggregate can hide one type well below 95%. Option A relies on the aggregate, C changes the model without checking the per-type requirement, and D measures after go-live although the client requires measurement before it.

---

## Q68 (Community sample (freight quotes))

**Chapter tag**: Ch 4 (Augmented Call, Workflow, Agent) · **Domain 1**: Solution Design & Architecture

**Question**: A retailer uses Claude to process inbound freight quotes. Each quote must first have its costs and service terms extracted, then be validated against procurement policy, and only then turned into a carrier recommendation. The process must be predictable and auditable. Which architecture fits best?

- **A.** A fixed workflow of sequenced LLM calls for extraction, policy validation and recommendation, with checks between steps.
- **B.** A single prompt that interprets each quote and decides on its own whether further processing is needed.
- **C.** An autonomous agent that plans its own steps and chooses tools for every batch of quotes.
- **D.** Parallel LLM calls that extract, validate and recommend at the same time to reduce latency.

**Correct answer**: A

**Explanation**: The steps are known, ordered and dependent, so a prompt-chaining workflow gives predictable cost, intermediate outputs to audit and validation gates between stages. A single prompt (B) hides which stage failed, an agent (C) adds autonomy the task does not need, and parallel calls (D) ignore the data dependencies between stages.

---

## Q69 (Community sample (Claude Code rollout))

**Chapter tag**: Ch 21 (Team Enablement and Debugging) · **Domain 7**: Developer Productivity & Operational Enablement

**Question**: An organization standardizing Claude Code across many teams must enforce security settings that developers cannot override and distribute approved tools and workflows centrally. Which two actions should it take? (Select two.)

- **A.** Run a managed plugin marketplace that distributes approved skills, agents, hooks and MCP servers.
- **B.** Let developers install tools freely and audit local configurations every quarter.
- **C.** Enforce organization-wide controls with server-managed settings that lower levels cannot override.
- **D.** Publish recommended settings in a shared repository and ask each team to apply them.
- **E.** Keep approved tools in project-level configuration so each team can change or disable them.

**Correct answers**: A, C

**Explanation**: Managed settings sit at the top of the settings hierarchy, so project, user, local and command-line settings cannot override them, and a managed marketplace gives one vetted source for extensions. After-the-fact audits (B), recommended settings (D) and team-editable project configuration (E) all allow drift.

---

## Q70 (Authored D1-01)

**Chapter tag**: Ch 2 (Discovery Is Elicitation) · also Ch 3 · **Domain 1**: Solution Design & Architecture

**Question**: A hospital network asks your team to build a Claude assistant that summarizes discharge notes for follow-up care coordinators. The innovation group already has a hackathon prototype and wants to move straight to choosing a model and an agent framework. Before committing to an architecture, which two pieces of information should you capture because they most change the design? (Select two.)

- **A.** The model tier used in the hackathon prototype, so the production design starts from a configuration already shown to work.
- **B.** Whether summaries are needed interactively during calls or can be produced overnight in batch, and the expected daily and peak volume.
- **C.** A complete list of features stakeholders may want in later phases, so the first release can be designed to support all of them.
- **D.** The number of prompting techniques the team intends to compare during the first sprint of prototype refinement.
- **E.** The data classification of the discharge notes and whether each summary must be traceable for audit and compliance review.

**Correct answers**: B, E

**Explanation**: Latency mode and volume (B) decide model tier, queuing, batching and cost; data sensitivity and audit needs (E) decide redaction, retention, hosting and whether a traceable workflow is required. Discovering either late usually forces a redesign. The prototype's model tier (A) is a candidate to test, not a constraint. Speculative future features (C) inflate scope rather than shape the core design, and the number of prompting techniques (D) is an implementation detail decided after the architecture.

---

## Q71 (Authored D1-02)

**Chapter tag**: Ch 1 (What You Are Actually Being Asked to Decide) · also Ch 3 · **Domain 1**: Solution Design & Architecture

**Question**: A payments company scores card transactions with a streaming ML model that must decide within 40 milliseconds. Fraud analysts then spend about 25 minutes per flagged case writing an investigation narrative from transaction history, device data and prior notes. A product manager proposes moving fraud scoring to Claude so every decision comes with a natural-language explanation. What should you recommend?

- **A.** Move scoring to Claude on a lighter model tier with streaming responses, so the 40-millisecond budget is met while explanations are generated.
- **B.** Keep the ML model for real-time scoring and use Claude to draft investigation narratives for flagged cases, which analysts review and finalize.
- **C.** Replace both the ML model and the analysts' narratives with a Claude agent that scores, investigates and closes cases from end to end.
- **D.** Keep the ML model but have Claude re-score every transaction asynchronously, so its explanations can override scores the model gets wrong.

**Correct answer**: B

**Explanation**: Real-time scoring within 40 milliseconds is a job for a specialized low-latency model; an LLM call is too slow and variable for it. The real business pain is the 25-minute narrative, which is unstructured drafting where Claude is strong, and analyst review keeps a human on the decision (B). A lighter tier (A) still cannot reliably meet a millisecond budget. An end-to-end agent (C) removes both the fast scorer and human judgment on high-impact outcomes. Re-scoring every transaction (D) adds cost on the wrong problem and lets a slower component override a purpose-built one.

---

## Q72 (Authored D1-03)

**Chapter tag**: Ch 1 (What You Are Actually Being Asked to Decide) · **Domain 1**: Solution Design & Architecture

**Question**: A customs brokerage uses Claude to read commercial invoices and return the import duty owed for each shipment. The system prompt contains the tariff schedule and instructs the model to calculate duty per line item. Audits find that about 3% of duty amounts are wrong, even when the goods were classified correctly. What is the best architectural change?

- **A.** Add worked calculation examples for each tariff band to the system prompt and ask the model to show its arithmetic step by step.
- **B.** Move to the most capable model tier for the calculation step and keep the lighter tier for reading and classifying invoices.
- **C.** Run the calculation prompt three times per invoice and accept the duty amount that at least two of the three runs agree on.
- **D.** Have Claude extract and classify line items, compute duty in code from the tariff table, and validate results before persisting.

**Correct answer**: D

**Explanation**: Duty is an exact, repeatable calculation, so it belongs in code that is unit-testable and gives the same answer every time. Claude does the language work (reading invoices and classifying goods), code computes the amounts, and post-processing validation runs before records reach the system of record (D). Worked examples or step-by-step reasoning (A), a stronger model (B) and majority voting (C) may lower the error rate but cannot make a model's arithmetic deterministic or auditable.

---

## Q73 (Authored D1-04)

**Chapter tag**: Ch 6 (Reference Architectures and Live State) · also Ch 1 · **Domain 1**: Solution Design & Architecture

**Question**: An expense-processing service calls Claude synchronously from its upload API to extract and categorize receipts. During the last three days of each month, uploads rise about tenfold; the service hits rate-limit errors, uploads time out for employees, and some receipts are silently lost. Most month-end receipts only need to be processed before the finance close two days later. Which two changes best address the problem? (Select two.)

- **A.** Place an asynchronous queue between the upload API and the model layer, with retries and backoff, so uploads are acknowledged immediately.
- **B.** Move the extraction step to the most capable model tier so each request completes faster and fewer retries are needed at peak.
- **C.** Raise the client timeout on the upload API so employees wait until the synchronous model call completes during peak periods.
- **D.** Route non-urgent month-end receipts to batch processing that completes before the finance close, instead of real-time calls.
- **E.** Skip schema validation of extracted fields during month-end peaks and re-validate the affected records the following week.

**Correct answers**: A, D

**Explanation**: A queue (A) decouples intake from the rate-limited model stage: uploads are accepted and stored immediately, nothing is lost, and work is retried with backoff. Because most receipts only need to finish before the close, batch processing (D) absorbs the peak at lower cost. A more capable tier (B) is usually slower and pricier and does not address rate limits. Longer timeouts (C) keep employees waiting and still lose requests. Skipping validation (E) trades a throughput problem for bad data in the system of record.

---

## Q74 (Authored D1-05)

**Chapter tag**: Ch 1 (What You Are Actually Being Asked to Decide) · also Ch 19 · **Domain 1**: Solution Design & Architecture

**Question**: A contract-extraction system has run for nine months. Reviewers correct extracted fields in the review UI before records are saved to the contract repository, but only the final values are stored. Field accuracy has slowly declined as new supplier templates appear, and the team learns about problems only from reviewer complaints. Which change best closes the gap?

- **A.** Store each reviewer correction with the original output, add it to the eval set, and re-run evals before shipping prompt changes.
- **B.** Schedule a quarterly prompt rewrite in which the original developers update instructions based on the error types they remember from complaints.
- **C.** Ask the model to return a confidence score for each field and save fields above a fixed threshold to the repository without reviewer involvement.
- **D.** Switch extraction to the most capable model tier whenever a document arrives from a supplier template that has not been seen before.

**Correct answer**: A

**Explanation**: The architecture lacks a feedback loop. Human corrections are the most valuable signal because they show the right answer; storing them with the original output turns drift into labelled eval cases and lets every change be tested before release (A). Memory-based quarterly rewrites (B) are slow and unmeasured. Self-reported confidence (C) is not a reliable control and removes review exactly where the model is failing. Escalating to a bigger model (D) guesses at the cause and still gives no measurement of whether it helped.

---

## Q75 (Authored D1-06)

**Chapter tag**: Ch 4 (Augmented Call, Workflow, Agent) · **Domain 1**: Solution Design & Architecture

**Question**: A telecom company receives 40,000 support emails a day. About 70% are routine billing or plan questions; the rest are technical faults or contract disputes that need deeper reasoning and different knowledge sources. Today one large prompt on the most capable model handles every email, and both cost and answer quality on routine emails are poor. Which pattern fits best?

- **A.** An autonomous agent with every knowledge source and tool, which decides for each email how many steps to take and which sources to use.
- **B.** Parallel voting, in which three model calls answer each email independently and the most common answer is sent to the customer.
- **C.** Routing, in which a first step classifies each email and sends it to a specialized prompt and model tier for its category.
- **D.** Prompt chaining, in which every email passes through the billing, technical and dispute prompts in sequence before a reply is drafted.

**Correct answer**: C

**Explanation**: The inputs fall into distinct categories that are better handled separately, which is the routing pattern: a classifier sends routine billing questions to a focused prompt on a lighter model and complex cases to stronger, specialised paths (C). An agent (A) adds variable cost and steps to a problem whose structure is known. Voting (B) triples cost on every email without fixing the mismatch between categories. Chaining every email through all three prompts (D) adds cost and latency for steps most emails do not need.

---

## Q76 (Authored D1-07)

**Chapter tag**: Ch 5 (When a Second Agent Is a Liability) · also Ch 4 · **Domain 1**: Solution Design & Architecture

**Question**: Before an architecture review board meeting, a platform team proposes patterns for five Claude workloads. You must flag which proposals are sound so the board can approve them without rework. Which two pairings of workload and pattern are sound? (Select two.)

- **A.** A nightly report that always runs the same four dependent steps, assigned to an autonomous agent so it can adapt each night.
- **B.** An extract, then validate, then summarize pipeline, run as parallel calls because the three stages are separate concerns.
- **C.** A review of one vendor contract for legal, financial and security issues, run as parallel sectioned calls whose findings are merged.
- **D.** Marketing copy with no agreed quality criteria, run as an evaluator-optimizer loop until the evaluator is satisfied with it.
- **E.** A library upgrade whose affected files are only known after analysis, run as orchestrator-workers that plan subtasks at runtime.

**Correct answers**: C, E

**Explanation**: Sectioning (C) fits because the legal, financial and security reviews are independent and can run concurrently before merging. Orchestrator-workers (E) fits because the subtasks cannot be known until the codebase is analysed. A fixed four-step nightly report (A) needs a workflow, not autonomy. Stages where validation needs the extraction output (B) are dependent and must be chained, not parallelised. An evaluator-optimizer loop (D) only helps when there are clear evaluation criteria; without them it iterates without converging.

---

## Q77 (Authored D1-08)

**Chapter tag**: Ch 4 (Augmented Call, Workflow, Agent) · **Domain 1**: Solution Design & Architecture

**Question**: A lender's loan-file assistant uses one long prompt that parses bank statements, computes debt-to-income ratios, checks policy thresholds, flags missing documents and drafts an underwriter memo. About 8% of runs produce a wrong memo, and engineers cannot tell which part of the prompt failed or retry just that part. What decomposition should you recommend?

- **A.** Keep the single prompt but add few-shot examples covering each failure type seen so far, and re-run the whole prompt when a memo looks wrong.
- **B.** Move parsing, ratios and threshold checks into code, and split gap detection and memo drafting into separate, individually tested calls.
- **C.** Convert the prompt into an autonomous agent that decides the order of parsing, calculation and drafting for each loan file it receives.
- **D.** Run the single prompt three times per loan file and send the underwriter whichever memo appears most often across the three runs.

**Correct answer**: B

**Explanation**: Decomposition has two parts: move deterministic stages (parsing, ratio maths, threshold checks) into code, and break the remaining model work into small sub-tasks that can be evaluated, retried and debugged individually (B). That makes the 8% failure traceable to a stage. More examples (A) keep the failure opaque and still require re-running everything. An agent (C) adds variability to steps whose order is already known. Majority voting (D) multiplies cost and hides, rather than locates, the failing step.

---

## Q78 (Authored D1-09)

**Chapter tag**: Ch 4 (Augmented Call, Workflow, Agent) · also Ch 5 · **Domain 1**: Solution Design & Architecture

**Question**: A company is designing an employee-services assistant that will cover payroll questions, leave requests and IT access requests, with about 25 planned tools. Leave balances and access approvals follow fixed policy rules. The first draft puts every tool behind one agent with a single long system prompt. Which two decomposition choices should you make before building? (Select two.)

- **A.** Keep one agent with all 25 tools and write longer tool descriptions so the model can tell similar payroll, leave and access tools apart.
- **B.** Put a router agent in front of the single agent to filter its 25 tools per request, leaving the agent's prompt and scope unchanged.
- **C.** Give each domain agent the complete set of 25 tools so that any agent can still finish a request that happens to cross domains.
- **D.** Compute leave balances and evaluate access-approval rules in code, with Claude extracting the request details and explaining the outcome.
- **E.** Group the tools by business domain into payroll, leave and IT-access agents, each holding only the tools its own workflow needs.

**Correct answers**: D, E

**Explanation**: Decompose along two lines: deterministic policy logic such as balances and approval rules goes into code that behaves the same way every time (D), and capabilities are grouped by business domain so each agent has a small, focused tool set (E). One agent with every tool (A) keeps overlapping choices in one context; better descriptions help but do not remove the bloat. A router (B) treats the symptom of an agent that should not be one agent. Giving every domain agent all tools (C) recreates the bloat and widens the security surface.

---

## Q79 (Authored D1-10)

**Chapter tag**: Ch 5 (When a Second Agent Is a Liability) · **Domain 1**: Solution Design & Architecture

**Question**: A team built a five-agent system to answer employee questions about a single 20-page travel policy: a lead agent delegates to subagents for flights, hotels, meals, per-diem rules and approvals, then merges their answers. Each question is short, the policy fits easily in one context, and token cost is about five times that of the original single-call prototype with no measured quality gain. What should you recommend?

- **A.** Keep the design but move all five subagents to the lightest model tier, so the multi-agent structure stays while per-question cost falls.
- **B.** Add a sixth reviewer subagent that checks the merged answer, so the additional cost buys a measurable improvement in answer quality.
- **C.** Let every subagent read the lead agent's full conversation history, so that fewer clarification rounds are needed between the agents.
- **D.** Return to a single augmented call with the policy in a cacheable prefix, since the task has no real parallelism or context-isolation need.

**Correct answer**: D

**Explanation**: Multi-agent designs multiply token cost and latency and must be justified by real parallel breadth or by material too large for one context. Neither applies here: questions are short, the policy fits in one context, and the extra spend bought no measured quality gain, so a single augmented call with the stable policy cached is the right design (D). A lighter tier (A) cuts unit cost but keeps the unjustified structure. A reviewer agent (B) adds more cost to a design that has not earned it. Sharing full history (C) inflates context and removes the isolation that was the only argument for subagents.

---

## Q80 (Authored D1-11)

**Chapter tag**: Ch 3 (Sizing, Scoping, and the Feasibility Verdict) · **Domain 1**: Solution Design & Architecture

**Question**: Six months after rolling out Claude assistants to a tax advisory firm's associates and its internal engineering group, the CFO asks you to report productivity gains specifically, kept separate from efficiency, transformation, cost and SLA results. Which two stakeholder statements are primarily productivity evidence? (Select two.)

- **A.** Tax associates now spend their afternoons on client advisory work that they previously had no time to take on.
- **B.** Each tax associate now completes about 35% more standard returns per week than before the rollout began.
- **C.** Engineers now spend review time on architecture risks instead of hunting for formatting and naming issues.
- **D.** The firm closed its manual return-preparation desk and moved those staff into a new advisory service line.
- **E.** Peak-season response times stayed within the committed 4-second target throughout the filing deadline.

**Correct answers**: A, C

**Explanation**: Productivity means people produce more valuable output with AI help: associates taking on advisory work (A) and engineers focusing review on architecture risk (C) both describe higher-value work. More standard returns per person (B) is the same work done faster, which is efficiency. Closing a desk and creating a new service line (D) changes roles and the operating model, which is transformation. Meeting a committed response-time target (E) is a performance SLA result.

---

## Q81 (Authored D2-01)

**Chapter tag**: Ch 8 (Prompts as Architecture) · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: A claims-intake assistant writes a free-text reply, and a downstream service parses that text with regular expressions to decide whether to open a case in the claims system. After a prompt update, the integration began failing whenever the model phrased its decision differently, and two malformed decisions were acted on before anyone noticed. Which change most directly fixes the root cause?

- **A.** Lower the sampling temperature so that the model phrases its decision the same way on every request.
- **B.** Add more regular-expression patterns to the parser to cover each new phrasing as it appears in the logs.
- **C.** Add an instruction telling the model to always use the exact wording 'OPEN CASE' or 'NO CASE' in its reply.
- **D.** Request output in a defined JSON schema and validate it in code before the claims service acts on a decision.

**Correct answer**: D

**Explanation**: The root cause is a downstream system depending on unstructured text. Requesting a defined schema states the intent, and validating it in code before acting enforces it, so malformed decisions are rejected or retried instead of executed (D). Lower temperature (A) reduces variation but guarantees nothing and is not a guardrail. More regex patterns (B) chase symptoms and break on the next phrasing. A wording instruction (C) still relies on scraping free text and has no enforcement when the model deviates.

---

## Q82 (Authored D2-02)

**Chapter tag**: Ch 8 (Prompts as Architecture) · also Ch 15 · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: A retail bank's card-support assistant has a system prompt that says only "be careful with sensitive topics." Evaluation shows it sometimes gives investment suggestions and sometimes discusses other customers' accounts, and in a red-team test it followed instructions hidden inside a pasted customer email. Retrieved policy text and the customer message are concatenated with the instructions as plain text. Which two changes should you make to the prompt design? (Select two.)

- **A.** List explicit out-of-scope categories, such as investment advice and other customers' accounts, with a fixed handoff response.
- **B.** Lower the sampling temperature so that responses on sensitive topics become more conservative and repeatable.
- **C.** Log every response that mentions a sensitive topic so that the compliance team can review them each week.
- **D.** Add an instruction telling the model to use its best judgment about which topics are too sensitive to answer.
- **E.** Wrap the policy text and the customer message in separate XML tags and instruct the model to treat them as data.

**Correct answers**: A, E

**Explanation**: Vague safety wording produces inconsistent behaviour; naming the out-of-scope categories with a fixed handoff response makes refusals consistent and testable (A). Separating instructions from retrieved and user content with tags, and telling the model that content is data, is one layer of defence against injected instructions (E). Temperature (B) and logging (C) are not guardrails: they neither define the boundary nor prevent the behaviour. 'Use best judgment' (D) restates the vague instruction that caused the problem.

---

## Q83 (Authored D2-03)

**Chapter tag**: Ch 4 (Augmented Call, Workflow, Agent) · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: A procurement team uses a zero-shot prompt to extract clause types from supplier contracts into a fixed JSON format. Evaluation on 400 labelled contracts shows high accuracy overall, but outputs for multi-party indemnities and clauses amended by later addenda frequently use the wrong field structure. The task description and category definitions are already complete. What is the most appropriate next change?

- **A.** Add step-by-step reasoning instructions to every request so the model works through each clause before answering.
- **B.** Add a few diverse, tagged examples that show the correct output for multi-party indemnities and amended clauses.
- **C.** Move the workload to the most capable model tier so it handles the edge cases without further prompt changes.
- **D.** Add forty examples of the most common clause type so the model sees the target JSON format reinforced many times.

**Correct answer**: B

**Explanation**: The failure is inconsistent format on specific edge cases while the instructions are already complete, which is where a few diverse, clearly marked examples help (B). Chain-of-thought on every request (A) adds tokens and latency for a formatting problem, not a reasoning one. A heavier tier (C) raises cost without addressing the cause and would still need evaluation. Many examples of the common type (D) add tokens and bias the model toward one pattern while leaving the edge cases uncovered.

---

## Q84 (Authored D2-04)

**Chapter tag**: Ch 7 (Model, Context Window, Context Strategy) · also Ch 10 · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: An internal operations agent is connected to 70 tools across HR, finance, facilities and IT. Every tool is used by at least one request type, but a typical request needs only two or three. Tool definitions now account for most of the input tokens on every call, time to first token has grown, and the agent increasingly confuses tools with similar names. Which change best reduces token usage while keeping every capability available?

- **A.** Keep a small core set of tools loaded and let the agent discover the remaining definitions on demand via tool search.
- **B.** Move to a model configuration with a larger context window so all 70 tool definitions fit with room to spare.
- **C.** Shorten every tool description to a single line so that each definition consumes as few tokens as possible.
- **D.** Copy the tool definitions into the system prompt as plain text so they are cached together with the policies.

**Correct answer**: A

**Explanation**: Every definition is sent on every call although few are used. Keeping a core set loaded and deferring the rest behind tool search keeps capability breadth without paying for it up front, and fewer visible tools also improves selection (A). A larger window (B) adds capacity, not efficiency, and leaves cost, latency and confusion unchanged. One-line descriptions (C) save tokens but strip the information the model uses to choose, worsening the similar-name errors. Plain text in the system prompt (D) is not a callable tool definition and still loads everything.

---

## Q85 (Authored D2-05)

**Chapter tag**: Ch 7 (Model, Context Window, Context Strategy) · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: An IT helpdesk assistant runs sessions that often exceed 60 turns. Each request resends the full transcript plus the top ten retrieved knowledge-base articles in full. Per-turn cost and latency rise steadily through a session, and late-session answers increasingly reference fixes from earlier, unrelated issues. You must cut tokens without lowering quality on the evaluation set. Which two changes should you make? (Select two.)

- **A.** Increase retrieval to the top twenty articles so that the answer is more likely to be present somewhere in context.
- **B.** Summarize older turns while keeping recent turns verbatim and key identifiers, decisions and constraints explicit.
- **C.** Remove the out-of-scope and output-format sections from the system prompt to free room for conversation history.
- **D.** Trim retrieved articles to the passages relevant to the current question and drop duplicate or overlapping chunks.
- **E.** Move the assistant to a configuration with a larger context window so that the full transcript always fits.

**Correct answers**: B, D

**Explanation**: Summarizing older turns while keeping recent turns and critical facts explicit removes stale history that both costs tokens and distracts the model (B). Trimming retrieved articles to relevant spans and deduplicating keeps the evidence while dropping noise (D). More articles (A) add noise, cost and latency. Removing critical instructions (C) saves tokens by sacrificing behaviour the product depends on. A larger window (E) lets the noise keep growing and does nothing about the distraction from unrelated earlier issues.

---

## Q86 (Authored D2-06)

**Chapter tag**: Ch 8 (Prompts as Architecture) · **Domain 2**: Claude Models, Prompting & Context Engineering

**Question**: A support assistant sends a 6,000-token system prompt containing the tone guide and return policy, followed by the conversation. Prompt caching was enabled a month ago, but monitoring shows almost no cache hits and no change in time to first token. A review of the request builder finds that the current timestamp and the customer's first name are inserted on the first line of the system prompt. What should you do?

- **A.** Shorten the system prompt below the size at which caching applies, since caching is not producing any savings.
- **B.** Send the policy as a retrieved document after the user message so that the system prompt itself stays small.
- **C.** Move the timestamp and customer name to the end of the request so the static prompt forms an identical prefix.
- **D.** Send a warm-up request every few minutes so that the cached prefix does not expire between customer requests.

**Correct answer**: C

**Explanation**: Caching matches an exact prefix, so per-request values on the first line make every prefix unique and nothing is reused. Moving them to the dynamic tail lets the static tone guide and policy be cached (C). Shrinking the prompt (A) gives up the savings instead of fixing the miss. Placing the policy after the user message (B) puts stable content behind dynamic content, which also prevents reuse. Warm-up requests (D) cannot help when no two real prefixes are identical in the first place.

---

## Q87 (Authored D3-01)

**Chapter tag**: Ch 12 (Observability at Scale) · **Domain 3**: Integration

**Question**: A research assistant built from an orchestrator and five subagents has doubled its monthly model spend over two months. The service dashboard shows total input and output tokens rising, but the team cannot say which subagent or step is responsible. Before changing any configuration, which instrumentation change most directly enables the team to find the root cause?

- **A.** Switch every subagent to the fastest, cheapest model tier and compare next month's total bill with this month's.
- **B.** Add a budget alert that fires when total monthly token spend crosses a fixed threshold set by the finance team.
- **C.** Emit a tracing span for every agent step with its token usage and latency, joined by a propagated correlation ID.
- **D.** Log the full raw prompt and response of every request so engineers can manually review the longest conversations.

**Correct answer**: C

**Explanation**: Cost attribution needs per-step data: a span per agent step carrying tokens and latency, linked by a correlation ID, shows exactly which subagent or step grew (C). A blanket model downgrade (A) acts before measuring, risks quality and still does not say where the cost came from. A budget alert (B) detects overspend but cannot attribute it. Raw prompt logging (D) creates a sensitive, unredacted data copy and leaves engineers guessing instead of querying structured per-span metrics.

---

## Q88 (Authored D3-02)

**Chapter tag**: Ch 12 (Observability at Scale) · **Domain 3**: Integration

**Question**: A post-incident review of a patient-scheduling agent finds two problems: engineers could not reconstruct what a failed rescheduling tool call sent and received, nor which user request triggered it, and several existing log lines contain patient phone numbers copied from tool arguments. Which two changes best address these findings? (Select two.)

- **A.** Log tool-call inputs, outputs and status with known sensitive fields redacted before they reach the log store.
- **B.** Stop logging tool-call payloads entirely and keep only the success or error status code for each call.
- **C.** Copy full unredacted prompts and tool payloads to a separate restricted bucket with longer retention.
- **D.** Run a nightly batch job that scans the log store and deletes any line matching a phone-number pattern.
- **E.** Propagate a request-scoped correlation ID through the agent, every tool call and downstream services.

**Correct answers**: A, E

**Explanation**: Redacted payload logging (A) makes failed tool calls replayable without writing patient identifiers to logs, and a propagated correlation ID (E) links each tool call back to the user request and agent step that triggered it. Dropping payloads (B) removes the very data needed for replay. A separate unredacted bucket (C) creates a second copy of regulated data with weaker controls. A nightly scrubbing job (D) leaves data exposed until it runs and depends on fragile pattern matching instead of redacting at the source.

---

## Q89 (Authored D3-03)

**Chapter tag**: Ch 9 (Chunking, Indexing, Retrieval) · **Domain 3**: Integration

**Question**: A knowledge assistant over 40,000 engineering documents was performing well until last week, when the platform team switched the embedding model used to encode incoming user queries. Since then, answer relevance has dropped sharply across all document types, while the generation model, prompts and latency are unchanged. What is the most appropriate fix?

- **A.** Raise retrieval top-k from 5 to 20 so that relevant passages are more likely to appear somewhere in the returned set.
- **B.** Move generation to the most capable model tier so it can better reason over loosely related passages.
- **C.** Add a system-prompt instruction telling Claude to answer that it does not know when passages look unrelated.
- **D.** Re-embed the whole corpus with the new embedding model, then run a retrieval regression set before releasing.

**Correct answer**: D

**Explanation**: Query vectors from the new embedding model no longer live in the same space as the corpus vectors from the old one, so similarity scores are meaningless; re-embedding the full corpus with the same model and checking a retrieval regression set fixes the root cause (D). A larger top-k (A) returns more mismatched results and adds noise. A stronger generation model (B) cannot repair retrieval that hands it the wrong passages. A refusal instruction (C) hides the symptom while relevance stays broken.

---

## Q90 (Authored D3-04)

**Chapter tag**: Ch 9 (Chunking, Indexing, Retrieval) · also Ch 10 · **Domain 3**: Integration

**Question**: A law firm is designing a RAG pipeline over client contracts and matter files. Partners require that every answer can be traced to the exact clause it relies on, and that lawyers only ever see content from matters they are staffed on. Which two design choices best meet these requirements? (Select two.)

- **A.** Embed each contract as one whole-document vector so every citation points to a complete, self-contained file.
- **B.** Assemble context with stable chunk source IDs, require clause citations, and verify cited IDs were retrieved.
- **C.** Let retrieval search all matters, then hide passages from unstaffed matters in the interface after generation.
- **D.** Capture matter access lists at ingestion as chunk metadata and filter on them at retrieval, before context assembly.
- **E.** Increase top-k so that answers draw on more contracts and are less likely to miss a relevant clause.

**Correct answers**: B, D

**Explanation**: Stable source IDs with required, verified clause citations make every answer auditable down to the clause (B). Capturing access lists as metadata at ingestion and filtering at retrieval keeps unstaffed matters out of the model context entirely (D). Whole-document vectors (A) destroy clause-level precision and cannot point to the exact clause. Hiding content in the interface (C) happens after the model has already read restricted data. A larger top-k (E) adds noise and does nothing for traceability or access control.

---

## Q91 (Authored D3-05)

**Chapter tag**: Ch 6 (Reference Architectures and Live State) · **Domain 3**: Integration

**Question**: Finance analysts ask an internal assistant questions such as total refunds over a given amount by region for last quarter. Refund records live in a relational warehouse with a well-indexed schema. The current design embeds each refund row into a vector index and asks Claude to add up the retrieved rows, and the totals are frequently wrong. Which redesign best fixes this?

- **A.** Give Claude a constrained query tool that runs read-only SQL against the warehouse and explains the returned result.
- **B.** Raise top-k substantially so that more matching refund rows are retrieved before Claude computes each total.
- **C.** Switch the vector index to hybrid dense and keyword retrieval so that exact region names are matched reliably.
- **D.** Route these questions to the most capable model tier so that it performs the multi-row arithmetic more accurately.

**Correct answer**: A

**Explanation**: Filter-and-aggregate questions over relational data belong in the database: a constrained, read-only query tool computes exact totals using the schema and indexes, and Claude explains the result (A). Similarity retrieval returns a handful of similar rows rather than the complete matching set, so a larger top-k (B) still misses rows and bloats context. Hybrid retrieval (C) improves recall for text but still cannot guarantee a complete set for aggregation. A stronger model (D) cannot sum rows it never received.

---

## Q92 (Authored D3-06)

**Chapter tag**: Ch 9 (Chunking, Indexing, Retrieval) · also Ch 6 · **Domain 3**: Integration

**Question**: A SaaS vendor runs one support assistant for many customer tenants over a shared document index. User queries mix paraphrased symptoms such as 'my device will not wake up' with exact error codes such as 'E-4471', and dense-only retrieval often misses the error-code articles. An audit also found one tenant's private runbooks quoted in another tenant's answers. Which two changes best address these issues? (Select two.)

- **A.** Combine dense and sparse keyword retrieval, fuse the ranked results, and rerank the candidates before assembly.
- **B.** Keep dense-only retrieval but replace the current embedding model with a larger general-purpose embedding model.
- **C.** Apply a tenant metadata filter inside retrieval so other tenants' content never competes for the top-k slots.
- **D.** Scan each generated answer and delete sentences that mention another tenant's name before it is shown to users.
- **E.** Raise top-k for any query containing an error code so the exact-match article is more likely to be returned.

**Correct answers**: A, C

**Explanation**: Hybrid retrieval (A) pairs dense matching for paraphrased symptoms with sparse matching for exact codes, and reranking keeps the context small. A tenant metadata filter applied within retrieval (C) stops cross-tenant content from ever reaching the model. A larger embedding model (B) still blurs rare tokens such as error codes. Post-generation scrubbing (D) acts after the model has read another tenant's data and misses content that does not name the tenant. Raising top-k (E) adds noise without fixing the mismatch between query type and retriever.

---

## Q93 (Authored D3-07)

**Chapter tag**: Ch 7 (Model, Context Window, Context Strategy) · also Ch 10 · **Domain 3**: Integration

**Question**: An operations assistant has 45 tools across billing, shipping and returns. A recent audit confirmed that every tool maps to a defined task, but definitions consume a large share of each request, time to first token is high, and Claude sometimes picks the wrong one of several similarly named tools. The team lead proposes deleting the 20 least-used tools. What is the best recommendation?

- **A.** Accept the proposal, since removing the 20 least-used tools reduces both the token load and the selection errors.
- **B.** Keep the core frequently used tools loaded and defer the rest behind tool search with clear, domain-prefixed descriptions.
- **C.** Merge similar tools into a few broad multipurpose tools that take a mode parameter selecting the underlying action.
- **D.** Move to a model with a larger context window so all 45 definitions fit comfortably with room for the conversation.

**Correct answer**: B

**Explanation**: The audit already showed every tool serves a defined task, so this is a context-strategy problem, not capability bloat. Keeping a small core loaded and deferring the rest behind tool search with clear, domain-prefixed descriptions cuts tokens and latency and improves selection while keeping full breadth (B). Deleting legitimate tools (A) breaks defined tasks. Broad mode-switching tools (C) widen each tool's permissions and make selection and validation harder. A bigger window (D) still pays the cost and distraction on every request.

---

## Q94 (Authored D3-08)

**Chapter tag**: Ch 7 (Model, Context Window, Context Strategy) · also Ch 8 · **Domain 3**: Integration

**Question**: An internal assistant's system prompt has grown to include a 30-page compliance procedure, a 20-page brand style guide and several product reference manuals, yet each is relevant to only a minority of requests. Cost and latency have risen, and Claude occasionally applies compliance steps to unrelated requests. Which two changes best address both the cost and the misapplication? (Select two.)

- **A.** Summarize all three bodies of content into a two-page digest that stays in the system prompt on every request.
- **B.** Package the compliance procedure and the style guide as Skills that load their full content only when a task matches.
- **C.** Keep everything in the system prompt but enable prompt caching so the long static prefix is cheaper to reprocess.
- **D.** Move to a model with a larger context window so the full content no longer crowds out the user's conversation.
- **E.** Replace the pasted product manuals with a retrieval tool that fetches only the relevant passages when needed.

**Correct answers**: B, E

**Explanation**: Skills (B) expose a short description and load the full procedure or guide only when a task matches, so unrelated requests neither pay for nor get distracted by them. A retrieval tool (E) brings in just-in-time manual passages instead of whole manuals on every request. A two-page digest (A) loses the detail the procedures need and still sits in every prompt. Prompt caching (C) lowers repeated-prefix cost but leaves the distracting content in context, so misapplication continues. A larger window (D) changes neither the cost nor the distraction.

---

## Q95 (Authored D3-09)

**Chapter tag**: Ch 11 (The Numbers Before You Build) · **Domain 3**: Integration

**Question**: A sales team uses a Claude-based assistant to draft proposal sections from a fixed 6,000-token instruction and template block plus deal notes retrieved per request. Leadership's stated priorities are that draft quality on the evaluation rubric must not drop, and that users should wait less before seeing output. Which change should the architect make first?

- **A.** Serve every draft from a lighter model tier, since lighter models respond faster and most drafts are routine.
- **B.** Halve the maximum output length so that each proposal section finishes generating in roughly half the time.
- **C.** Cache the fixed instruction and template prefix ahead of the deal notes, and stream the draft as it is generated.
- **D.** Reduce retrieved deal notes from eight passages to two so that each request sends fewer tokens to the model.

**Correct answer**: C

**Explanation**: With quality as a hard constraint, start with accuracy-neutral levers: caching the stable 6,000-token prefix (placed before the per-request deal notes) cuts time to first token, and streaming shows output sooner without changing content (C). A lighter model (A), shorter output (B) and fewer retrieved passages (D) can all lower draft quality, so each would need evaluation evidence before adoption and is not the right first move.

---

## Q96 (Authored D4-01)

**Chapter tag**: Ch 13 (Evals as Acceptance Criteria) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: A procurement team is deploying Claude to screen incoming supplier contracts for uncapped indemnity clauses before signature. A missed clause has previously exposed the company to seven-figure liability, while each false flag costs a lawyer about two minutes of review. The team asks which metric should be the primary go-live gate. Which metric should you recommend?

- **A.** Overall accuracy across all clauses in the reviewed contracts, because it summarizes both kinds of error in one number.
- **B.** Recall on uncapped indemnity clauses, with precision tracked as a secondary metric so lawyer review load stays manageable.
- **C.** Precision on flagged indemnity clauses, because every false flag consumes lawyer time that the business wants to reduce.
- **D.** Mean time to complete each contract screen, because the team will only adopt the assistant if signature cycles stay short.

**Correct answer**: B

**Explanation**: A missed indemnity clause is the expensive error, so recall on that clause type is the right primary gate; precision still matters, but only as a secondary constraint, because a false flag costs minutes. Overall accuracy (A) is dominated by the many ordinary clauses and can look high while risky clauses are missed. Optimizing precision (C) favors the cheap error over the expensive one. Screening time (D) is an operational metric that says nothing about whether risky clauses are caught.

---

## Q97 (Authored D4-02)

**Chapter tag**: Ch 13 (Evals as Acceptance Criteria) · also Ch 11 · **Domain 4**: Evaluation, Testing & Optimization

**Question**: An IT service desk agent resolves tickets by calling Claude several times per ticket, with tool lookups and occasional retries. The contract SLA states that 95 percent of chat replies must arrive within six seconds, and finance wants to compare the current setup with a cheaper model tier that may need more retries. Which two metrics should the evaluation report to support both decisions? (Select two.)

- **A.** p95 response latency per chat reply, measured against the six-second SLA target.
- **B.** Average response latency across all chat replies, reported as a weekly trend line.
- **C.** Cost per API call at list price for each of the model tiers under consideration.
- **D.** Total monthly token volume across all tickets, compared between the two tiers.
- **E.** Cost per resolved ticket, including retries and tool round-trips for each tier.

**Correct answers**: A, E

**Explanation**: The SLA is stated as a percentile, so p95 latency per reply (A) is the matching metric; an average (B) hides the slow tail that users and the SLA care about. For an agent, one ticket needs several calls and possibly retries, so cost per resolved ticket (E) is the honest comparison. Cost per call (C) makes a cheaper tier look better even if it needs more retries, and total monthly tokens (D) is not normalized to completed work and ignores price differences between tiers.

---

## Q98 (Authored D4-03)

**Chapter tag**: Ch 11 (The Numbers Before You Build) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: Every night a support platform re-classifies about 200,000 closed tickets for a weekly trends report that executives read on Monday. The classification prompt and model tier were validated last quarter, and accuracy must not change. The nightly job now costs more than the live chat assistant, and nobody needs its results before morning. Which change should you make first?

- **A.** Concatenate twenty tickets into each request so the long classification prompt is sent once per group of tickets.
- **B.** Move the nightly job to the smallest model tier, since closed-ticket classification is low risk for the business.
- **C.** Truncate each ticket to its first few hundred tokens so that every classification request is shorter and cheaper.
- **D.** Submit the unchanged requests through the Message Batches API for asynchronous processing at the lower batch price.

**Correct answer**: D

**Explanation**: The workload is non-urgent and the validated prompt and model must not change, so asynchronous batch processing (D) lowers cost without altering what the model sees. Packing many tickets into one call (A) merges unrelated tasks, complicates parsing and risks cross-contamination, so it changes behavior. A smaller tier (B) and truncation (C) are quality-affecting levers that would need new evals, and the stated constraint is that accuracy must not change.

---

## Q99 (Authored D4-04)

**Chapter tag**: Ch 14 (A/B, Shadow, and Not Overclaiming) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: A team is A/B testing a revised prompt for a claims-intake assistant, with random assignment by user and a planned sample size that will be reached on day 14. On day 3, the variant leads on the primary metric by six points with a p-value under 0.05, and all guardrail metrics are within limits. The product manager wants to stop the test and promote the variant today. What should you advise?

- **A.** Continue to the planned sample size and decide then, stopping early only if a guardrail metric is breached.
- **B.** Stop the test and promote the variant now, because the result is already statistically significant.
- **C.** Stop the test and start a new one with three more variants to find an even stronger prompt.
- **D.** Promote the variant now for the user segments where its lead is largest, and keep testing the rest.

**Correct answer**: A

**Explanation**: Peeking and stopping as soon as a variant looks ahead inflates false positives; early leads are often noise even when one interim check shows significance. The decision belongs at the planned sample size, with early stops reserved for guardrail breaches (A). Promoting now (B) is exactly the early-stop error. Restarting with more variants (C) discards valid data and adds no evidence. Promoting by segment (D) chases subgroups chosen after looking at the results, which compounds the problem.

---

## Q100 (Authored D4-05)

**Chapter tag**: Ch 14 (A/B, Shadow, and Not Overclaiming) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: In an A/B test for a multilingual support assistant, variant B combined a rewritten system prompt with a higher retrieval top-k. At the planned sample size, B improved the overall resolution rate beyond the minimum detectable effect, but resolution for Spanish-language users fell by five points. The team must decide what to do next. Which two actions are most appropriate? (Select two.)

- **A.** Promote variant B to all users, because the overall primary metric beat the minimum detectable effect.
- **B.** Run a follow-up test whose variants differ by a single change, so that the effect can be attributed.
- **C.** Drop the Spanish-language slice from the analysis, because it is only a small share of the traffic.
- **D.** Record an iterate decision with the slice regression, and add failing Spanish cases to the reference set.
- **E.** Pool these results with last quarter's experiment data to raise statistical power before deciding.

**Correct answers**: B, D

**Explanation**: Two changes moved together, so the result cannot be attributed to either; a follow-up that isolates one change (B) fixes that. A gain overall with a regression in one slice is the classic iterate outcome, documented with the trade-off, and the failing cases belong in the reference set for the next round (D). Promoting on the aggregate (A) ships a known regression, dropping the slice (C) hides it, and pooling with older data (E) mixes experiments run under different conditions.

---

## Q101 (Authored D4-06)

**Chapter tag**: Ch 12 (Observability at Scale) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: Six weeks after launch, a policy Q&A assistant shows no rise in error rates, and p95 latency is within its SLO. However, department heads report that answers have gradually become less accurate since the HR handbook was reorganized. Current monitoring covers only HTTP status codes, latency and token cost. Which monitoring change would most directly detect this kind of problem going forward?

- **A.** Lower the alert threshold on HTTP 5xx error rates so that smaller increases page the on-call engineer sooner.
- **B.** Log the complete prompt and response for every request indefinitely so engineers can investigate any complaint.
- **C.** Score sampled production outputs on a schedule with the offline eval checks and rubrics, sliced by index version.
- **D.** Add a thumbs-down button and alert the team whenever negative feedback exceeds a fixed count on a given day.

**Correct answer**: C

**Explanation**: Quality drift produces no error code, so it can only be seen by scoring real outputs. Sampling production traffic and grading it with the same code checks and judge rubrics as offline evaluation, sliced by index version, ties the decline to the handbook change (C). Tighter 5xx alerts (A) watch the wrong signal. Logging everything indefinitely (B) creates privacy and retention problems and still scores nothing. Thumbs-down counts (D) are sparse, biased and not tied to a baseline.

---

## Q102 (Authored D4-07)

**Chapter tag**: Ch 12 (Observability at Scale) · **Domain 4**: Evaluation, Testing & Optimization

**Question**: Overnight, cost per task for a document-analysis assistant rose 40 percent and time-to-first-token roughly doubled. The engineering team says no code was deployed, but the on-call engineer cannot tell what changed, because traces record only request IDs, total tokens and total latency. Which two additions to the per-request trace would most directly let the team diagnose this kind of change? (Select two.)

- **A.** The full raw prompt text, including customer content, retained without any fixed retention limit.
- **B.** A daily cost total imported from the provider invoice and attached to each of the request records.
- **C.** The model identifier, prompt version and retrieval index version that served each request.
- **D.** A static alert on every metric emitted by the service, using thresholds that were set before launch.
- **E.** Input tokens split into cached and uncached counts, recorded alongside time-to-first-token.

**Correct answers**: C, E

**Explanation**: A jump in cost and time-to-first-token with no code deploy often comes from a configuration change, such as a new prompt version that breaks the cache, or a model or index change. Version identifiers on each trace (C) let the team correlate the jump with what changed, and cached versus uncached input tokens (E) show directly whether the cache hit rate collapsed. Unbounded raw prompts (A) create privacy exposure, a daily invoice total (B) has no per-request detail, and static alerts on every metric (D) add noise without diagnosis.

---

## Q103 (Authored D5-01)

**Chapter tag**: Ch 15 (The Safety Stack and Guardrail Placement) · **Domain 5**: Governance, Safety & Risk Management

**Question**: An email-triage agent reads inbound customer emails and has tools to update CRM records, draft replies and forward messages to any external address. During red-teaming, an email containing hidden text that told the agent to forward the latest account export to an outside address caused the agent to attempt the forward. Which response best addresses this risk?

- **A.** Add a system-prompt rule telling the agent to ignore any instructions that appear inside customer emails.
- **B.** Log every forwarding action to the SIEM and have the security team review flagged events each week.
- **C.** Let the agent follow embedded instructions only when the sender's domain is on an approved list.
- **D.** Remove external forwarding from the tools and screen email content as untrusted data before the agent acts.

**Correct answer**: D

**Explanation**: This is indirect prompt injection: attacker text inside content the agent reads. The strongest response removes the capability the attack needs and treats email content as data that is screened before the agent acts (D). A prompt rule alone (A) is a single layer that can be talked around. Weekly SIEM review (B) detects the leak after it has happened. An approved-sender list (C) is a bypass, because trusted senders can be spoofed or compromised.

---

## Q104 (Authored D5-02)

**Chapter tag**: Ch 16 (Human Review by Stakes) · **Domain 5**: Governance, Safety & Risk Management

**Question**: An insurance claims assistant drafts settlement summaries that adjusters approve before payment. After four months, adjusters accept 97 percent of drafts unchanged, and the operations director proposes removing the second-level audit of approved claims to save cost. No one has compared the accepted drafts against verified claim outcomes. Which concern should you raise first?

- **A.** The acceptance rate is too high to be credible, so the assistant should be replaced with a more capable model.
- **B.** Acceptance shows what adjusters kept, not what was correct, and a usually-right system breeds over-reliance.
- **C.** The audit can be removed safely, because adjusters remain accountable for every claim that they approve.
- **D.** The assistant should run at a lower temperature first, so that its drafts become more consistent overall.

**Correct answer**: B

**Explanation**: A high acceptance rate measures what reviewers kept, not whether the drafts were right, and reviewers who usually see good drafts stop checking closely: classic over-reliance. Correctness must be measured on sampled claims against verified outcomes before any review layer is removed (B). Calling the rate not credible and swapping models (A) is unsupported by the scenario. Nominal accountability (C) does not help if reviewers are rubber-stamping. Lower temperature (D) changes variability, not correctness.

---

## Q105 (Authored D5-03)

**Chapter tag**: Ch 15 (The Safety Stack and Guardrail Placement) · also Ch 1 · **Domain 5**: Governance, Safety & Risk Management

**Question**: A finance team uses Claude to extract line items from supplier invoices and compute VAT totals for posting to the ledger. Auditors found that totals for the same invoice occasionally differ by a few cents between runs, even with identical input. The controller requires totals to be exact and reproducible. What is the most appropriate design change?

- **A.** Set the temperature to zero for all invoice calls so that each run returns the same totals every time.
- **B.** Run each invoice three times and post the total that appears most often across the separate runs.
- **C.** Have the model extract line items into a validated schema and compute the totals in deterministic code.
- **D.** Move the workload to the most capable model tier, since stronger reasoning will remove arithmetic errors.

**Correct answer**: C

**Explanation**: Model output is non-deterministic, and exact arithmetic is a job for code. Let the model do what it is good at, extracting fields into a validated schema, and compute the totals deterministically (C). Temperature zero (A) reduces variety but does not guarantee identical or correct arithmetic. Majority voting (B) triples cost and can still post a wrong value. A more capable model (D) may lower error rates but does not make results exact or reproducible.

---

## Q106 (Authored D5-04)

**Chapter tag**: Ch 15 (The Safety Stack and Guardrail Placement) · also Ch 16 · **Domain 5**: Governance, Safety & Risk Management

**Question**: A procurement agent turns approved purchase requests into JSON that is posted directly to the ERP to create purchase orders. Recent incidents include an order with a negative quantity and an order to a vendor that is not on the approved list. Policy also says that orders above a set amount need a manager's sign-off. Which two controls most directly enforce these rules? (Select two.)

- **A.** Add a system-prompt instruction asking the model to double-check quantities and vendors before it responds.
- **B.** Validate each JSON payload in code against a strict schema with types, ranges and allowed vendor values.
- **C.** Retry with a higher temperature whenever the ERP rejects an order, so the model produces a different output.
- **D.** Log every created purchase order and have the finance team audit a sample of them at the end of each month.
- **E.** Apply the amount limit as a code rule that routes orders above the threshold to a manager for approval.

**Correct answers**: B, E

**Explanation**: The model proposes and deterministic code decides. Strict schema validation (B) blocks negative quantities and unapproved vendors before the ERP call, and an amount rule in code (E) enforces the sign-off policy by routing large orders to a manager. A prompt instruction (A) is guidance, not enforcement. Retrying at a higher temperature (C) adds randomness, not control. A month-end audit (D) only detects bad orders after they exist.

---

## Q107 (Authored D5-05)

**Chapter tag**: Ch 17 (Proving It to Someone Who Was Not There) · **Domain 5**: Governance, Safety & Risk Management

**Question**: A US federal agency wants a Claude-based assistant to summarize case files for its staff. The team's prototype calls a commercial API endpoint chosen for price, stores embeddings in a SaaS vector database, and sends logs to a third-party monitoring tool. The agency's authorizing official says the workload requires FedRAMP Moderate. What should determine the production architecture?

- **A.** Every component in the data path, including model access, vector store and logging, must run in environments authorized at the required level.
- **B.** The model must be reached through an authorized environment, while the vector store and logging tools can stay on their current services.
- **C.** The team should select the most capable model tier, because the agency's decision rests mainly on the quality of the case summaries.
- **D.** A signed Business Associate Agreement with the model provider, together with a system-prompt rule forbidding retention of case data.

**Correct answer**: A

**Explanation**: FedRAMP is a hard constraint on every service in the data path: model access, vector store and logging must all run in environments authorized at the required impact level (A). Authorizing only the model endpoint (B) leaves case data flowing through unauthorized services. Model capability (C) is irrelevant if the environment is not authorized. A BAA (D) is a HIPAA instrument, and a prompt rule is not a retention control.

---

## Q108 (Authored D5-06)

**Chapter tag**: Ch 15 (The Safety Stack and Guardrail Placement) · also Ch 10 · **Domain 5**: Governance, Safety & Risk Management

**Question**: An internal IT helpdesk agent answers employee questions and resets an employee's own password on request. To move fast, it was given a shared administrator service account that can also delete accounts and change group memberships across the directory. A security review asks how to reduce the impact of a hallucinated or injected instruction. Which two changes should you make? (Select two.)

- **A.** Remove the account-deletion and group-membership tools that the helpdesk task does not require.
- **B.** Require the agent to ask the employee for confirmation in chat before deleting any account.
- **C.** Replace the shared admin account with credentials scoped to the requesting employee's own account.
- **D.** Send every administrative action the agent performs to the SIEM for review by the security team.
- **E.** Move the agent to the most capable model tier so that it misinterprets fewer employee requests.

**Correct answers**: A, C

**Explanation**: Excessive agency multiplies the damage of any hallucination or injection, so the fix is least privilege: remove tools the task does not need (A) and scope credentials to the requesting user (C), so the agent cannot touch other accounts. A chat confirmation (B) keeps the dangerous capability and can itself be manipulated. SIEM logging (D) detects after the damage is done. A more capable model (E) may reduce mistakes but leaves the blast radius unchanged.

---

## Q109 (Authored D5-07)

**Chapter tag**: Ch 16 (Human Review by Stakes) · also Ch 1 · **Domain 5**: Governance, Safety & Risk Management

**Question**: A legal operations team wants an agent to manage vendor contract renewals end to end, including sending termination notices when a contract should not renew. Once sent, a termination notice cannot be withdrawn. To save time, the team proposes that the agent send notices automatically whenever its confidence score exceeds 0.9. Which design should you recommend?

- **A.** Allow automatic sending above the confidence threshold and route only lower-confidence notices to a lawyer.
- **B.** Require a lawyer to approve every agent step, including contract retrieval, date checks and renewal reminders.
- **C.** Allow automatic sending for contracts below a set annual value and require lawyer approval for larger ones.
- **D.** Have the agent draft notices into a review queue without a send tool, and have a named lawyer approve each one.

**Correct answer**: D

**Explanation**: A termination notice is high impact and irreversible, so a human must approve each one; giving the agent only a drafting tool makes sending impossible without that approval (D). Confidence scores (A) miss confidently wrong outputs. Reviewing every step (B) causes review fatigue and adds nothing on low-impact steps. A contract-value cutoff (C) uses size as a proxy for risk, but even a small termination is binding and cannot be undone.

---

## Q110 (Authored D5-08)

**Chapter tag**: Ch 17 (Proving It to Someone Who Was Not There) · also Ch 9 · **Domain 5**: Governance, Safety & Risk Management

**Question**: A SaaS company is adding a Claude-powered document assistant to a product used by several EU enterprise customers. Customer contracts require that their data stay in the EU and that one customer's documents never appear in another customer's answers. The current prototype uses one shared vector index and a US-hosted deployment. Which two changes address these requirements? (Select two.)

- **A.** Keep the shared index, and instruct the model in the system prompt to use only the current customer's documents.
- **B.** Pseudonymize customer names in the documents, since pseudonymized data then falls outside the scope of the GDPR.
- **C.** Keep full prompts and retrieved documents in long-term logs so that any cross-customer leak can be investigated.
- **D.** Separate the indexes per customer, or apply tenant filters at retrieval before any document enters the context.
- **E.** Choose a deployment region and access path that keep prompts, indexes and logs within the EU, as contracted.

**Correct answers**: D, E

**Explanation**: Tenant isolation must happen at retrieval, before documents reach the context window, through separate indexes or enforced tenant filters (D). Residency is an architectural choice of region and deployment path for every component, including indexes and logs (E). A prompt instruction (A) is not an isolation control, because the other tenant's data has already been retrieved. Pseudonymized data is still personal data under the GDPR (B). Long-term logging of full content (C) increases exposure and conflicts with minimal retention.

---

## Q111 (Authored D6-01)

**Chapter tag**: Ch 20 (Documentation That Survives) · also Ch 3 · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: Three months after a document-review assistant was handed to the operations team, two incidents occurred. During a quality-drop alert, the on-call engineer could not tell whether the latest prompt change could be rolled back, or how. Separately, the release evaluation suite had silently stopped running after launch because no one knew it was their job. Which two additions to the handoff documentation most directly address these gaps? (Select two.)

- **A.** A lessons-learned retrospective describing the decisions the project team made during the design phase.
- **B.** A customer FAQ explaining what the assistant does and which document types it currently supports.
- **C.** A runbook and on-call playbook covering alert triage and prompt rollout and rollback through a version pin.
- **D.** The design meeting notes and review comments, so the operations team understands the original reasoning.
- **E.** A named owning team for the evaluation suite, with how to run it and the thresholds that gate each release.

**Correct answers**: C, E

**Explanation**: The first incident is a missing operational procedure: a runbook and on-call playbook that explain alerts, triage and how to roll a prompt change forward or back via the version pin (C). The second is missing ownership: evals stop running when no team owns them, so name the owner and document how to run the suite and its release thresholds (E). A retrospective (A) and design meeting notes (D) explain the past, not how to operate the system. A customer FAQ (B) is written for end users, not operators.

---

## Q112 (Authored D6-02)

**Chapter tag**: Ch 20 (Documentation That Survives) · also Ch 17 · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: Pre-handoff evaluation of a benefits-claims assistant showed accuracy well below the release threshold on handwritten scanned forms and on claims written in Portuguese, both a small share of traffic. The product manager asks you to leave these results out of the handoff documents so that the support team and auditors do not lose confidence in the launch. How should you handle these results?

- **A.** Leave them out of the handoff set and plan to address both weak slices quietly in the next release cycle.
- **B.** Record them only in the project retrospective, where the team can revisit them during the next phase.
- **C.** Document them as known limitations, with the affected inputs, residual risk and how they are routed to humans.
- **D.** Mention them in the customer FAQ with positive wording that encourages users to submit typed English forms.

**Correct answer**: C

**Explanation**: Known limitations tell support teams where the system should not be trusted, give auditors evidence that risk was understood rather than hidden, and keep the next team from rediscovering the failures. Stating the affected inputs, residual risk and human-routing path makes the limitation operable (C). Omitting the results (A) hides a known risk from operators and auditors. A retrospective (B) is not where operators look. A customer FAQ (D) targets end users, spins the risk and gives operators nothing to act on.

---

## Q113 (Authored D6-03)

**Chapter tag**: Ch 3 (Sizing, Scoping, and the Feasibility Verdict) · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: A contract-summarization service has run on one model version for eight months, and the team has kept its versioned reference set and release thresholds. A newer model version has just been released, and the business sponsor asks you to switch production to it this week because the announcement says it reasons better. What should you do?

- **A.** Rerun the existing reference set and thresholds on the new version per slice, check SLAs and cost, then roll out behind a version pin.
- **B.** Switch production to the new version this week, since a newer release should perform at least as well as the current one.
- **C.** Stay on the current version until the provider retires it, because it already meets every one of the release thresholds.
- **D.** Build a new evaluation set around the new version's announced strengths, then decide whether to switch based on it.

**Correct answer**: A

**Explanation**: A model upgrade is a change like any other: rerun the existing reference set and thresholds per slice, confirm latency and cost against SLAs and budget, and roll out gradually behind a version pin with a documented rollback (A). Switching on the strength of an announcement (B) skips evidence, and behaviour can shift in ways that matter. Ignoring the release (C) forgoes possible gains in quality or cost. A new eval set built around the announced strengths (D) moves the yardstick, so results are no longer comparable with the current version.

---

## Q114 (Authored D6-04)

**Chapter tag**: Ch 20 (Documentation That Survives) · also Ch 3 · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: ADR-007, accepted at launch a year ago, put all traffic of a claims-triage assistant on the most capable model tier. Rerunning the carried-forward reference set now shows a lighter tier meeting the quality bar in aggregate at much lower cost. A team lead argues that accepted decisions should stay fixed for consistency. Which two actions should you take? (Select two.)

- **A.** Write a new ADR that records the new evidence and supersedes ADR-007, leaving the original record visible.
- **B.** Edit ADR-007 in place to describe the lighter tier, so that only one current decision record exists.
- **C.** Check the lighter tier per slice against the release thresholds before routing production traffic to it.
- **D.** Keep ADR-007 unchanged, since revisiting accepted decisions undermines stakeholder trust in the design.
- **E.** Move all traffic to the lighter tier now, since the aggregate result on the reference set already passes.

**Correct answers**: A, C

**Explanation**: Decisions should be stable but revisable when evidence changes; a new ADR that records the evidence and supersedes ADR-007 keeps the history visible (A). An aggregate pass can hide failing slices, so validate the lighter tier per slice against the release thresholds before routing traffic (C). Editing an accepted ADR (B) erases the record of why the first choice was made. Locking the decision (D) ignores evidence and wastes cost. Switching on the aggregate alone (E) risks shipping a regression on important slices.

---

## Q115 (Authored D6-05)

**Chapter tag**: Ch 3 (Sizing, Scoping, and the Feasibility Verdict) · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: Production monitoring of an invoice-processing assistant shows that extraction quality drops on invoices from a recently acquired subsidiary, which uses a different layout. The finding is written up in the monitoring-phase retrospective, and planning for the next iteration starts next week. Which action best ensures this lesson actually changes the next iteration?

- **A.** Archive the retrospective in the long-term project repository so the finding is preserved for future reference.
- **B.** Send the retrospective to every party on the stakeholder register as part of the phase-transition notification.
- **C.** Schedule a review of the finding at the end of the next iteration, once more production data has been collected.
- **D.** Turn it into inputs: add subsidiary invoices to the reference set, a discovery question and a design option to test.

**Correct answer**: D

**Explanation**: A lesson only helps when it becomes an input to the next phase: new cases in the reference set make the regression measurable, a discovery question confirms layouts and volumes with the subsidiary, and a design option gives the iteration something concrete to evaluate (D). Archiving (A) preserves the record but nobody uses it. Notifying the register (B) is communication hygiene, not knowledge transfer. Reviewing at the end of the next iteration (C) means that iteration runs without the lesson.

---

## Q116 (Authored D6-06)

**Chapter tag**: Ch 19 (Feedback Loops and SLAs) · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: Six weeks after launch of a proposal-drafting assistant, sales leads in one region say it "feels too slow to use during client calls." The SLA agreed in discovery commits to a p95 draft latency, and the organization-wide dashboard shows p95 comfortably within it. The regional director asks you to act on the complaint. What should you do first?

- **A.** Move all drafting traffic to a lighter model tier right away so that every region experiences faster drafts.
- **B.** Map the complaint to the latency SLA and measure p95 for that region before choosing a fix or renegotiation.
- **C.** Close the complaint, because the organization-wide p95 latency is within the SLA committed in discovery.
- **D.** Add a progress indicator to the drafting screen so users perceive the wait as shorter during client calls.

**Correct answer**: B

**Explanation**: Vague feedback should first be mapped to the value pillar or SLA it concerns. Measuring p95 for the region's slice shows whether this is a breach to fix, a need the SLA never captured (live client calls) to renegotiate, or an opinion to note (B). Changing the model for everyone (A) acts before measuring and may cost quality. Closing on the aggregate (C) ignores that aggregates hide slice failures. A progress indicator (D) treats perception without establishing whether the commitment is met.

---

## Q117 (Authored D6-07)

**Chapter tag**: Ch 19 (Feedback Loops and SLAs) · **Domain 6**: Stakeholder Communication & Lifecycle Management

**Question**: You are finalizing service commitments for a Claude-based underwriting assistant with the business sponsor and the platform operations team. The sponsor wants a clear quality and latency commitment to report against, and operations wants warning of trouble before that commitment is broken. Which two arrangements should you put in place? (Select two.)

- **A.** Set the internal targets equal to the stakeholder commitment so that there is a single number everyone tracks.
- **B.** Report to stakeholders against the SLA agreed in discovery, expressed as measurable latency and quality thresholds.
- **C.** Report the stricter internal targets to stakeholders as the commitment so that the sponsor sees ambitious numbers.
- **D.** Configure alerts to fire only once the SLA has been breached so that the operations team avoids alert fatigue.
- **E.** Operate against stricter internal SLOs with an error budget so that alerts fire before the SLA is put at risk.

**Correct answers**: B, E

**Explanation**: Stakeholders need a commitment they can hold the system to, so report against the agreed SLA with measurable thresholds (B). Operations needs headroom, so operate against stricter internal SLOs with an error budget that surface problems before the commitment breaks (E). Equal targets (A) and alerting only on breach (D) both make the breach itself the first signal. Presenting internal targets as the commitment (C) creates expectations the team never agreed to and removes the safety margin.

---

## Q118 (Authored D7-01)

**Chapter tag**: Ch 21 (Team Enablement and Debugging) · also Ch 15 · **Domain 7**: Developer Productivity & Operational Enablement

**Question**: An SRE team wants to give a Claude-based on-call assistant cluster-admin credentials on production Kubernetes so it can diagnose and fix incidents faster. The assistant reads logs and support tickets, some of which contain customer-supplied text. Which access design should you recommend?

- **A.** Grant cluster-admin credentials but log every command the assistant runs, so any harmful action can be traced and reversed afterwards.
- **B.** Grant cluster-admin only during declared incidents and add a CLAUDE.md instruction telling the assistant to avoid destructive commands.
- **C.** Provide read-only log, trace and metrics tools by default, plus narrowly scoped remediation tools that run only after on-call approval.
- **D.** Deny the assistant all production access, so engineers copy relevant log excerpts into the session by hand during each incident.

**Correct answer**: C

**Explanation**: Investigation needs read-only access to logs, traces and metrics; remediation such as a restart or rollback should be a narrow, scoped tool executed only after an on-call engineer approves, under a least-privilege identity with an audit trail (C). Logging alone (A) detects harm only after it happens. Time-boxed admin rights plus a CLAUDE.md instruction (B) rely on guidance rather than enforcement, and customer text in logs could inject instructions. Removing all access (D) throws away the speed the team needs and makes manual copying a new source of error.

---

## Q119 (Authored D7-02)

**Chapter tag**: Ch 21 (Team Enablement and Debugging) · **Domain 7**: Developer Productivity & Operational Enablement

**Question**: Twenty minutes after a deploy, checkout-api starts returning intermittent 502 errors. An engineer opens Claude Code and asks it to 'find the bug and push a fix' to the main branch. Error logs, distributed traces with correlation IDs and the deploy history are available through read-only tools. Which two steps should happen before any fix is merged? (Select two.)

- **A.** Have Claude apply its most plausible fix directly to production, then confirm the diagnosis afterwards from the error rate.
- **B.** Follow failing requests across services by correlation ID and line up the first errors with the deploy and config history.
- **C.** Switch the session to the most capable model tier, since a stronger model is more likely to guess the root cause first time.
- **D.** Restart every checkout-api pod immediately and close the incident if the error rate drops below the alert threshold.
- **E.** Reproduce the failure outside production, ideally as a failing test that the proposed fix must then make pass.

**Correct answers**: B, E

**Explanation**: Diagnosis comes before change. Correlating failing requests by ID and aligning them with the deploy timeline (B) ties each hypothesis to evidence, and reproducing the failure as a failing test (E) turns a guess into a fact and becomes the regression test for the fix, which then goes through normal review. Pushing a plausible fix to production (A) skips both verification and review. A stronger model (C) does not replace evidence. Restarting pods (D) may hide the symptom while leaving the root cause in place.

---

## Q120 (Authored D7-03)

**Chapter tag**: Ch 21 (Team Enablement and Debugging) · **Domain 7**: Developer Productivity & Operational Enablement

**Question**: A platform team's CLAUDE.md tells Claude Code to run the formatter and linter after every file edit and never to modify files under db/migrations. Reviewers still find unformatted code in AI-generated pull requests, and last week a session edited an already-applied migration. The team wants both behaviors enforced every time across all repositories. What should you recommend?

- **A.** Add hooks that format after edits and block protected paths, distributed centrally through the managed plugin marketplace.
- **B.** Rewrite both instructions in capital letters near the top of CLAUDE.md and repeat them in each developer's personal CLAUDE.local.md file.
- **C.** Ask reviewers to reject any AI-generated pull request with formatting problems or migration changes until developers adjust their prompts.
- **D.** Move the instructions into each repository's README so that Claude reads them together with the build and test documentation.

**Correct answer**: A

**Explanation**: CLAUDE.md is guidance that Claude usually follows, but not with certainty. Behavior that must always happen belongs in hooks, which run at fixed lifecycle points: a post-edit hook runs the formatter and a pre-edit hook blocks protected paths. Distributing the approved hooks centrally keeps every repository consistent (A). Louder or duplicated instructions (B) and README text (D) are still guidance. Catching problems in review (C) finds them after the fact and does nothing to stop an applied migration from being edited.

---

