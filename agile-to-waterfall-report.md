# The Agentic Waterfall: How the AI Industry Is Regressing Software Development

**By Muhammadali Nazarov**

---

## Table of Contents

1. The Core Argument
2. Summary
3. The Current State
4. The Industry Push
5. The Degradation Path
6. The Tooling Regression
7. The Exhaustive Matrix
8. Two Cases of Review
9. The Convergence Trap
10. The "Product Builder" Is a Developer
11. The "AI-Native SDLC" Fallacy
12. The Parallel Agent Fallacy
13. The Asymmetric Review Argument
14. The Context Gap: Why AI Cannot Accumulate Codebase Knowledge
15. Why Human Developers Cannot Be Replaced by AI Agents
16. The Junior Pipeline Problem
17. The Vicious Cycle
18. Common Counterarguments
19. Q&A — Anticipated Objections
20. Key Findings
21. Conclusion

---

## The Core Argument

This entire report reduces to one structural proof:

> **Code created with General Intelligence (GI) in the loop = reviewed code**
>
> **Code created without GI in the loop = vibe code**

A human developer pair-programming with AI has GI in the loop during creation. The code is reviewed as it is written. The PR can merge without further review. This is not vibe code.

An AI agent coding autonomously does not have GI in the loop. The code is unreviewed at creation. There are only two options:

> **Option A:** Accept without human review → vibe code
>
> **Option B:** Add human review after creation → Waterfall → slower than having GI in the loop during creation (Agile)

There is no Option C. Every workflow in the industry is one of these two options or a combination of them. There is no configuration where autonomous AI agents produce non-vibe-code without making the process slower than synchronous human + AI development.

This is not an emotional argument about replacing humans with robots. It is a structural fact: replacing GI with no-GI in the coding loop either produces unreviewed code or forces a slower methodology. The rest of this report proves this in detail.

---

## Summary

The software industry is undergoing a methodology regression. In the rush to adopt AI agents, teams are unknowingly abandoning Agile principles and reverting to Waterfall — the sequential, document-heavy, plan-then-execute methodology the industry spent twenty years learning to abandon.

A critical distinction must be made between two types of AI agents:

**Synchronous agents** operate alongside the developer in a pair-programming model. The developer sees what the agent does in real time, can stop it mid-task, redirect it, discuss with it, and review the code as it's being written. Coding and reviewing are fused into a single activity — just as in traditional pair-programming, but with AI as the partner. This preserves Agile principles.

**Asynchronous agents** operate independently. They receive a task or spec, execute autonomously — whether locally or in the cloud — and submit a finished artifact (usually a pull request) for review after the fact. The developer cannot see what the agent is doing, cannot interject, and must review the output as a separate phase. This is Waterfall by structure.

This report is not an argument against AI in development. Synchronous agents are a clear improvement — they make developers faster while preserving review quality and Agile methodology. The argument is against the industry's push toward asynchronous agents as the default workflow, which forces a regression from Agile to Waterfall regardless of how the tooling is configured.

---

## The Current State

Most development teams today operate in some form of Agile with synchronous AI assistance. A developer works alongside an AI tool — Cursor, Copilot, Claude Code. The feedback loop is seconds to minutes. The developer can interrupt, redirect, discuss, and course-correct in real time. Coding and reviewing are fused into a single continuous activity.

This is Agile + synchronous Agentic AI. It works. It is fast. It preserves everything Agile was designed to preserve: small increments, fast feedback, and discovery of requirements through building.

## The Industry Push

Leadership across the industry — from startups to Microsoft to dedicated "AI-native SDLC" platforms — is pushing a different model: autonomous AI agents that receive tasks, produce code, and submit pull requests for human review. The promise is parallelism. Multiple agents working simultaneously, producing features while humans sleep.

The pitch is compelling. The structural reality is not.

## The Degradation Path

To understand why the regression happens, compare the three processes side by side:

**Process 1 — Agile + Sync Agentic AI:**
task → developer pair-programs with AI with fast review cycles (see issue → stop → correct → continue) → PR → merge

One phase. Coding and reviewing are fused into a single activity. The developer sees every line as it's written, stops the AI when something is wrong, redirects immediately. Feedback cycles are seconds. The PR is already reviewed when it is submitted.

**Process 2 — Waterfall + Async Agents (developer writes specs):**
task → developer writes detailed spec → AI Agent codes autonomously → PR → slow review cycles (comment → wait → fix → re-review) × N → merge

The review phase is the same cognitive work as pair-programming in Process 1 — understanding the code, catching issues, providing corrections. But it is performed as a separate phase after coding. The developer cannot course-correct mid-cycle. Each feedback cycle is minutes to hours instead of seconds. On top of that, a spec-writing phase has been added that does not exist in Process 1.

**Process 3 — Waterfall + Async Agents (Product Builder writes specs):**
task → Product Builder writes spec → AI Agent codes → PR → developer loads context → slow review cycles (comment → wait → fix → re-review) × N → merge

The same as Process 2, with an additional phase: the developer must load context they did not create before they can even begin the review.

**The structural proof:**

The review phase in Waterfall is a degraded version of the entire Agile process. The developer is doing the same cognitive work — understanding the task, reading the code, catching issues, providing corrections — but as a separate phase rather than a fused activity, with slower feedback cycles and no ability to course-correct mid-cycle.

> **Process 1** = Task + Fused review with fast feedback cycles and mid-cycle course-correction
>
> **Process 2** = Task + Spec Writing + Separate review with slow feedback cycles and no mid-cycle course-correction
>
> **Process 3** = Task + Spec Writing + Context Loading + Separate review with slow feedback cycles and no mid-cycle course-correction

The same cognitive work — reviewing the code — happens in all processes. The difference is when and how:

| | Process 1 (Sync) | Process 2 & 3 (Async) |
|---|---|---|
| Review timing | During coding | After coding |
| Feedback cycles | Fast — seconds | Slow — minutes to hours |
| Course-correction | Mid-cycle — stop, redirect, continue | Between cycles — comment, wait, re-review |
| Fused or separate | Fused with coding | Separate phase |

This inequality holds because of four properties. Each must be false for the inequality to fail:

> **Axiom 1 — Formalization cost:** Process 2 requires upfront, predictive specification. Process 1 requires only incremental, reactive direction. In sync, you say "add pagination" and course-correct when the AI chooses wrong. In async, you must anticipate that choice and specify it in advance. Every ambiguity you fail to predict becomes a review cycle later. Predictive specification always costs more than reactive direction, because prediction requires modeling failure modes that reaction handles for free.
>
> **Axiom 2 — Context reload:** Splitting work into separate phases forces the developer to re-engage with the task after a gap. In Process 1, context is continuous — the developer never leaves the task. In Process 2, the developer writes the spec, the agent codes, the developer returns to review. Even minutes apart, re-engaging has non-zero cost. This is not debatable — task-switching cost is established cognitive science.
>
> **Axiom 3 — Feedback latency:** Async feedback is slower than sync feedback by definition. In Process 1, the developer sees an issue and says "stop" — seconds. In Process 2, the developer comments on a PR, the agent processes, the developer re-reviews — minutes to hours. This is the definition of async, not a limitation of current tooling.
>
> **Axiom 4 — Tooling delta:** The review environment in Process 2 (PR diff interface) provides fewer capabilities than the development environment in Process 1 (local IDE with full codebase navigation, debugger, terminal, real-time visibility). Currently strictly positive. Theoretically improvable to zero — but not negative, because no one argues a diff viewer exceeds a full IDE. And if tooling improves to provide full IDE access with real-time visibility and the ability to interject, it has become sync — it has become Process 1.

The complete inequality:

> **Process 2 = Process 1 + Formalization Δ + Context Reload + Feedback Latency + Tooling Δ**

| Term | Strictly > 0? | Can be negative? | Can reach zero? |
|---|---|---|---|
| Formalization Δ | Yes — prediction > reaction | No | No — upfront spec always exceeds incremental direction |
| Context Reload | Yes — any phase break has cost | No | Only if phases are not split — which is Process 1 |
| Feedback Latency | Yes — by definition of async | No | Only by becoming sync — which is Process 1 |
| Tooling Δ | Currently yes | No | Theoretically — but achieving it recreates Process 1 |

> **Process 2 > Process 1, always. Process 3 > Process 2 > Process 1, always.**
>
> To falsify this inequality, you must show that at least one axiom is wrong — that predictive specification is free, that context-switching has no cost, that async is faster than sync, or that a diff viewer exceeds a full IDE. None of these can be reasonably argued. Three of the four terms cannot even theoretically reach zero without converting Process 2 into Process 1 — which concedes the argument.

**Improving the AI does not change the inequality.** Feeding rules, CLAUDE.md files, or codebase context to the AI agent improves its output in both workflows equally. In sync, the AI writes better code and the developer interjects in real time when rules are insufficient or don't cover the situation — fewer corrections, faster. In async, the AI writes better code but nobody interjects during coding — better initial output, but still no course-correction, still review cycles when rules weren't sufficient, still Waterfall. Rules are an improvement to the tool, not to the methodology. Better rules make both Process 1 and Process 2 faster. The delta between them stays the same. Process 2 is still slower.

**Why human review gets dropped:** The entire purpose of moving to agents was speed. But Waterfall is structurally slower than Agile because it contains the same work plus additional overhead. The only way to deliver on the speed promise is to remove the phase that makes it slow — human review. This is not a choice anyone makes consciously. It is the only move available when the math doesn't work. Once human review is removed, AI codes and nobody with engineering competence reviews. This is vibe coding at enterprise scale.

## The Tooling Regression

The methodology regression from Agile to Waterfall is compounded by a concrete tooling regression. Moving from local development to cloud-based agents means swapping a fully-featured IDE for GitHub's pull request interface. This is not a tool preference — it is a loss of capability at every level.

**What you have locally:**

- See code changes in real time, as the AI writes each line
- Full IDE navigation: jump to definition, find references, search all files
- Reference any file in the codebase when giving the AI feedback
- Run the code, set breakpoints, test in real time
- Full debugger, console, and logs
- Stop the AI mid-task and redirect immediately
- Give instant feedback by pointing to specific lines and files
- Full terminal access to run scripts and check logs
- Full codebase search with regex

**What you get with GitHub PR UI:**

- See changes only after the agent finishes, as a static diff
- Only changed files are visible in the PR diff
- Cannot reference files that are not part of the PR diff
- Cannot run code from the GitHub interface
- No debugger
- Cannot interrupt the agent — must wait until it finishes
- Feedback is limited to comments on changed lines, with async response times
- No terminal access
- Limited search

Every item on this list is a concrete capability that developers use continuously during local development. The cloud workflow removes all of them and replaces them with a diff viewer. No amount of better AI rules, CLAUDE.md files, or prompt engineering compensates for losing the ability to run the code, navigate the codebase, or stop the AI mid-task.

## The Exhaustive Matrix

Every possible workflow is a combination of who codes and who reviews:

| Row | Coder | Reviewer | Methodology | Result |
|---|---|---|---|---|
| 1 | Human | Human | Agile | Traditional development. Competent reviews. |
| 2 | Human + AI | Human | Agile + sync Agentic AI | Faster coding. Competent reviews. |
| 3 | Human + AI | Human + AI | Agile + sync Agentic AI | Faster coding. Faster reviewing. Optimal current state. |
| **⚠ METHODOLOGY BREAK — AGILE → WATERFALL** | | | | |
| 4 | AI Agent | Human | Waterfall + async Agents | Fastest initial coding but no supervision during creation. Competent reviews but more feedback cycles. Net slower for non-trivial tasks. |
| 5 | AI Agent | Human + AI | Waterfall + async Agents | Fast unreliable code. Fast review. Unreliable quality. |
| 6 | AI Agent | AI Agent | Waterfall + async Agents (Vibe code) | Pure vibe code. The only path to full autonomy. Only viable when AI review competence matches human review competence. |

The break happens between Row 3 and Row 4. The moment you replace the human coder with an autonomous agent, the workflow shifts from Agile to Waterfall — not by choice, but by structural necessity. The developer is no longer in the coding loop, so review becomes a separate phase after the fact rather than a continuous activity during development.

The industry is selling Row 6 as the destination, but teams are landing on Rows 4 and 5 and calling it innovation.

Row 3 is the optimal current state. It is what most effective teams already have. The key structural advantage of Row 3 is that in synchronous development, the coder and reviewer roles collapse into a single activity — the developer is reviewing as they code. This eliminates the handoff that creates Waterfall.

## Two Cases of Review

The argument so far applies to the developer who could have written the code themselves. But there is a second case that must be addressed separately.

**Case 1: The developer reviews code they could have written.**

The inequality applies in full:

> Process 2 = Process 1 + Formalization Δ + Context Reload + Feedback Latency + Tooling Δ

This is structural and permanent. If the developer is going to do the cognitive work of understanding the task and the code, doing it as pair-programming (Process 1) is always faster than doing it as spec writing + reviewing someone else's output (Process 2). All four terms are strictly positive. No improvement in AI changes this. The inequality holds by construction.

**Case 2: The developer reviews someone else's PR.**

When a developer reviews another person's PR — whether written by a human or an AI agent — the review process is the same. Same GitHub UI, same comments, same feedback. The only measurable difference is the number of review cycles:

- A human developer's PR has already been through a first review. The author pair-programmed with AI, ran the code, tested it, caught issues. The reviewer's pass is a lightweight second review. Fewer cycles.
- An AI agent's PR has had no first review. More issues survive to the review stage. More cycles are needed.

This difference — the number of review cycles — is a current limitation of AI quality, not a structural one. As AI improves, agent-authored PRs will approach the quality of human-authored PRs, and the cycle count will converge. When it does, reviewing an agent's PR and reviewing a human's PR becomes equivalent.

## The Convergence Trap

The previous section appears to suggest that as AI improves, agents become viable. This is the argument the industry is making. It is wrong. Here is why.

For an AI agent to produce a PR of human quality, it needs a spec of sufficient quality. A spec of sufficient quality requires the author to understand the codebase, the architecture, the edge cases, and how the change fits into the larger system. This is developer-level knowledge. A person with this knowledge is a developer, regardless of their title.

This means:

**A Product Builder without developer knowledge** writes shallow specs. The agent produces low-quality code. Many review cycles. Or vibe code if nobody reviews.

**A Product Builder with developer knowledge** writes good specs. The agent produces decent code. But this person has the same knowledge as a developer. They could have done Process 1 — pair-programmed with AI directly — and it would have been faster, because:

> Process 2 = Process 1 + Formalization Δ + Context Reload + Feedback Latency + Tooling Δ

The knowledge required to write a good spec and the knowledge required to write good code are the same knowledge. The output format is different. The cognitive work is identical. Making a task well-defined enough for an agent IS the development work.

Therefore, swap the Product Builder who has developer knowledge with an actual developer. What you get is a developer writing specs for an agent instead of pair-programming with AI. That is Process 2. Process 2 is always slower than Process 1.

Now consider the best possible case: AI becomes smart enough that its PRs are identical in quality to a human developer's PRs. The review cycle difference disappears. An agent's PR and a human's PR are indistinguishable. This sounds like it validates the agent workflow. It does not.

In this scenario, the developer writing the spec has developer knowledge. The agent produces a perfect PR. The reviewer sees a PR identical to what a human would have written. But the developer who wrote the spec could have pair-programmed with AI (Process 1) and produced the same PR faster — because Process 1 does not include the formalization cost, the context reload, the feedback latency, or the tooling degradation.

**Even with perfect AI, Process 2 is slower than Process 1 for anyone with the knowledge to write good specs. And without that knowledge, the specs are bad and the output is vibe code.**

There is no middle ground. The "AI will improve" argument does not save the Waterfall model. It proves that the person capable of writing good specs should be pair-programming instead.

## The "Product Builder" Is a Developer

The industry is promoting a new role: the "Product Builder" — described as part Product Manager, part Software Engineer, part Designer, part Business Analyst. The premise is that equipped with AI tools, this person can skip traditional development and ship features by writing specs and prompts.

This is not a new role. It is the developer under a new name.

In Agile + AI, the developer pair-programs with AI and outputs code. In Waterfall + AI, the developer writes specs for agents and outputs English. The cognitive work is identical — understanding the task, the codebase, the architecture, the edge cases, how the change fits the larger system. The only thing that changed is the output format.

The industry is renaming "developer" to "Product Builder" because the methodology shifted from Agile to Waterfall, and in Waterfall the developer's output is specs, not code. This is not innovation. It is a methodology regression that changed what the developer produces, repackaged as a new role.

And the medium change is strictly worse. Code is precise. Specs are lossy. When a developer pair-programs with AI, the AI executes exactly what they are building together. When a developer writes specs, the agent interprets their English and produces what it thinks they meant. Every ambiguity in the spec becomes a bug. Every unstated assumption becomes a review cycle.

If a Product Builder lacks developer knowledge, their specs are shallow and the output is vibe code. If a Product Builder has developer knowledge, they are a developer — and they would be faster pair-programming with AI (Process 1) than writing specs for agents (Process 2). There is no configuration where the Product Builder role adds value over a developer using Agile + sync AI.

There is a third case: domain experts — doctors, lawyers, financial analysts — using AI to build internal tools for their own domain. These people have deep domain knowledge but no engineering knowledge. Their output is vibe code. That may be an acceptable tradeoff for low-risk internal tools. But this should be labeled honestly as vibe code for domain-specific tooling, not marketed as a new software development methodology. The "Product Builder" role conflates two fundamentally different activities — professional software engineering and domain-expert prototyping — under one title, obscuring that the latter produces unreviewed code by people who cannot evaluate its correctness beyond surface behavior.

## The "AI-Native SDLC" Fallacy

Platforms like 8090 Software Factory market themselves as "AI-native SDLC orchestration." Their pipeline consists of:

- **Refinery:** Create a detailed PRD (Requirements)
- **Foundry:** Expand PRD into a structured Blueprint (Design)
- **Planner:** Generate Work Orders with implementation plans (Implementation Planning)
- **Execution:** AI executes the work orders (Implementation)
- **Validator:** Collect user feedback, create tasks (Verification)

This is the Waterfall methodology with industrial naming. Requirements → Design → Plan → Build → Validate. The sequential, document-heavy, plan-then-execute structure is identical to what the industry rejected twenty years ago.

Their own documentation acknowledges that "development itself has never been the bottleneck" and that teams struggle with deciding "what to build, why, and how it fits into the larger system." Their solution is to make the planning phase heavier — more PRDs, more Blueprints, more Feature Nodes, more Work Orders — before any code is written. This is the foundational Waterfall assumption: if we plan better upfront, execution will go smoothly. Agile exists because that assumption is false. Requirements are discovered during implementation, not before it.

## The Parallel Agent Fallacy

The core promise of the agentic workflow is parallelism: give a developer five agents, get five times the output. This fails for a structural reason.

A developer cannot review five agents' output in parallel. They review them sequentially. But to review each agent's PR, they must first load the context of the task — understand the problem, the requirements, the edge cases. This context-loading cost means that reviewing a PR you didn't write is slower than writing the code yourself with AI assistance.

One developer, one agent, synchronous. This is the maximum efficient configuration. Anything beyond this creates overhead that exceeds the time saved.

This inequality is per-task and holds regardless of team size. Whether the team has one developer or fifty, each developer assigned to a task would be faster with sync AI than delegating it to an async agent. Scaling the team does not change the per-task math — it just means more people each facing the same inequality.

**The clarifying questions escape hatch does not work.**

A common counterargument is that agents can ask clarifying questions during coding, recovering some of the sync feedback loop. This fails in two ways.

First, if the agent is asking questions during coding, you need context of the task to answer. You are now doing synchronous work — but in an asynchronous environment with worse tooling. You have the worst of both worlds. If synchronous interaction is required, it should happen locally where you have full IDE access, real-time visibility, and instant feedback — not through PR comments and async message exchanges.

Second, if five agents ask questions simultaneously, you cannot context-switch between five different tasks. You need to load the context of each task to answer each question. That is five context switches. You answer one agent's question, by the time you reach the fifth, you have lost the nuance of the first. While you are answering agent three's question, agents one, two, four, and five are either blocked waiting for your response or continuing without your input — which means more issues to find during review.

The "parallel agents with clarifying questions" model is:

- Not truly async — you are being pulled into synchronous interactions
- Not truly sync — you do not have real-time visibility or control
- Fragmented across multiple context switches
- Agents blocked or proceeding blind while you are occupied with another

Compare to synchronous local development: one agent, one task, full context, instant answers, no switching. Finish. Next task. One agent, one task. Sequential but fast.

The parallel agent model does not parallelize the developer. It fragments them. The bottleneck has always been human attention, and human attention cannot be parallelized.

## The Asymmetric Review Argument

A common argument from leadership is: "I review your PRs asynchronously. Why can't you review the agent's PRs the same way?"

This comparison fails for two reasons.

First, leadership's async review works because developers did synchronous work first. The PR has already been through a first review — the developer pair-programmed with AI, tested locally, caught issues during coding. The leadership review is a lightweight second pass on a pre-reviewed artifact, checking strategic alignment and high-level architectural concerns. Replace the developer's sync work with an async agent, and the leadership review becomes the first and only review — a fundamentally different job requiring deep engagement with unfamiliar code.

Second, the speed accountability is asymmetric. Leadership measures developer speed — time from task assignment to PR submission. Leadership does not measure its own review speed. When the methodology changes from Agile to Waterfall, the developer's workflow changes entirely — they are now writing detailed specs, waiting for agents, reviewing unreviewed code with degraded tooling, going through multiple review cycles. They get slower.

But from leadership's position, nothing changed. They still review async. Their review is still a lightweight second pass. Their speed is unaffected. They see the symptom — developers are slower — without experiencing the cause — the methodology change that made them slower. The speed was never lost at the leadership review layer. It was lost at the developer layer, which is exactly where the Agile-to-Waterfall regression happens. And if leadership demands the developer speed up within the Waterfall model, there is only one lever left: reduce or remove human review. That is enterprise-scale vibe code.

## The Junior Pipeline Problem

The trend is not merely that juniors stop coding. The trend is that juniors stop being hired. The logic is straightforward: if AI agents do the coding and seniors supervise, why hire juniors or mid-level developers at all? They are the most expensive line item that agents are supposed to replace. The industry is converging on a model where a small number of seniors write specs, supervise async agents, and review the output.

This eliminates the pipeline entirely. Juniors do not become seniors by writing specs. They become seniors by writing code, making mistakes, debugging, and understanding how systems work from the inside.

What juniors learn from coding cannot be learned from writing specs:

- **Debugging:** Understanding why code fails requires running it, stepping through it, reading stack traces, forming hypotheses. Specs do not fail. Code does. The skill of diagnosing a system under failure is built exclusively through hands-on coding.
- **System understanding:** A junior who writes a database query, watches it execute slowly, profiles it, and rewrites it understands indexing. A junior who writes "the query should be fast" in a spec understands nothing.
- **Implicit knowledge:** The thousands of rules that seniors carry — "don't mutate state here," "this API is eventually consistent," "this pattern causes deadlocks under load" — are learned by encountering the consequences firsthand. No spec document teaches this. No onboarding session covers it. It is absorbed through years of writing, breaking, and fixing code.

The damage is delayed. The senior engineers who exist today were juniors five to ten years ago. They wrote code, made mistakes, debugged production incidents, and built the deep understanding that makes them capable of reviewing, architecting, and leading. If the industry stops hiring juniors today, the pipeline does not break today. It breaks in five years, when the current seniors leave, burn out, or retire and there is no one to replace them. The model of "seniors supervising agents" works only as long as the seniors exist. It is consuming a non-renewable resource — experienced engineers — and producing no replacement supply.

This is irreversible on short timescales. You can purchase an AI subscription tomorrow. You cannot purchase a senior engineer who understands your system, your architecture, your domain, and your history of decisions. That person takes years to develop, and the development requires writing code — not specs.

A generation of engineers who can write specs but have never deeply understood the code they are shipping is a generation that cannot review, debug, or maintain the systems they have built. The industry is not just regressing its methodology — it is destroying the pipeline that produces the senior engineers needed to make any workflow function.

## The Context Gap: Why AI Cannot Accumulate Codebase Knowledge

Human memory and AI context are fundamentally different architectures, not different sizes of the same thing.

**Human developers have two memory systems:**

- **Working memory:** Small — roughly 4 to 7 items at once. This is the active thinking space.
- **Long-term memory:** Essentially unlimited. Persistent. Associative. Never resets.

A senior developer who has worked on a codebase for a year does not hold millions of lines of code in their head as text. They hold a compressed, structured understanding — architecture at a high level, patterns, relationships, reasons, and the ability to zoom into specific details on demand. This costs zero tokens. It is always available. It was built through months of pair-programming, debugging, reviewing, and making mistakes.

**AI agents have one memory system:**

- **Context window:** Currently 200,000 to 2 million tokens depending on the model. This is both working memory and the only memory. It resets completely every session.

200,000 tokens is roughly 15,000 to 20,000 lines of code. Even models with 1–2 million token windows hold at most 100,000–200,000 lines. A medium production codebase is easily 500,000 or more lines. A large one is millions. Even the largest context windows hold a fraction of a real codebase — and that is before rules, task descriptions, and conversation history consume part of the window. If your rules document is 5,000 lines and your codebase is 500,000 lines, you can fit the rules or a small percentage of the codebase, not both. And the effective capacity is worse than advertised — models become unreliable at 60–70% of their stated limit and struggle to retrieve information positioned in the middle of long contexts.

**The distinction:** A human developer writes code from internalized rules. An AI agent guesses rules from code that happens to be in its context window. Even when rules are explicitly provided, the AI follows them mechanically without understanding why they exist — so it cannot make judgment calls when rules conflict, when rules don't cover a situation, or when an exception is warranted.

**"Just feed the rules at the start of every session" does not solve this:**

- You cannot document everything. A senior developer carries thousands of implicit rules they could not articulate — "don't touch module X because it's fragile and we're refactoring it next quarter," "this function looks wrong but it handles a specific edge case for client Y," "we tried approach Z last year and it caused performance issues under load." These never make it into a rules document because nobody thinks to write them down until someone breaks them.
- Someone must write and maintain the rules. That person needs deep codebase knowledge. That person is a developer. Maintaining a comprehensive rules document is itself ongoing development work — spec writing again, same cognitive work, different output format.
- Every token spent on rules is a token not available for the actual task. The context window is a zero-sum resource. Rules consume space that the AI needs for understanding the code it is working on.

A human developer does not need to be fed the rules every morning. They just know them. The rules are in long-term memory, cost nothing, and are instantly accessible. The AI needs them fed every session, they consume context, and they are still incomplete.

The context gap is a real limitation of AI, but it is not the core argument of this report. AI agents with limited context are still excellent pair-programming partners in synchronous workflows — the developer compensates for the AI's context gaps in real time, pointing the AI to relevant files, explaining implicit rules, course-correcting when the AI misses something. This is why Agile + sync AI works so well.

The context gap becomes a critical problem only in asynchronous workflows, where there is no human in the loop to compensate. The AI is on its own with whatever fits in the context window. Every gap in context becomes a bug that survives to the review phase. The solution is not a bigger context window — it is a human in the loop during coding.

## Why Human Developers Cannot Be Replaced by AI Agents

If AI agents can produce PRs that look identical to a human developer's PRs, why not replace the developers entirely?

This can be proven structurally, not just argued as a risk.

A senior developer with codebase knowledge does Process 1 — pair-programs with AI. During coding, a person with general intelligence and deep codebase understanding is reviewing every line, catching issues, making architectural decisions. The PR is reviewed by the time it is submitted. No second review is needed. They can merge it themselves. This is not vibe code. It was supervised by general intelligence throughout creation.

An AI agent may produce identical-looking code. But during coding, no general intelligence was in the loop. The PR was not reviewed by anyone with general intelligence during creation. It is vibe code by definition — regardless of how good the code appears.

The only way to make the AI agent's PR not vibe code is to add a human with general intelligence to review it. But that adds a separate review phase — which is Waterfall — which is slower than if that human had done Process 1 themselves.

> Senior developer → Process 1 → PR reviewed during creation by general intelligence → can merge → not vibe code
>
> AI agent → codes autonomously → PR not reviewed by general intelligence → two options:
> - Accept as-is → vibe code
> - Add human review → Waterfall → slower than Process 1

There is no path where an AI agent produces non-vibe-code without a human reviewer. And adding a human reviewer creates Waterfall, which is always slower than that human doing Process 1. This is not a current limitation. It is permanent until AI achieves general intelligence.

This has direct consequences for hiring and retention:

**A human developer is an investment with decreasing review cost:**

- Month 1: Needs thorough PR review. High review burden on the lead.
- Month 6: Knows the codebase, conventions, patterns. Review becomes lighter.
- Month 12: Understands architecture, best practices, do's and don'ts. Review is sanity checks.
- Month 18: Owns the feature. Leads it. Review is unnecessary — they are the authority. Who would review their PR? The previous lead who now has the same knowledge? Review becomes ceremonial at most.

The review burden trends toward zero over time. The investment pays off.

**An AI agent is a recurring expense with permanent review cost:**

- Month 1: Needs thorough PR review. Starts fresh, no codebase knowledge.
- Month 6: Needs thorough PR review. Starts fresh, no codebase knowledge.
- Month 12: Needs thorough PR review. Starts fresh, no codebase knowledge.
- Month 18: Needs thorough PR review. Starts fresh, no codebase knowledge.

The review burden never decreases. The AI has no persistent memory across sessions. Its context window resets every invocation. It cannot accumulate understanding of the codebase, the architecture, the history of decisions, or why things are done a certain way. Even if the AI gets smarter per session, it never builds the cumulative knowledge that turns a junior into a senior.

This is not about AI being unintelligent. It is about the architecture of how LLMs work — limited context, no persistent learning, fresh start every invocation. A human developer eventually becomes the most knowledgeable person on their feature. At that point, there is nobody above them with more context. They ARE the authority. AI can never reach this state because it forgets everything between sessions.

The underlying principle is one condition:

> **PR review adds value only when the reviewer's knowledge exceeds the author's knowledge on that specific area.**

When the author's knowledge equals or exceeds the reviewer's, review is zero value. A human developer's knowledge grows over time — it eventually meets or surpasses the reviewer's, and review cost reaches zero. An AI agent's knowledge resets every session — it never accumulates, never catches up, and review cost remains permanent.

- Firing senior developers eliminates the people whose general intelligence makes Process 1 work without review. Preventing juniors from coding eliminates the pipeline that produces those seniors.

The industry is making three simultaneous bets — that AGI will arrive, that it will be affordable, and that it will match human contextual understanding — while treating all three as certainties and making irreversible decisions based on them.

Formally, AI replacing human developers is viable only when all three conditions are met:

> **GI condition:** AI general intelligence ≥ human general intelligence
>
> **Context condition:** AI context capacity ≥ human contextual understanding of codebase, business domain, team conventions, and decision history
>
> **Cost condition:** AI cost < human cost

If any one of these is not met, the replacement fails. Currently, the first condition alone — AI general intelligence matching human general intelligence — is not met. The other two conditions are irrelevant until it is.

If any of those bets fail, the company has no one with the general intelligence needed to maintain, debug, or evolve the system. Codebase knowledge takes years to build. Senior developers take years to grow. The moment you break the pipeline, the damage compounds — and no amount of AI tooling can substitute for a human who understands your system.

## The Vicious Cycle

The degradation from Agile to Waterfall is not a one-time mistake. It is a self-reinforcing loop.

1. AI makes developers faster. Teams adopt Agile + sync AI. Output increases.
2. Leadership sees increased output and reduces headcount. Fewer developers remain.
3. Fewer developers means remaining developers must produce more. Leadership introduces async agents to compensate — "agents can work in parallel while you review."
4. Async agents force the workflow into Waterfall. Developers are now writing specs and reviewing unreviewed PRs with degraded tooling. They get slower, not faster.
5. Leadership sees developers are slower. Demands more speed. The only lever available within the Waterfall model is to reduce or remove human review.
6. Review gets rushed or delegated to AI. Quality drops. Bugs ship. Emergency patches follow.
7. Quality problems create more work — hotfixes, rework, customer escalations. Pressure on remaining developers increases.
8. Return to step 3.

Each step makes the next one worse. The layoffs create the pressure that forces the methodology change that degrades quality that creates more pressure. The cycle cannot be broken from within the Waterfall model. It can only be broken by returning to Agile + sync AI and accepting that the bottleneck is human attention, which cannot be parallelized or removed without accepting vibe code.

**Why leadership does not see the cycle:** The metrics that are visible to leadership reward the async model. "Five PRs created overnight" looks like five times the output. What is not visible: five PRs × three review cycles × two hours each = thirty hours of developer time consumed. The metric that drives the push — PRs created — is not the metric that measures value — working software shipped. Leadership sees agents producing artifacts and developers moving slowly. The conclusion is that developers are the bottleneck. The reality is that the methodology change made them the bottleneck. This is Goodhart's Law applied to software delivery: when PRs created becomes the target, it ceases to be a useful measure of productivity.

## Common Counterarguments

**"Agents can code overnight. You review in the morning. That's free time."**

For the agent to produce quality output overnight, you need to write detailed specs before you leave. That spec-writing is the same cognitive work as coding. You could instead pair-program with AI in sync, produce an already-reviewed PR, and go home. The overnight agent saves no time — it shifts the work to spec writing beforehand and review cycles afterward. Both of which are slower than the sync alternative.

**"Linters, static analysis, and CI/CD can catch issues before human review."**

These tools already exist in Row 3 (Agile + sync AI). They are not unique to the agent workflow. Adding deterministic checks to agent output reduces the human review burden, but if you are trying to eliminate human review entirely, you arrive at Row 6 — AI codes, automated checks review. That is vibe code with a CI pipeline.

**"Vibe code is fine for prototypes and throwaway work."**

Even for throwaway work, the developer still needs to write specs detailed enough for the agent. It is faster to pair-program with AI in sync and produce the prototype directly. Sync coding produces reviewed work as a side effect. Vibe coding produces unreviewed work and still requires the same upfront cognitive effort in spec form.

**"What if cloud IDE tooling improves to provide real-time sync visibility into the agent?"**

That tool already exists. It is called a local IDE with a synchronous agent. If someone builds a cloud tool that provides full IDE access, real-time visibility, ability to interject and redirect — they have built sync. The argument was never about local vs cloud. It was about sync vs async. Inventing sync in the cloud just recreates what already works locally.

**"Ten agents producing mediocre PRs is still more total throughput than one developer on one task."**

Each of those ten agents requires a developer to write detailed specs. The bottleneck is the developer's capacity to produce specs — which is the same cognitive work as coding. You cannot parallelize ten spec-writing tasks for the same reason you cannot parallelize ten coding tasks: there is one developer. And each mediocre PR requires review cycles that further consume that developer's time.

## Q&A — Anticipated Objections

**"Remote developers work asynchronously and receive tasks. That's not Waterfall. Why is it Waterfall when an AI does it?"**

When a remote human developer receives a task, they do not need heavy specs. They can do Agile + sync AI locally — understand the task, pair-program with AI, submit a reviewed PR. If a company writes heavy specs for remote developers, they already have a Waterfall problem. The solution is to fix the methodology, not introduce async agents.

**"What if the spec is just a Jira ticket — the same brief description you'd give a human? Then spec writing cost is zero."**

If the agent can work from a brief Jira ticket, the spec cost shifts to review cycles — the brief spec produces ambiguous output that requires more rounds of feedback. If the agent can work from a brief ticket and produce perfect output, that is Row 6 — AI codes, no meaningful spec, no meaningful review. That is vibe code.

**"Wall-clock time matters more than developer-hours. Three agents producing three PRs by morning beats one developer finishing one task."**

Each of those three agents requires a spec written by the developer. The developer cannot write three detailed specs in parallel. They write them sequentially. Each spec is the same cognitive work as coding. And each resulting PR requires review cycles. The developer's total wall-clock time is: three specs + three review sessions, versus three sync coding sessions. The sync sessions are faster because they produce reviewed work as a side effect.

**"The agent does tasks the developer would never get to. Low-priority bugs, backlog items. That's free additional throughput."**

The throughput is not free. To review the agent's PR, the developer must understand the task — load the context, understand the requirements, read the code. This is the same context-loading required to pair-program with AI on that task. Once loaded, the developer is back in the formula: reviewing unfamiliar code with potential review cycles (Process 2) versus pair-programming directly (Process 1). The review time would be more productive spent pair-programming on any task — whether this one or another. And if nobody reviews the PR, it is vibe code. The agent did not produce free throughput. It produced either slower throughput (if reviewed) or unreviewed code (if not reviewed). In neither case is it free. Furthermore, low-priority bugs and backlog items are exactly the tasks that junior developers should be working on — they are how juniors build codebase knowledge, learn debugging, and grow into seniors. Giving these tasks to agents eliminates the training ground that produces the senior engineers the company will need in five years.

**"Better rules, better CLAUDE.md, better context injection — these reduce review cycles without removing the human."**

These improvements already exist in Row 3 (Agile + sync AI). They are not unique to the agent workflow. They make sync development better too. The structural inequality remains: Process 2 = Process 1 + Formalization Δ + Context Reload + Feedback Latency + Tooling Δ. Improving the agent improves both sides equally.

**"Fine-tuning a model on our codebase gives it persistent knowledge. That solves the context gap."**

Fine-tuning improves the AI — it gives the model better pattern-matching on your specific codebase. But a fine-tuned AI operates in both workflows. In Process 1, the fine-tuned AI is a better pair-programming partner — fewer corrections, faster development. In Process 2, the fine-tuned AI produces better initial PRs — fewer review cycles. The improvement is to the tool, not to the methodology. Process 1 with a fine-tuned AI is still inherently faster than Process 2 with the same fine-tuned AI, because the four axioms are unchanged. Fine-tuning does not eliminate formalization cost, context reload, feedback latency, or tooling delta.

**"The Product Builder is a PM upskilling into a technical role. That's the point."**

If a PM learns the codebase and architecture well enough to write good specs, they have developer-level knowledge. They would be faster pair-programming with AI than writing specs for agents. The Product Builder is not an evolution of the PM — it is a developer operating in a Waterfall methodology under a different title.

**"Developers already context-switch between tasks, meetings, reviews. Managing multiple agents is no different."**

Context-switching between human activities is already a known productivity cost. Adding agent management on top does not solve this — it adds more switching. Each agent requires loading a different task's context. The argument that "we already context-switch" is an argument against adding more context switches, not for it.

**"Not all code needs human review. Internal tools, admin panels, CRUD endpoints — the cost of a bug is low."**

This is a valid business decision to accept vibe code for low-risk code. It does not invalidate the analysis. If you choose not to review, you can vibe code locally with sync AI without review cycles — faster than writing specs for async agents. The async agent adds overhead even to vibe code.

**"Open source works exactly this way — strangers submit PRs, you review in GitHub, no pair-programming."**

In open source, the contributor identified the issue themselves, understood the codebase, created the task, and submitted a PR. They did Process 1 on their own. If you had the task yourself, you could do it faster with Agile + sync AI than by waiting for a stranger's PR.

**"Pair-programming between two humans was rejected by the industry. Isn't sync AI just pair-programming that already failed?"**

Pair-programming was never rejected because it was ineffective. It was rejected because it was expensive — two humans on one task. AI pair-programming gives the same effectiveness without the cost. The industry should be adopting it, not abandoning it for Waterfall.

**"In two years, agents will have full IDE integration, self-review, and run their own tests. They'll do Process 1 internally."**

If an agent can do Process 1 internally — understand the task, code, review, test, course-correct — then it is a fully autonomous developer. The output is vibe code by definition, because no human reviewed it. It may be reliable vibe code. But if you want a human to review the artifact, that human needs to load context and review unfamiliar code, which is slower than if they had pair-programmed from the start.

**"This is theoretical. Where's the data?"**

This is not an empirical claim that requires case studies. It is a structural inequality derived from four axioms: (1) predictive specification costs more than reactive direction, (2) context-switching between phases has non-zero cost, (3) async feedback is slower than sync feedback by definition, (4) a diff viewer does not exceed a full IDE. Each axiom is either definitionally true or established cognitive science. The resulting inequality — Process 2 = Process 1 + Formalization Δ + Context Reload + Feedback Latency + Tooling Δ — holds because every term is strictly positive. You do not need to run experiments to verify that a < a + b when b > 0. You need to show which axiom is false.

**"This analysis only applies to complex backend work. For frontend, for simple endpoints, agents might be better."**

For simple work where review is unnecessary, you are choosing vibe code. That is a valid choice. But you can vibe code faster with sync AI locally — just don't review. The async agent adds overhead even when you skip review, because you still wrote a spec and waited for execution instead of coding directly.

**"Agents can at least handle new feature development, even if they can't debug production issues."**

A significant portion of real development work is not feature creation — it is maintenance, debugging, and incident response. "The /payments endpoint is returning 500s" cannot be specified upfront. It requires real-time investigation: forming hypotheses, tracing through logs, stepping through code, reproducing issues, testing fixes. This is inherently synchronous, exploratory work that is structurally incompatible with async agents. The same applies to exploratory refactoring, performance profiling, and any work where the next step depends on what you discover in the previous step. Even if the async model worked perfectly for feature development — which this report has shown it does not — it would still be inapplicable to a large portion of the work that developers actually do. The model does not merely perform worse on these tasks. It cannot participate in them at all.

**"Agents are useful as exploration tools — fire off a quick prompt, skim the output, throw it away, then do Process 1 properly."**

If the agent's output is never reviewed or merged — if it is purely a thinking aid to understand the problem space — then it is not Process 2. It is a research step before Process 1. This does not challenge the core argument, because the deliverable is still produced through Process 1. However, the same exploration happens naturally during sync pair-programming: ask the AI "how would you approach this?", sketch an approach together, course-correct in real time. The sync version gives the same exploration with faster feedback and no waiting for a separate agent to finish.

**"One senior plus agents is cheaper than five developers. Even if slower per task, the ROI is better."**

This is a cost argument, not a speed argument, and it requires all of the following to hold simultaneously: the one senior can review all the agents' output (the Parallel Agent Fallacy shows they cannot), quality does not degrade without multiple reviewers (it does — rushed review produces vibe code), and the senior does not burn out under the permanent review burden that never decreases (the "Why Human Developers Cannot Be Replaced" section shows it never will). If any one of these fails, the cost savings are consumed by quality problems — hotfixes, rework, customer escalations, and eventual system rewrites. More fundamentally, this model consumes seniors without producing replacements. When the one senior leaves, there is no pipeline of juniors who grew into the role because no juniors were hired. The company is then left with agents that nobody can supervise and a codebase that nobody understands. The short-term cost saving is a long-term existential risk.

**"We have 200 tasks in the backlog and 3 developers. We need agents to cover the gap."**

There are only two options: hire more developers, each doing Process 1, or accept vibe code. Async agents do not create a third option. If the agents' output is reviewed, the 3 developers are now spending their time on review cycles instead of Process 1 — they get fewer tasks done, not more. If the output is not reviewed, it is vibe code. And you cannot vibe code with Process 1 — GI is inherently in the loop during creation, so Process 1 always produces reviewed code. The developer must understand the task regardless of methodology. In Process 2, that understanding goes into a spec that produces unreviewed code. In Process 1, the same understanding goes into directing the AI and produces reviewed code as an inherent side effect. Same cognitive investment, same time — but Process 1 gives you reviewed code and Process 2 gives you vibe code. The backlog pressure does not change the structural inequality. It only changes whether the organization acknowledges the tradeoff it is making. Agents do not scale development. They scale code production. Code production without review is vibe code. Code production with review consumes the same developers who could be doing Process 1 faster.

**"Developers vibe code in sync too — they accept AI suggestions without understanding them. How is that different from async?"**

It is different structurally. Sync development allows GI to be in the loop — the developer can read every line, stop the AI, ask questions, run the code, and verify understanding before accepting. Async development prevents GI from being in the loop during coding — there is no opportunity to interject. A developer who rubber-stamps AI suggestions in sync is choosing not to review. A developer in async has no choice — they cannot review during coding regardless of intent. The report's argument is not that sync guarantees good review. It is that sync makes good review possible while async makes it structurally impossible during the coding phase. The tool that allows review is strictly better than the tool that prevents it.

**"Don't give agents whole features. Give them micro-tasks — 'add this field,' 'rename this variable,' 'add a null check.' The spec is precise, review is trivial."**

The Jira ticket exists in both workflows — it is not additional overhead. The difference is what happens after the ticket. In sync, the developer sees the ticket, tells the AI "add a null check here," and it is done in seconds. In async, the agent picks up the ticket, creates a PR, and the developer must context-switch to review a diff for something they could have coded directly in less time than the review takes. The async ceremony — agent execution, PR creation, context switch, diff review, merge — has a fixed floor regardless of task size. For tasks small enough that this floor dominates, sync is disproportionately faster. If no spec is needed beyond the ticket, there is even less reason to involve an async agent — just code it directly. The micro-task model also fragments development into atomic operations, losing the architectural coherence that comes from a developer working through a feature end-to-end with continuous context.

**"What about mechanical-but-not-trivial tasks — adding a required field to 15 endpoints, updating 30 test fixtures, adding error handling to 20 similar functions? These aren't sed, but they're repetitive."**

The structural inequality still holds. Each of the four terms is still positive. But the magnitude of the delta is small for repetitive mechanical work — the formalization cost is low, the context reload is light, and the review is pattern-based rather than deep. This is the category where the practical difference between Process 1 and Process 2 is smallest. However, even here Process 1 has a structural advantage: if the agent gets the pattern wrong, it gets it wrong on all 15 instances, and you discover this during review — an entire review cycle wasted. In Process 1, you catch it on the first instance, correct it, and the AI gets the remaining 14 right. The cost of a wrong pattern scales with the number of instances in Process 2. It is constant (one correction) in Process 1.

## Key Findings

- **Async agents force Waterfall by structural necessity** — separating coding from review creates sequential phases regardless of tooling
- **Waterfall is strictly slower than Agile + sync AI** — Process 2 = Process 1 + Formalization Δ + Context Reload + Feedback Latency + Tooling Δ; each term is strictly positive by axiom — predictive specification > reactive direction, context-switching has non-zero cost, async feedback is slower than sync by definition, and a diff viewer does not exceed a full IDE; three of the four terms cannot even theoretically reach zero without converting Process 2 into Process 1
- **Every improvement to async converges back to Agile** — if you add interjection, you have Agile with unnecessary spec writing; if you improve tooling, you're rebuilding local sync development in the cloud; every fix recreates sync
- **The only way to make Waterfall faster is to remove human review** — which produces enterprise-scale vibe code
- **The "Product Builder" is a developer under a different name** — coding was never the hard part; the hard part was always understanding whether the code is right, which requires General Intelligence; the cognitive work of writing good specs requires that same understanding
- **AI improvement does not resolve the structural problem** — even with perfect AI, the person writing specs would be faster pair-programming
- **Human attention cannot be parallelized** — multiple agents fragment the developer, they don't multiply them
- **AI agents cannot produce non-vibe-code without human review** — permanent until AI achieves general intelligence
- **A human developer is an investment whose review cost trends to zero** — their knowledge eventually equals or exceeds the reviewer's, making review zero value; an AI agent's knowledge resets every session, so its review cost is permanent
- **AI replacing human developers is viable only when three conditions are met** — AI general intelligence ≥ human general intelligence, AI context capacity ≥ human contextual understanding, and AI cost < human cost; currently the first condition alone is not met, making the other two irrelevant
- **Pair-programming was always the best methodology** — it was just too expensive with two humans; AI made it free

## Conclusion

This report has proven the following:

**Async agents force Waterfall.** When the developer is removed from the coding loop, the workflow necessarily splits into separate phases — spec writing, autonomous execution, after-the-fact review. This is Waterfall by structure, regardless of what it is called.

**Waterfall is strictly slower than Agile + sync AI.** The review phase in Waterfall is the same cognitive work as pair-programming in Agile, but performed as a separate phase with additional overhead. The total time for any Waterfall configuration is: Process 1 + Formalization Δ + Context Reload + Feedback Latency + Tooling Δ. Each term is strictly positive — by the nature of human cognition (formalization cost, context reload) and by definition (async feedback latency, tooling delta). The inequality holds by construction.

**The only way to make Waterfall faster is to remove human review.** Since Waterfall is structurally slower and the purpose of adopting agents was speed, the only available optimization is to cut the phase that makes it slow — human review. This is not a choice anyone makes consciously. It is the only move available. The result is vibe code at enterprise scale.

**The Product Builder is a developer in a Waterfall methodology.** The cognitive work required to write good specs is the same as the cognitive work required to write good code. A person with this knowledge would be faster pair-programming with AI than writing specs for agents. A person without this knowledge produces vibe code.

**AI improvement does not resolve the structural problem.** Even with perfect AI that produces flawless PRs, the person writing the specs still needs developer-level knowledge. That person would still be faster in Process 1 (sync) than Process 2 (async). The inequality is permanent.

**Human attention cannot be parallelized.** Multiple agents require multiple specs, multiple context switches, and multiple review cycles — all from the same human. The bottleneck was always the developer's attention. Agents do not remove this bottleneck. They fragment it.

**AI agents cannot produce non-vibe-code without human review.** A senior developer's Process 1 PR is reviewed by general intelligence during creation — it can merge without further review. An AI agent's PR was never reviewed by general intelligence. Adding human review makes it Waterfall (slower). Skipping review makes it vibe code. This is permanent until AI achieves general intelligence. Firing seniors and preventing junior growth is an irreversible bet on AGI arriving, being affordable, and matching human contextual understanding.

There is no configuration of async agents that is faster than sync AI for anyone with the knowledge to do the work. This is not a tool preference, an opinion, or a prediction. It is a structural property of the workflows.

---

*This analysis is based on first-principles structural reasoning about development workflows, not on any specific tool, vendor, or implementation.*
