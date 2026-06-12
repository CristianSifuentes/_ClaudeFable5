# Claude Fable 5 — Complete Expert Course

> Master Anthropic's most capable model from day one: prompting, pricing, Claude Code integration, and production-grade workflows — all in one place.

---

## Table of Contents

1. [Claude Fable 5: What Changes and When to Use It](#1-claude-fable-5-what-changes-and-when-to-use-it)
2. [Technical Architecture: How Claude Fable 5 Works Under the Hood](#2-technical-architecture-how-claude-fable-5-works-under-the-hood)
3. [Advanced Prompting Techniques for Claude Fable 5](#3-advanced-prompting-techniques-for-claude-fable-5)
4. [Pricing, Costs & Availability — What You Must Know Before Integrating](#4-pricing-costs--availability--what-you-must-know-before-integrating)
5. [Claude Code + Claude Fable 5: The Ultimate Developer Workflow](#5-claude-code--claude-fable-5-the-ultimate-developer-workflow)
6. [Model Comparison & Decision Framework: Fable 5 vs Previous Models](#6-model-comparison--decision-framework-fable-5-vs-previous-models)
7. [Building Production-Ready Workflows with Claude Fable 5](#7-building-production-ready-workflows-with-claude-fable-5)

---

## 1. Claude Fable 5: What Changes and When to Use It

### Course Overview

**Claude Fable 5** is the newest model from Anthropic — the company behind Claude Opus and Claude Code. It arrives as a powerful tool for developers and anyone serious about leveraging state-of-the-art AI in real work.

Anthropic published launch documents, tutorials, and detailed articles about this model. All of that material has been distilled into a short, effective, and practical course designed to be useful from the very first day.

### What You Will Learn

This course focuses on what matters most to get productive fast. The goal is that you make informed decisions about when and how to use Claude Fable 5.

Core topics covered throughout all 7 sections:

| Topic | What You Get |
|---|---|
| Ideal prompting techniques | Patterns that unlock the model's full potential |
| Limitations and costs | Honest constraints you need to plan around |
| When to use it vs. when not to | A practical decision framework |
| Unique model characteristics | What sets Fable 5 apart from every predecessor |

### Key Characteristics of the Model

Claude Fable 5 is currently available exclusively to Claude subscribers until a specific date. It also carries particular pricing that is worth understanding before integrating it into any workflow.

There is one critical behavior to be aware of: **when given certain tasks, the model automatically blocks and falls back to Opus 4.8.** This is not a bug — it is a deliberate safety and capability boundary baked into the model's design. Knowing exactly which task categories trigger this behavior will save you hours of debugging.

Despite these constraints, Claude Fable 5 is substantially superior to its predecessors across reasoning, code generation, long-context understanding, and agentic task execution.

### How This Course Was Built

This course format was built using **Platzi Learn** — an internal Platzi tool for rapid content generation. Some lessons may feel AI-assisted in structure. The invitation is clear: treat it as an experiment and give it a real chance.

Watch every lesson completely — especially the first one — before forming a judgment. These lessons are better than the format might initially suggest. Your direct experience is the most reliable evaluation.

### Why Your Feedback Matters

The Platzi team reads every comment on every lesson. That feedback directly improves the model and the content creation system. Because of that system, this course launched **less than one hour after Claude Fable 5 was publicly released**.

Platzi Learn is designed to be used only where it genuinely adds value — moments like this, when a major model drops and you need expertise immediately.

---

## 2. Technical Architecture: How Claude Fable 5 Works Under the Hood

### Proof Point: The Stripe Migration

Before the architecture, a real-world result that defines what this model is.

A team of engineers at Stripe had a **50-million-line Ruby migration** on their roadmap. Human estimate: more than two months of engineering work. Claude Fable 5 completed it in a single day.

That is not an incremental improvement over Opus 4.8. It is a categorical shift in what you can delegate.

One critical nuance: **that result did not come from typing "migrate this code" and waiting.** It came from precise delegation — a clear objective, explicit context, defined verification criteria, and a well-structured prompt. The model is the engine; the prompt is the blueprint. A mediocre blueprint produces mediocre output regardless of how capable the engine is.

### Real-World Agentic Case Studies

The Stripe migration is the most cited example, but it is not isolated. Two more documented cases illustrate the range of domains where autonomous, long-horizon execution has produced verifiable results.

#### Case Study: Genomic Research

Task: assemble and analyze single-cell data at scale.

- Worked autonomously for **more than one week** without human intervention
- Assembled data from **millions of cells across 138 species**
- Designed a machine learning model from the assembled dataset
- Produced results that **surpassed a published finding in Science**

The key capability here: the model maintained coherent research context across an extended session — writing its own intermediate notes and consulting them later, like a researcher with a lab notebook. This is not a feature layered on top; it is part of how the model manages long-horizon tasks without losing thread.

#### Case Study: Protein Design for Drug Discovery

Task: identify binding sites and produce protein candidates.

- Autonomously **chose binding sites** across 14 target proteins
- Executed specialized protein design tools without human guidance
- **Self-recovered from tool failures** without prompting
- Result: **9 of 14 target proteins** produced strong drug candidates

The self-recovery from failures is architecturally significant. When a tool call fails, the model does not stop and ask what to do — it diagnoses the failure, adjusts its approach, and retries. This is the behavior that makes it deployable in research pipelines where a human cannot be on call for every unexpected API response.

#### What These Cases Have in Common

```
Stripe migration        → Software engineering   → 50M lines, 1 day
Genomic research        → Scientific research    → 1+ week autonomous
Drug design             → Computational biology  → 9/14 targets, self-recovering

Common pattern:
─────────────────────────────────────────────────────
1. Multi-day or multi-step scope impossible to hand-hold
2. Clear goal with measurable end state (tests pass / Science result / candidates)
3. Access to domain tools the model could invoke autonomously
4. Human reviews the final output, not every intermediate step
─────────────────────────────────────────────────────
```

### Fable 5 vs Mythos 5: Same Engine, Different Gates

Both models share the **exact same underlying architecture**. The difference is what sits in front of it.

```
Claude Fable 5
──────────────────────────────────────────────────────────
[Request] → [Safety Classifier Layer] → [Core Model] → [Response]
                      ↑
             Intercepts requests in categories:
             cybersecurity, biology, and others.
             When triggered → redirects to Opus 4.8 fallback.

             Think of it as: a building with a security guard.
             Same building. The guard decides who enters.
──────────────────────────────────────────────────────────
✓ Available: all users with API access or compatible subscription
✓ Self-serve: yes
```

```
Claude Mythos 5
──────────────────────────────────────────────────────────
[Request] → [Core Model] → [Response]

             Same building. No guard. No classifiers.
             Maximum capability, no safety interception.
──────────────────────────────────────────────────────────
✗ Available: approved organizations only (Project Glasswing)
✗ Self-serve: no — requires formal access approval
```

**There is no Claude Haiku 5.** No confirmed model ID exists, and no availability has been published for this generation. If you see it referenced anywhere, there is no documentation to support it.

Both models share the same pricing tier: `$10/M input tokens · $50/M output tokens`.

### Project Glasswing: Access to Mythos 5

Glasswing is the Anthropic program that grants access to Mythos 5 — the classifier-free variant. There are four access paths:

| Path | Self-Serve | Status |
|---|:---:|---|
| Partnership with Anthropic account team | No | Active |
| Claude for Open Source (repo maintainers) | No | Active |
| **Cyber Verification Program** | **Yes** | **Active** — `claude.com/form/cyber-use-case` |
| Biology Trusted-Access Program | No | Planned, not yet active |

The Cyber Verification Program is the **only self-serve path into Glasswing today**. It is designed for security professionals doing pentesting, red-teaming, and offensive research who consistently hit the Fable 5 classifier.

For all other use cases, Fable 5 with correct fallback handling is the right path. Mythos 5 is not an upgrade you select for general productivity tasks — it is an access tier with a specific use-case rationale that Anthropic reviews before granting.

### Agentic vs. Assistant: The Fundamental Distinction

Every previous Claude model — including Opus 4.8 — was an **assistant model**: you ask a question, it answers; you give a task, it completes the next step; you need more, you ask again. The human is the loop.

Claude Fable 5 is an **agentic model**: you hand it a project with a goal and it returns a completed result. The model is the loop.

```
Assistant model (Opus 4.8 and earlier)
──────────────────────────────────────
Human: "Do step 1"
Model: [does step 1]
Human: "Now do step 2"
Model: [does step 2]
Human: "Step 3 needs a different approach, here's context..."
Model: [does step 3]
→ Human drives every step

Agentic model (Fable 5)
──────────────────────────────────────
Human: "Here is the goal and the constraints."
Model: [step 1 → evaluates result → step 2 → adjusts → step 3 → ... → final output]
→ Model drives execution; human reviews the result
```

This distinction explains the Stripe migration. An assistant model would have required a human to approve every file change, review every test, and unblock every ambiguity. An agentic model reads the codebase, forms a migration plan, executes it, runs the test suite, and iterates until the suite passes — without a human in the middle.

### The Transformer Foundation (and What Changed)

Claude Fable 5 builds on the dense transformer architecture Anthropic has refined across the Claude 3 and Claude 4 families, with significant changes in three areas:

```
Standard Transformer Stack
─────────────────────────────────────
Tokenizer → Embedding Layer
         → N × [Attention + FFN]
         → Output Head (logits)
─────────────────────────────────────

Claude Fable 5 Additions
─────────────────────────────────────
+ Extended context window (200K tokens)
+ Improved multi-step reasoning chains
+ Enhanced tool-use / function-calling layer
+ Tighter safety classifiers at inference time
─────────────────────────────────────
```

### Context Window: 200K Tokens in Practice

| Context Size | Real-World Equivalent |
|---|---|
| 4K tokens | ~3,000 words (short article) |
| 32K tokens | ~24,000 words (short novel chapter) |
| 100K tokens | ~75,000 words (full novel) |
| **200K tokens** | **~150,000 words (entire codebase + docs)** |

This is the architectural detail that matters most for developers. You can now pass an **entire repository, its documentation, and a multi-turn conversation history** in a single prompt without chunking or retrieval gymnastics.

### Constitutional AI & RLHF: The Safety Layer

Anthropic trains Claude models with a two-stage approach:

1. **Supervised fine-tuning (SFT)** — The model learns from human-curated demonstrations of desired behavior.
2. **Reinforcement Learning from Human Feedback (RLHF)** — A reward model scores outputs, and the policy is updated to maximize the reward.

Claude Fable 5 adds a third element:

3. **Constitutional AI (CAI)** — A set of written principles ("the constitution") that the model uses to critique and revise its own outputs during training, reducing reliance on expensive human labeling for every safety scenario.

This is why the automatic fallback to Opus 4.8 exists: the safety classifiers identify certain task categories as out-of-scope for Fable 5's current deployment configuration, and route them accordingly.

### Tool Use Architecture

Claude Fable 5 supports native tool/function calling, structured JSON output, and multi-turn agentic loops. The architecture looks like this:

```
User prompt
    │
    ▼
[Claude Fable 5 — Reasoning Layer]
    │
    ├── No tool needed → Direct text response
    │
    └── Tool call needed
            │
            ▼
        Tool definition (JSON schema)
            │
            ▼
        External execution (your code / API)
            │
            ▼
        Tool result injected into context
            │
            ▼
        [Claude Fable 5 — Synthesis Layer]
            │
            ▼
        Final response
```

This loop can repeat multiple times within one API call, enabling autonomous multi-step tasks without manual orchestration.

### What Makes Fable 5 Specifically Different

- **Improved instruction-following fidelity** — Longer, more nuanced system prompts are followed more precisely.
- **Reduced "sycophancy"** — The model pushes back more reliably when given incorrect premises.
- **Better code editing vs. code generation** — Prior models excelled at generating code from scratch; Fable 5 shows significant improvement in editing, refactoring, and migrating existing codebases.
- **Multi-modal reasoning** — Enhanced image understanding integrated tighter with text reasoning chains.
- **Native visual processing without plugins** — Fable 5 can interact with graphical interfaces, dashboards, and forms using only what it sees on screen. Where previous workflows required plugins or custom scrapers to pass UI state to the model, Fable 5 reads it directly. This simplifies any flow where the model must interpret visual data: charts, web interfaces, PDFs, screenshots.
- **Token efficiency** — Fable 5 produces measurably better results while consuming approximately **half the tokens of Opus 4.8** for equivalent tasks. Think of it as a precision instrument: rather than disassembling the whole structure to find the problem, it places the exact beam needed.
- **Thinking is always active** — Unlike Opus 4.8, where internal reasoning was an optional feature you toggled, Fable 5 reasons before every response without exception. You cannot disable it. You can only regulate its depth with `effort` and control its visibility with `display`.

### Adaptive Thinking: Always On, Configurable Depth

This is the architectural change responsible for the most broken integrations on launch day. Developers with working Opus 4.8 code started receiving HTTP 400 errors with no explanation — same request, same endpoint, different model, broken.

```
Opus 4.8 thinking model           Fable 5 thinking model
───────────────────────────────    ───────────────────────────────
Off by default                     Always on — no off switch
You turn it on when needed         Already running when you arrive
You allocate a token budget        Budget managed internally (adaptive)
Sending thinking: disabled → ok    Sending thinking: disabled → HTTP 400
```

Think of it as an engine. In Opus 4.8, the engine started cold and you decided when to turn the key. In Fable 5, the engine is already running. You can control the RPMs with `effort`, and decide whether to see the exhaust with `display` — but you cannot turn the engine off.

**Two safe migration paths from Opus 4.8:**

```python
# Option A: Omit the thinking field entirely (recommended)
response = client.messages.create(
    model="claude-fable-5",
    max_tokens=8192,
    messages=[{"role": "user", "content": prompt}]
    # No thinking field — model uses adaptive defaults
)

# Option B: Explicit adaptive declaration
response = client.messages.create(
    model="claude-fable-5",
    max_tokens=8192,
    thinking={"type": "adaptive"},   # explicit but equivalent to omitting
    messages=[{"role": "user", "content": prompt}]
)
```

**What breaks from Opus 4.8 code:**

```python
# BREAKS — thinking: disabled is not valid in Fable 5
response = client.messages.create(
    model="claude-fable-5",
    thinking={"type": "disabled"},   # → HTTP 400 immediately
    ...
)

# BREAKS — manual token budget is not accepted
response = client.messages.create(
    model="claude-fable-5",
    thinking={"type": "enabled", "budget_tokens": 5000},  # → HTTP 400
    ...
)
```

**The silent migration trap — `max_tokens` exhausted by reasoning:**

Routes in Opus 4.8 that ran without thinking spent zero tokens on reasoning. The same request in Fable 5 consumes part of your `max_tokens` budget on internal reasoning before writing a single word of output.

```
Opus 4.8 classification request (max_tokens=256):
  Thinking tokens:  0
  Output tokens:   256 available for text

Fable 5 classification request (max_tokens=256):
  Thinking tokens:  ~200 (consumed before output starts)
  Output tokens:    ~56 remaining for text
  Result:           Truncated or empty response
```

If you have tasks where `max_tokens` was tuned tightly for Opus 4.8, audit them before migrating. Diagnose by reading `usage.output_tokens_details.thinking_tokens` — if it is consuming the majority of your allocated tokens, either raise `max_tokens` or lower `effort` for that route.

---

## 3. Advanced Prompting Techniques for Claude Fable 5

### The Core Mental Model

Claude Fable 5 responds best when you treat it as a **very capable, honest collaborator** rather than a search engine or a code autocomplete tool. This shapes every prompting decision.

```
WRONG mental model:  "Give me the answer to X."
RIGHT mental model:  "Here is the context, here is my goal,
                      here are my constraints — work with me."
```

### Technique 1: System Prompt Architecture

The system prompt is the most underused lever in the API. For Fable 5, structure it in three blocks:

```
[ROLE]
You are a senior software engineer specializing in distributed systems.
You write production-grade Python. You do not add unnecessary comments.

[CONSTRAINTS]
- Always return structured JSON when the user requests data.
- If a request is ambiguous, ask one clarifying question before proceeding.
- Never hallucinate library APIs. If unsure, say so.

[CONTEXT]
The codebase uses Python 3.12, FastAPI, SQLModel, and Alembic.
The target environment is AWS Lambda behind API Gateway.
```

This three-block pattern works because it separates **who the model is**, **what it must never do**, and **what world it operates in** — three distinct cognitive contexts.

### Technique 2: Chain-of-Thought with Explicit Checkpoints

For complex reasoning tasks, force the model to externalize its thinking at defined checkpoints rather than just asking for the final answer:

```
Bad:   "Refactor this function to be more efficient."

Good:  "Refactor this function. First, identify the bottleneck
        and explain it in one sentence. Second, list the approaches
        you considered and why you ruled each out. Third, write
        the refactored version with a brief comment on what changed."
```

The intermediate steps are not just useful for you — they **improve the quality of the final output** because the model's own reasoning is now part of the context it attends to.

### Technique 3: Negative Constraints

Claude Fable 5 responds very well to explicit "do not" instructions. Use them proactively:

```
Do not use third-party libraries unless I specify one.
Do not add error handling unless I ask for it.
Do not explain what the code does — only write the code.
Do not repeat my question back to me before answering.
```

Each of these reduces hedging, reduces padding, and reduces the model doing work you did not ask for.

### Technique 4: Role-Primed Context Injection

When injecting large documents (logs, codebases, reports), prime the model with a reading role before the document:

```
You are performing a security audit.
Read the following server logs and identify:
1. Failed authentication attempts
2. Unusual request patterns
3. Any evidence of data exfiltration

<logs>
[...200K tokens of logs...]
</logs>

Now provide your findings.
```

Without the role primer, the model treats the document as neutral data. With it, attention is focused and the output is more precise.

### Technique 5: The "Skeleton + Fill" Pattern for Long Documents

For long structured outputs (reports, documentation, code modules), give the model a skeleton first:

```
Here is the outline I need you to fill in:

# Report: Q2 Infrastructure Cost Analysis

## 1. Executive Summary
[Fill: 3 sentences max]

## 2. Key Cost Drivers
[Fill: bullet list, each with dollar amount and % of total]

## 3. Recommendations
[Fill: 3 actionable items ranked by impact]
```

This pattern prevents the model from deciding its own document structure — which is where most unwanted verbosity and hallucinated sections come from.

### Technique 6: The Four-Component Delegation Framework

This is the most important framework in this course. The difference between a result you can hand to your manager and a mediocre result is almost never the model — it is the quality of the delegation.

Most people get poor results because they write vague prompts. "Make me a sales report" is not a work order; it is a wish. Fable 5 is powerful but does not read your mind. A well-structured delegation has exactly four components:

---

**Component 1: Clear Objective**

Define the final deliverable and the precise moment when the work is truly done. Ambiguity here is the single most common cause of poor output.

```
Weak:  "Search for relevant information."

Strong: "Find all articles published in these three sources between
         January and June 2025. For each article, write a one-paragraph
         summary. Stop when all articles from all three sources have a
         summary. Do not proceed to any other task."
```

The stopping condition is not optional. Without it, the model decides when it is done — and its definition of "done" may not match yours.

---

**Component 2: Relevant Context**

Give the model information it needs to **decide well**, not just information it needs to act. There is a difference.

```
Include:
- What resources are available (files, APIs, databases, tools)
- What constraints apply (budget, format, audience, deadline)
- What has already been tried and ruled out

Omit:
- Credentials and API keys (pass via environment, not in the prompt)
- Personal data the task does not strictly require
- Confidential figures that do not affect the decision logic
```

Context given at the start shapes every downstream decision the model makes. Incomplete context means the model fills gaps with assumptions — and those assumptions may not match your reality.

---

**Component 3: Expected Delivery Format**

Describe exactly what the result looks like and what evidence must be present in it.

```
Weak:  "Give me a report on the analysis."

Strong: "The report must include:
         - The actual raw output of each tool call (not a paraphrase)
         - The exact query used for each data source
         - A table with one row per finding, columns: source / finding / confidence
         Do not summarize what you expected to find — show what you found."
```

This constraint prevents one of the model's most common failure modes: producing a polished summary of what the analysis was supposed to find rather than showing the actual data.

---

**Component 4: Review Criteria**

State explicitly what "correct" looks like in terms of verifiable, real-world outcomes — not in terms of how complete or confident the output sounds.

```
Weak:  "The answer is correct if it sounds thorough and complete."

Strong: "The answer is correct if:
         1. Each finding can be traced back to a specific tool output in the report
         2. No source is cited that was not explicitly in the provided list
         3. The final section lists every assumption the model made that was
            not verified against real data — this list is mandatory, not optional"
```

The mandatory list of unverified assumptions is the most powerful element here. It forces the model to be honest about what it inferred vs. what it confirmed, and it is exactly what prevents you from presenting the model's assumptions to your manager as verified facts.

---

**Full Template**

```
OBJECTIVE:
[What is the final deliverable? What does "done" look like exactly?]

CONTEXT:
Resources available: [list files, tools, data sources]
Constraints: [format, audience, budget, what to avoid]
Background: [relevant prior decisions or context]

DELIVERY FORMAT:
The output must contain:
- [Specific element 1 with format]
- [Specific element 2 with format]
- [Mandatory list of unverified assumptions at the end]

REVIEW CRITERIA:
The result is correct if:
- [Criterion 1: verifiable against real data]
- [Criterion 2: traceable to specific source]
- [Criterion 3: explicit about what was not verified]
```

---

### Technique 7: Request a Plan Before Execution

For any task with serious downstream consequences, add one word to your prompt: **"plan"**.

```bash
# Instead of:
claude -p "Refactor the authentication module"

# Use:
claude -p "Plan a refactor of the authentication module.
           List every file you will touch, every change you will make,
           and every test you expect to pass afterward.
           Do not make any changes yet — only the plan."
```

Then review the plan. Only once you have approved the scope does execution begin.

This single habit prevents the majority of "the model did too much / the wrong thing" incidents, and it costs almost nothing in tokens relative to the full task.

### Prompting Anti-Patterns to Avoid

| Anti-Pattern | Why It Fails | Fix |
|---|---|---|
| "Be concise" at the end | Model already drafted the response | Put constraints at the top |
| Vague role: "You are a helpful assistant" | No signal for the model to calibrate | Use a specific, expert role |
| Over-praising in prompts | Correlated with lower-quality outputs | Be neutral and professional |
| "Do your best" | Zero information content | Specify the success criterion |
| Mixing multiple tasks in one prompt | Attention splits across tasks | One task per prompt |
| Prompt without stopping condition | Model decides when "done" means | Always define the end state explicitly |
| Accepting "verified" without proof | Model may have done partial checks | Require actual tool output, not status claims |

---

## 4. Pricing, Costs & Availability — What You Must Know Before Integrating

### Availability Tiers

Claude Fable 5 follows a staged rollout:

```
Phase 1: Claude.ai subscribers (Pro + Team plans) — exclusive access
Phase 2: Anthropic API — token-based pricing
Phase 3: Bedrock / GCP Vertex AI — cloud provider availability
```

If you are evaluating whether to build on Fable 5, assume Phase 1 availability with Phase 2 arriving on a defined date. **Do not architect a production system on subscriber-only access.**

### Plan-Specific Access Rules

Access to Fable 5 is not uniform across plans. The rules differ significantly depending on how you pay.

| Plan Type | Access Model | Notes |
|---|---|---|
| **API** | Full access, pay per token | No additional restrictions; cost scales with usage |
| **Enterprise (consumption-based)** | Full access, pay per token | Same as API — no caps |
| **Pro / Max / Team (subscription)** | Requires additional credits after June 23 | See credit burn rates below |

**Subscription plan detail:** After June 23, using Fable 5 on Pro, Max, or Team plans requires purchasing credits on top of your subscription fee. Anthropic plans to reintegrate Fable 5 as a standard subscription feature once compute capacity scales, but there is no committed date.

Analogy: a streaming service that gives you free access to a premium channel for two weeks and then charges extra. Plan your budget accordingly.

### Credit Burn Rates on Subscription Plans

Agentic use is orders of magnitude more token-intensive than conversational use. The model runs multiple internal reasoning steps, tool calls, and self-corrections per task — all of which consume credits.

```
Plan: Max ($100/month)
Standard allocation: ~6 hours of usage per cycle

Real-world result with intensive agentic workflows:
→ Entire 6-hour allocation exhausted in 20 minutes
```

This is not an edge case. Any workflow that involves multi-file editing, autonomous research, or tool-calling loops will trigger this burn rate.

**Before committing to a subscription plan for agentic work, run one representative task and measure actual credit consumption.** Then extrapolate to your monthly volume. API/Enterprise pricing is almost always more cost-predictable at scale.

### Confirmed Pricing and Model Specifications

These are the published figures for Claude Fable 5 (and Mythos 5, which shares the same tier):

```
Pricing
────────────────────────────────────────
Input tokens:    $10.00 per million tokens
Output tokens:   $50.00 per million tokens
────────────────────────────────────────
Output is 5× the cost of input.

Context window:  1,000,000 tokens (1M)
Max output:      128,000 tokens per request
────────────────────────────────────────
```

The 1M token context window is the largest in any Anthropic model to date. In practice, this means you can load:
- An entire large codebase with full history
- All documentation + tests + CI config simultaneously
- A year of financial statements in one prompt

The 128K max output per request is the ceiling on a single response. For tasks that require more output than this, you need to structure the work into sequential requests.

### Data Retention Requirement: The Silent 400 Error

**This is the most common silent failure for enterprise deployments.**

Claude Fable 5 requires **30-day data retention** on the Anthropic side. If your organization has `zero-data-retention` (ZDR) enabled on your account, every Fable 5 request returns a `400` error with no model-specific explanation.

```
Organization setting   →  Result
────────────────────────────────────────────────────
Standard (default)     →  Fable 5 works normally
ZDR enabled            →  HTTP 400 on every request
────────────────────────────────────────────────────
Workaround if ZDR required: use Opus 4.8, which
supports zero-data-retention configurations.
```

Check your organization's data retention settings before deploying Fable 5. Enterprise security teams often enable ZDR org-wide without realizing it affects model availability.

```python
# Detect and handle the ZDR 400 silently
try:
    response = client.messages.create(model="claude-fable-5", ...)
except anthropic.BadRequestError as e:
    if "data retention" in str(e).lower():
        # Fall back to Opus 4.8 which supports ZDR
        response = client.messages.create(model="claude-opus-4-8", ...)
    else:
        raise
```

### Token Pricing Model

Anthropic prices all Claude models on a per-token basis, split between input and output:

```
Input tokens:  text you send in (prompt + context + tools)
Output tokens: text the model generates (response + tool calls)

Output tokens are priced 5× higher than input tokens.
```

#### Cost Estimation Framework

```python
# Rough estimator (adjust multipliers for your actual plan)

input_tokens  = len(prompt_text) / 4          # ~4 chars per token
output_tokens = expected_response_length / 4

input_cost  = input_tokens  * INPUT_PRICE_PER_TOKEN
output_cost = output_tokens * OUTPUT_PRICE_PER_TOKEN
total_cost  = input_cost + output_cost

# Always measure both directions — long contexts cost money
# even before the model writes a single output token.
```

### Fable 5 Costs 2× More Than Opus 4.8

This is not a footnote — it is a design constraint that should inform every architecture decision.

```
Claude Opus 4.8    baseline cost
Claude Fable 5     ~2× Opus 4.8 per token

Implication: spending well is as important as producing well.
A well-delegated task on Fable 5 is cheaper than a poorly-delegated
task on Fable 5 run multiple times with retries.
```

The token efficiency advantage (~50% fewer tokens for equivalent results) partially offsets this multiplier. But the net effect for most workloads is still a higher per-task cost compared to Opus 4.8. This means you need to be deliberate: **use Fable 5 for tasks that are large, bounded, and verifiable** — not for tasks where Sonnet 4.5 or Opus 4 would do.

### API Parameters That Produce 400 Errors in Fable 5

This is the highest-frequency breaking change when migrating from Opus 4.8 or earlier models. The minimum valid payload for Fable 5 has three required fields and three forbidden ones.

```python
# Minimum valid payload — nothing more, nothing less required
{
    "model": "claude-fable-5",
    "max_tokens": 128000,
    "messages": [{"role": "user", "content": "your message"}]
}
```

**Parameters that produce HTTP 400 if included:**

```
Parameter                 Why it fails
────────────────────────────────────────────────────────────────────
thinking: {type: "disabled"}   Thinking is ALWAYS active in Fable 5.
                                You cannot disable it. Sending disabled
                                returns 400 immediately.

temperature                    Not supported. Fable 5 manages its own
                                sampling internally. Including this field,
                                even as null, returns 400.

top_p                          Same — not supported, returns 400.

top_k                          Same — not supported, returns 400.

Assistant prefill              Pre-filling the assistant turn is blocked.
(messages[-1].role = "assistant")  Not allowed in Fable 5 requests.
────────────────────────────────────────────────────────────────────
```

If your existing code sets any of these — even with default or null values — it will fail against Fable 5 without a model-specific error message. The 400 just says "invalid request."

```python
# Migration check: scan for forbidden parameters before deploying
FABLE5_FORBIDDEN = {"temperature", "top_p", "top_k"}

def validate_fable5_payload(payload: dict) -> list[str]:
    errors = []
    for key in FABLE5_FORBIDDEN:
        if key in payload:
            errors.append(f"Remove '{key}' — not supported in Fable 5")
    thinking = payload.get("thinking", {})
    if thinking.get("type") == "disabled":
        errors.append("thinking.type='disabled' is invalid — thinking is always active")
    messages = payload.get("messages", [])
    if messages and messages[-1].get("role") == "assistant":
        errors.append("Assistant prefill not allowed in Fable 5")
    return errors
```

Run this validator against your existing request builders before switching `model` to `claude-fable-5`.

### Display Modes: Visibility vs Cost

The `display` parameter controls what you can see of the model's internal reasoning. It has no effect on what you are billed.

```
display mode    What you receive                    Streaming behavior
─────────────────────────────────────────────────────────────────────────
omitted         thinking field = empty string       No thinking deltas sent.
(default)       Encrypted signature included        Text response starts
                (required for multi-turn)           arriving immediately.

summarized      Condensed readable reasoning        Summary arrives first.
                Encrypted signature included        Text response starts
                                                    after summary is complete.
─────────────────────────────────────────────────────────────────────────
```

**The counterintuitive billing rule:** generating the summary is free. Billing is identical in both modes. `omitted` reduces latency (lower time-to-first-text-token); it does not reduce your bill.

```
When to use each:
omitted     → Production. Faster time-to-first-text. Reasoning is internal.
summarized  → Debugging sessions and UIs with an expandable reasoning drawer.
              Never in high-volume production paths.
```

### Reading `usage` to Understand Your Actual Fable 5 Bill

At $50/million output tokens, the difference between a well-tuned and a poorly-tuned Fable 5 integration can be substantial. The `usage` object gives you the data you need to tune.

```python
response = client.messages.create(
    model="claude-fable-5",
    max_tokens=4096,
    messages=[{"role": "user", "content": prompt}]
)

u = response.usage

# Total billed output tokens (thinking + text combined)
print(f"Total output billed:  {u.output_tokens}")

# Breakdown — requires output_tokens_details
if hasattr(u, "output_tokens_details"):
    thinking = u.output_tokens_details.thinking_tokens
    text     = u.output_tokens - thinking
    print(f"  Thinking tokens:    {thinking}   (${thinking / 1_000_000 * 50:.4f})")
    print(f"  Text tokens:        {text}   (${text / 1_000_000 * 50:.4f})")

# Input cost
print(f"Input tokens:         {u.input_tokens}  (${u.input_tokens / 1_000_000 * 10:.4f})")
```

**Practical use:** if `thinking_tokens` is consuming 80%+ of your `output_tokens` budget on a simple classification route, that route should have its `effort` level lowered — or should be routed to Haiku 3.5 entirely.

**What the raw chain of thought looks like — and what you never see:**

```
What you receive in any display mode:
  thinking field:  "" (empty)  OR  "The user is asking about X..."  (summary)
  + encrypted signature string (for multi-turn continuity)

What you NEVER receive, under any configuration:
  The actual internal reasoning tokens.
  The full chain of thought is never exposed.
  This is not configurable.
```

### The Expensive Mistakes (and How to Avoid Them)

| Mistake | Cost Impact | Fix |
|---|---|---|
| Passing full codebase on every turn | High — input tokens × turns | Cache static context; only pass diffs |
| Streaming without token counting | No visibility into spend | Log token usage per request |
| Using Fable 5 for simple classification | Overkill — 2× Opus price for a haiku-level task | Route simple tasks to Haiku 3.5 |
| Retrying on hallucination instead of constraining | Doubles cost for the same task | Add output validation before retry |
| Ignoring context window limits | Truncation = invisible data loss | Always track token count in context |
| Vague prompts requiring multiple clarification rounds | Each round = full context retokenized | Use the Four-Component Framework upfront |

### The Fallback Behavior: Opus 4.8

When Claude Fable 5 encounters task categories outside its deployment configuration, it **automatically downgrades to Opus 4.8**. This matters for cost budgeting because:

- Opus 4.8 has a different pricing tier
- The switch happens silently unless you log the model field in the API response
- Some tasks will consistently trigger the fallback — test your use cases before going to production

**Always log `response.model` from the API response.** This tells you which model actually ran, not which model you requested.

```python
import anthropic

client = anthropic.Anthropic()
response = client.messages.create(
    model="claude-fable-5",
    max_tokens=1024,
    messages=[{"role": "user", "content": your_prompt}]
)

# Always check which model actually ran
print(f"Requested: claude-fable-5")
print(f"Actual:    {response.model}")
print(f"Tokens:    in={response.usage.input_tokens} out={response.usage.output_tokens}")
```

### Cost Optimization Checklist

- [ ] Route classification/extraction tasks to Haiku 3.5
- [ ] Use prompt caching for system prompts > 1024 tokens (API feature)
- [ ] Set `max_tokens` explicitly — never leave it at the maximum
- [ ] Compress context aggressively before injection (summaries, not raw text)
- [ ] Batch non-time-sensitive requests using the Batch API (50% cost reduction)
- [ ] Monitor spend per feature, not per user

---

## 5. Claude Code + Claude Fable 5: The Ultimate Developer Workflow

### What Is Claude Code?

Claude Code is Anthropic's official CLI tool for AI-assisted software development. It runs in your terminal, reads your codebase, and lets Claude operate as a real development collaborator — not just a chat window.

```bash
# Install Claude Code
npm install -g @anthropic-ai/claude-code

# Start a session in your project root
claude
```

### How Claude Code Uses Claude Fable 5

Claude Code selects the model based on task complexity:

```
Simple queries          → Claude Haiku 3.5 (fast, cheap)
Code generation / edit  → Claude Sonnet 4.5 (balanced)
Multi-file refactors    → Claude Fable 5 (full reasoning)
Agentic long-horizon    → Claude Fable 5 (autonomous loops)
```

When working with Claude Fable 5 through Claude Code, the full 200K context window means the tool can load your **entire repository** and reason about it holistically — no chunking, no vector search, no missed dependencies.

### Essential Claude Code Commands

```bash
# Start interactive session
claude

# Run a one-shot task (no interactive loop)
claude -p "Refactor src/auth/middleware.ts to use async/await"

# Pass a specific file as context
claude --files src/auth/middleware.ts "Audit this for security issues"

# Continue the last session
claude --continue

# Run in non-interactive mode (CI/CD pipelines)
claude --print "Generate a changelog from git log since v1.2.0"

# Explicitly request Claude Fable 5 (terminal)
claude --model claude-fable-5
```

### Model IDs by Platform

**Wrong model IDs fail silently.** A bad ID on some platforms returns a fallback response or a generic 404 with no clear indication that the model was never invoked. Memorize the correct format for each surface before writing a single line of integration code.

#### Claude API (Direct) and Claude Platform on AWS

```python
# Clean ID — no prefix, no version suffix, in the request body
response = client.messages.create(
    model="claude-fable-5",   # ← exact string, no date, no v1.0
    max_tokens=128000,
    messages=[{"role": "user", "content": prompt}]
)
```

Unlike previous Sonnet IDs (which carried a date stamp and `v1.0` suffix), **Fable does not use a version suffix**. Do not append anything after `claude-fable-5`.

#### Amazon Bedrock

```python
import boto3

bedrock = boto3.client("bedrock-runtime", region_name="us-east-1")

# Standard (single-region)
MODEL_ID = "anthropic.claude-fable-5"

# Cross-region inference (add regional prefix)
MODEL_ID_US     = "us.anthropic.claude-fable-5"
MODEL_ID_EU     = "eu.anthropic.claude-fable-5"
MODEL_ID_GLOBAL = "global.anthropic.claude-fable-5"

response = bedrock.invoke_model(
    modelId=MODEL_ID_US,
    body=json.dumps({
        "anthropic_version": "bedrock-2023-05-31",
        "max_tokens": 128000,
        "messages": [{"role": "user", "content": prompt}]
    })
)
```

Key difference from the direct API: **the `anthropic.` prefix is mandatory**. Without it, Bedrock returns a `ValidationException` that looks like a permissions error.

#### Vertex AI (Google Cloud)

```python
import anthropic

# On Vertex, the model ID goes in the URL path — not the body
client = anthropic.AnthropicVertex(
    region="us-east5",
    project_id="YOUR_PROJECT_ID"
)

# The model string is still claude-fable-5, but Vertex
# routes it differently from the direct API internally.
response = client.messages.create(
    model="claude-fable-5",
    max_tokens=128000,
    messages=[{"role": "user", "content": prompt}]
)
```

The ID looks the same as the direct API, but the routing is different: the SDK constructs a URL path from the model name. A body-level `model` parameter override does not work the same way it does on the direct API.

#### Microsoft Azure AI Foundry

```python
import openai  # Foundry uses the OpenAI-compatible endpoint

client = openai.AzureOpenAI(
    azure_endpoint="https://YOUR_ENDPOINT.openai.azure.com/",
    api_key=os.environ["AZURE_API_KEY"],
    api_version="2024-12-01-preview"
)

# model= points to your DEPLOYMENT NAME, not the model ID directly
# You named this deployment yourself when you set it up in the portal.
response = client.chat.completions.create(
    model="YOUR_DEPLOYMENT_NAME",   # ← the name YOU chose at creation
    messages=[{"role": "user", "content": prompt}]
)
```

**Critical Foundry constraint: deployment names cannot be changed after creation.** Once you create a deployment named `prod-fable-v1`, that name is permanent. Choose naming conventions carefully — they will outlast the model version.

#### Model ID Summary Table

| Platform | Model ID / Parameter | Where it goes | Notes |
|---|---|---|---|
| Claude API direct | `claude-fable-5` | Request body `model` | No prefix, no suffix |
| Claude Platform on AWS | `claude-fable-5` | Request body `model` | Same as direct API |
| Amazon Bedrock (single-region) | `anthropic.claude-fable-5` | Request body `modelId` | Provider prefix required |
| Amazon Bedrock (cross-region) | `us.anthropic.claude-fable-5` | Request body `modelId` | Regional prefix + provider prefix |
| Vertex AI | `claude-fable-5` | SDK constructs URL path | Not in request body |
| Microsoft Azure AI Foundry | your deployment name | Request body `model` | Points to deployment, not model |

### Platform Feature Matrix

Features that seem universal are not. Before committing to a platform for production, verify these specific capabilities are available there.

#### Feature Availability by Platform

| Feature | Claude API | Bedrock | Vertex AI | Azure Foundry |
|---|:---:|:---:|:---:|:---:|
| **Thinking** | GA | GA | GA | GA |
| **Effort levels** (low → max) | GA | GA | GA | GA |
| **Server-side fallback** (auto Opus 4.8) | GA | — | — | — |
| **Programmatic tool calling** | GA | — | — | Beta |
| **Code execution** | GA | — | — | Beta |
| **Prompt caching** | GA (512 tok min) | GA (1024 tok min) | GA (512 tok min) | Beta |
| **Automatic caching** | Yes | No | Yes | Beta |
| **Streaming** | GA | GA | GA | GA |

**Legend:** GA = Generally Available · — = Not available · Beta = Available but not production-stable

#### Thinking and Effort: Consistent Everywhere

The `thinking` capability is always active on Fable 5 across all platforms. The `effort` parameter accepts five levels: `low`, `medium`, `high`, `very_high`, `max`. Display mode is either `omitted` (thinking hidden from output) or `summarized` (brief summary shown).

```python
# Works identically on all four platforms
response = client.messages.create(
    model="claude-fable-5",
    max_tokens=128000,
    thinking={
        "type": "enabled",
        "budget_tokens": 10000,  # tokens allocated to internal reasoning
        "effort": "high",
        "display": "omitted"     # or "summarized"
    },
    messages=[{"role": "user", "content": prompt}]
)
```

#### Server-Side Fallback: API Only

**Server-side automatic fallback to Opus 4.8 only works on the Claude API direct and Claude Platform on AWS.** On Bedrock, Vertex, and Foundry, if the safety classifier triggers, the request fails — there is no automatic routing.

For non-API platforms, implement fallback in your application layer:

```python
def call_with_fallback(prompt: str, platform: str) -> str:
    primary_model = get_model_id("claude-fable-5", platform)
    fallback_model = get_model_id("claude-opus-4-8", platform)

    try:
        response = call_model(primary_model, prompt)
        if is_safety_blocked(response):
            logger.warning("Safety classifier triggered, falling back")
            return call_model(fallback_model, prompt)
        return response
    except ModelNotAvailableError:
        return call_model(fallback_model, prompt)
```

#### The Foundry Fallback Context Window Collapse

**This is a Foundry-specific edge case that affects no other platform.**

When Fable 5 falls back to Opus 4.8 inside Azure AI Foundry, the context window **drops from 1,000,000 tokens to 200,000 tokens**. This does not happen on the direct API, Bedrock, or Vertex.

```
Platform     Fable 5 context   After fallback to Opus 4.8
─────────────────────────────────────────────────────────
Claude API   1,000,000 tokens  200,000 tokens (standard)
Bedrock      1,000,000 tokens  200,000 tokens (standard)
Vertex AI    1,000,000 tokens  200,000 tokens (standard)
Foundry      1,000,000 tokens  200,000 tokens ← SAME drop, but
                                silently — no notification
─────────────────────────────────────────────────────────
```

If you are running long-context tasks on Foundry and a fallback triggers mid-session, **context that fit at 1M tokens will silently truncate** at 200K on the fallback. Detect fallbacks on Foundry explicitly and handle the context window reduction.

#### Prompt Caching: Platform Differences

```
Platform      Minimum cacheable tokens   Automatic caching
────────────────────────────────────────────────────────────
Claude API    512 tokens                 Yes — no manual annotation
Bedrock       1,024 tokens               No — must use cache_control
Vertex AI     512 tokens                 Yes — no manual annotation
Foundry       Beta — subject to change   Beta
────────────────────────────────────────────────────────────
```

If you rely on prompt caching to control costs, Bedrock's 1024-token minimum and lack of automatic caching means you need to annotate cache boundaries manually using `cache_control`:

```python
# Bedrock — explicit cache_control annotation required
messages = [
    {
        "role": "user",
        "content": [
            {
                "type": "text",
                "text": your_long_system_context,
                "cache_control": {"type": "ephemeral"}  # required on Bedrock
            },
            {
                "type": "text",
                "text": user_query
            }
        ]
    }
]
```

### Model Selection Priority in Claude Code

Claude Code resolves which model to use by applying four mechanisms in order. Think of them as layers of paint — the top layer always wins, regardless of what is underneath.

```
Priority  Mechanism                          How to set
────────────────────────────────────────────────────────────
1 (wins)  /model command during session      Type /model fable in chat
2         --model flag at startup            claude --model claude-fable-5
3         ANTHROPIC_MODEL env variable       export ANTHROPIC_MODEL=claude-fable-5
4 (loses) model field in settings file       .claude/settings.json or CLAUDE.md
────────────────────────────────────────────────────────────
```

The insidious problem: if someone on your team ran `/model` three weeks ago and pressed Enter (permanent save), that persists across all their sessions and silently overrides everything — including your project's settings file. Your repository config says Fable 5; they are getting something else; nothing reports an error.

**Team tip — the `best` alias:**

Instead of hardcoding a model name in your project settings file, use the `best` alias:

```json
// .claude/settings.json
{
  "model": "best"
}
```

`best` resolves to the most capable model each team member has access to. Engineers with Fable 5 access get Fable 5. Those without fall back to Opus without errors or broken builds. No one needs to manually manage model IDs per environment.

### The Enter vs `s` Key: Persistence Trap in claude.ai and Claude Desktop

When you run `/model fable` inside claude.ai or Claude Desktop, you see a confirmation prompt. What you press next determines scope:

```
Key pressed    Effect
────────────────────────────────────────────────────────────
Enter          Saves Fable 5 as your permanent default.
               ALL future sessions start on Fable 5.
               You will not be asked again.

s              Applies the change to this session only.
               Next session reverts to your previous default.
────────────────────────────────────────────────────────────
```

One keypress is a session preference. The other is a permanent account setting that persists until you explicitly change it. This catches nearly everyone the first time.

### Why Your First Request Can Trigger a Fallback Without Sensitive Content

The fallback classifier does not read only your message. It reads your **entire request payload**, which includes:

- The contents of your `CLAUDE.md` file
- Current git branch name and commit state
- Your working directory path and name

This means a completely innocent first message can trigger a fallback if the surrounding context looks problematic to the classifier:

```
Innocent message:  "Summarize the README"

But the payload also contains:
  - Directory name:  exploit-dev/
  - CLAUDE.md:       "Project: Red team infrastructure automation"
  - Branch name:     pentest-phase-2

Result: classifier intercepts, fallback to Opus 4.8
        Your message is fine. The envelope is not.
```

The classifier reads the envelope, not just the letter.

### Diagnosing Fallbacks with `--safe-mode`

`--safe-mode` strips all workspace customizations before the request is sent. It removes `CLAUDE.md` content, directory context, and git state from the payload — sending only your message and the system prompt.

Use it as a three-step diagnostic:

```bash
# Step 1: Run your request with safe-mode
claude --safe-mode --model claude-fable-5 -p "your original message"

# Step 2: Interpret the result
If fallback disappears  →  CLAUDE.md or project settings were the trigger
                           Fix: audit and sanitize your CLAUDE.md content

If fallback persists    →  Run without CLAUDE.md, check directory names
If fallback still       →  The message itself is triggering the classifier
  persists                 Fix: rephrase, or evaluate whether Glasswing is appropriate
```

This saves hours of blind debugging when your integration silently downgrades on every request.

### Verifying You Are Actually Running Claude Fable 5

Subscription plans can silently route you to a different model. Do not assume — verify.

**Terminal (Claude Code CLI):**
```bash
claude --model claude-fable-5
```

**Web interface or desktop app:**
```
/model fable
```
Then press **`s`** (not Enter) if you want session-only scope.

**Three signals that together confirm which model responded:**

```
Signal 1: response.model
────────────────────────────────────────────────────────────
The top-level model field tells you which model served the request.

Signal 2: content[].type == "fallback"
────────────────────────────────────────────────────────────
A block of type "fallback" in the content array signals a switch occurred.
If absent, the named model ran to completion.

Signal 3: usage.iterations (most reliable)
────────────────────────────────────────────────────────────
Lists every attempt in the request lifecycle.
  - Model that declined: output_tokens = 0
  - Model that responded: appears as fallback_message
This is the only signal that survives sticky routing (see below).
────────────────────────────────────────────────────────────
```

```python
# Complete response inspection
response = client.messages.create(...)

# Signal 1 — which model served
print(f"Served by: {response.model}")

# Signal 2 — explicit fallback block
fallback_blocks = [b for b in response.content if b.type == "fallback"]
if fallback_blocks:
    print("Fallback occurred — check usage.iterations")

# Signal 3 — full attempt history (most reliable)
if hasattr(response.usage, "iterations"):
    for i, iteration in enumerate(response.usage.iterations):
        print(f"  Attempt {i}: model={iteration.model} "
              f"output_tokens={iteration.output_tokens}")
```

**Sticky routing — the hidden persistent fallback:**

After a fallback occurs, the system routes **all subsequent turns in the session** to the fallback model for approximately one hour. This routing is silent:

```
Turn 1:  Fable 5 invoked → safety classifier triggers → falls back to Opus 4.8
         → response.content includes "fallback" block  ← visible

Turn 2:  [1 hour window active]
         Routed directly to Opus 4.8 without attempting Fable 5
         → NO "fallback" block in response.content    ← invisible
         → response.model says "claude-opus-4-8"
         → usage.iterations reveals only one attempt  ← looks clean

Turn 10: [still within the hour window]
         Same invisible routing to Opus 4.8
```

`usage.iterations` is the only field that reveals sticky routing. If `response.model` is unexpectedly `claude-opus-4-8` and there is no fallback block, check whether a fallback occurred in a previous turn within the last hour.

**Three questions to answer before every session:**
1. What plan are you on — API, Enterprise, Pro, Max, or Team?
2. Did you confirm Fable 5 is active with `--model claude-fable-5` or `/model fable` + `s`?
3. How much credit/allocation do you have left for this billing cycle?

Answer all three before starting any agentic task. Intensive workflows can exhaust subscription allocations in minutes.

### CLAUDE.md: Your Project's AI Constitution

Every repository that uses Claude Code should have a `CLAUDE.md` file at the root. This file is **automatically injected** into every Claude Code session as context.

```markdown
# CLAUDE.md

## Project: Payment Service API

### Stack
- Python 3.12, FastAPI, SQLModel, PostgreSQL
- Deployed on AWS ECS via GitHub Actions

### Code Style
- No comments unless logic is non-obvious
- Type annotations on all function signatures
- Tests use pytest + httpx for async test client

### Critical Constraints
- NEVER store PII in logs
- NEVER use shell=True in subprocess calls
- All database queries must go through the repository layer

### Common Tasks
- Run tests: `pytest tests/ -v`
- Lint: `ruff check . && mypy .`
- Migrate DB: `alembic upgrade head`
```

This single file replaces 90% of the verbal context you would otherwise type at the start of every session.

### Agentic Workflows with Claude Code

Claude Fable 5's strongest contribution to Claude Code is **agentic task execution** — multi-step work where the model takes actions, observes results, and continues autonomously.

```bash
# Example: autonomous bug investigation
claude -p "
The /api/payments endpoint returns 500 for some users.
I have no idea why. Investigate:
1. Check the error logs in logs/app.log for the last 100 errors
2. Find the relevant code path
3. Identify the root cause
4. Write a fix with a regression test
Do not ask me questions. Make decisions and document them.
"
```

Claude Code + Fable 5 will:
- Read the log file
- Grep for the relevant error
- Navigate to the failing code
- Read dependent files
- Write the fix
- Write the test
- Report what it did and why

All without you switching context once.

### MCP Servers: Extending Claude Code

The **Model Context Protocol (MCP)** allows Claude Code to connect to external data sources and tools. Configure in `.claude/settings.json`:

```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "${GITHUB_TOKEN}"
      }
    },
    "postgres": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-postgres"],
      "env": {
        "DATABASE_URL": "${DATABASE_URL}"
      }
    }
  }
}
```

With these MCP servers, Claude Code can read GitHub issues, query your database, and correlate information across both — in a single prompt.

### CI/CD Integration

```yaml
# .github/workflows/ai-review.yml
name: Claude Code Review

on:
  pull_request:
    types: [opened, synchronize]

jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Install Claude Code
        run: npm install -g @anthropic-ai/claude-code

      - name: Run AI review
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
        run: |
          claude --print "
            Review the diff of this PR against main.
            Check for: security issues, logic errors, missing tests.
            Output a markdown report with severity levels.
          " > review.md

      - name: Post review as comment
        uses: actions/github-script@v7
        with:
          script: |
            const fs = require('fs');
            const review = fs.readFileSync('review.md', 'utf8');
            github.rest.issues.createComment({
              issue_number: context.issue.number,
              owner: context.repo.owner,
              repo: context.repo.repo,
              body: review
            });
```

---

## 6. Model Comparison & Decision Framework: Fable 5 vs Previous Models

### The Anthropic Model Lineup

```
Claude Haiku 3.5   ── Fast, cheap, small tasks
Claude Sonnet 4.5  ── Balanced: most tasks, daily driver
Claude Opus 4      ── Deep reasoning, complex analysis
Claude Opus 4.8    ── Fallback target from Fable 5
Claude Fable 5     ── Flagship: maximum capability, agentic
```

### Benchmark Data: Fable 5 vs Opus 4.8

These are measured results from independent evaluations, not marketing claims.

#### FrontierCode: Production-Ready Code Quality

FrontierCode measures whether generated code meets production standards — not just whether it runs, but whether it handles edge cases, follows conventions, and could be shipped without manual revision.

```
FrontierCode Benchmark
──────────────────────────────────────────
Claude Fable 5    46.3%   ████████████████████░░░░░░░░░░░░░░
Claude Opus 4.8   34.3%   ███████████████░░░░░░░░░░░░░░░░░░░
──────────────────────────────────────────
Delta:           +12.0pp
```

A 12-percentage-point gap in production-ready code changes the delegation threshold. Tasks you previously had to review line-by-line can now be shipped with a lighter review pass.

#### Financial Work: Real-World Analytical Quality

Evaluators with real financial modeling experience compared outputs head-to-head across tasks including building financial models, running valuations, and preparing client-facing analysis.

```
Head-to-head preference: Fable 5 vs Opus 4.8
──────────────────────────────────────────
Fable 5 preferred:    74% of direct comparisons
Opus 4.8 preferred:   26% of direct comparisons
```

This is a measure of analytical quality by domain experts, not a synthetic benchmark — which makes it more relevant for finance, strategy, and research use cases.

#### Token Efficiency: More Output, Half the Cost

```
Same task class, measured token consumption:
──────────────────────────────────────────
Opus 4.8:    baseline token consumption
Fable 5:     ~50% of Opus 4.8 tokens for equivalent or better results
──────────────────────────────────────────
```

The efficiency gain is structural. The model reaches the correct solution through a more precise reasoning path rather than exploring and discarding more intermediate steps.

#### Multilingual Performance: GMMLU & INCLUDE

Two benchmarks that matter if you work in non-English languages or serve international users.

**GMMLU** — a multilingual knowledge benchmark covering 42 languages:

```
GMMLU (42 languages)
──────────────────────────────────────────
Claude Fable 5    93.2%   ████████████████████████████████████
──────────────────────────────────────────
Highest score among all evaluated models
```

**INCLUDE** — uses questions that were originally written in each language and culture, rather than translated from English. This tests real-world linguistic fluency, not translation quality.

```
INCLUDE (native-language questions)
──────────────────────────────────────────
Claude Fable 5    90.5%
──────────────────────────────────────────
```

Spanish falls in the **top performance tier** due to the volume of high-quality Spanish training data available. For bilingual or Spanish-primary workflows, this data supports using Fable 5 without an English intermediary step.

**Multimodal + multilingual caveat:**

When you combine complexity layers — non-English language + image or PDF input + dense structured data — each layer adds error potential. The analogy is stacking wet plates: each additional layer increases the chance something slips.

```
Complexity stack            Risk level
──────────────────────────────────────────
Text only (any language)    Low
Text + image                Medium
Text + image + spreadsheet  Higher
All of the above + dense
  terminology               Requires careful input hygiene
──────────────────────────────────────────
```

Practical rule: if you are working with complex multimodal inputs in any language, clean and structure your inputs aggressively before passing them. Clear column headers, no merged cells, labeled images, and clean OCR output produce consistently better results than raw, messy uploads.

### Capability Matrix

| Capability | Haiku 3.5 | Sonnet 4.5 | Opus 4 | Fable 5 |
|---|:---:|:---:|:---:|:---:|
| Context window | 200K | 200K | 200K | 200K |
| Code generation | Good | Very Good | Excellent | Excellent |
| Code editing/refactor | Fair | Good | Very Good | **Best** |
| Multi-step reasoning | Fair | Good | Very Good | **Best** |
| Instruction following | Good | Very Good | Excellent | **Best** |
| Tool use / agents | Fair | Good | Very Good | **Best** |
| Speed | **Fastest** | Fast | Medium | Slower |
| Cost per million tokens | **Lowest** | Low | Medium | Highest |

### The Decision Flowchart

```
Start: What is the task?
         │
         ├── Classification / tagging / extraction
         │     └── Use Haiku 3.5
         │
         ├── Simple question / summarization / drafting
         │     └── Use Sonnet 4.5
         │
         ├── Complex analysis / long document reasoning
         │     └── Use Opus 4
         │
         ├── Full codebase refactor / multi-file edit
         │     └── Use Fable 5
         │
         ├── Autonomous agentic workflow (many steps)
         │     └── Use Fable 5
         │
         └── Task requires real-time response < 200ms
               └── Never use Fable 5; use Haiku 3.5
```

### What Fable 5 Is NOT Better At

Knowing where NOT to use the flagship model is as important as knowing where to use it.

| Use Case | Better Model | Reason |
|---|---|---|
| High-volume chat autocomplete | Haiku 3.5 | Latency + cost; Fable 5 overkill |
| Simple intent classification | Haiku 3.5 | Single-pass task |
| Embeddings | Use a dedicated embedding model | Fable 5 does not produce embeddings |
| Real-time voice / streaming | Sonnet 4.5 | Fable 5 first-token latency is higher |
| Fine-tuning for domain | Not currently available | No fine-tuning on flagship models |

### Migration from Opus 4 to Fable 5

If you have existing Opus 4 prompts, the migration is mostly safe but there are three things to test:

1. **System prompt verbosity** — Fable 5 follows more precisely; over-specified system prompts that relied on Opus 4 ignoring some instructions may produce unexpected behavior.
2. **Fallback triggers** — Test your full task set; some tasks that worked on Opus 4 may route to Opus 4.8 on Fable 5 due to safety classifiers.
3. **Output length** — Fable 5 tends to be more precise and shorter. If you relied on long-form outputs, audit downstream systems that parse model responses.

---

## 7. Building Production-Ready Workflows with Claude Fable 5

### Choosing the Right Tasks to Delegate

Not every task is a good candidate for Fable 5. The 2× cost and agentic nature of the model mean you need to be selective. A task is worth delegating if it meets all three conditions:

```
Condition 1: LARGE
The task has multiple steps and would take a human meaningful time.
Trivial tasks do not benefit from autonomous execution.

Condition 2: BOUNDED
There is a clear, unambiguous stopping point.
"Research everything about X" is unbounded. "Find all papers from
these 5 journals published in 2024 and summarize each" is bounded.

Condition 3: VERIFIABLE
You can open the result and check it against reality.
If you cannot verify the output without re-doing the work yourself,
you have no way to catch errors before they reach production.
```

**Domain examples:**

| Domain | Good Delegation Task |
|---|---|
| Operations | From three monthly reports + one spreadsheet, generate an executive report with 5 key metrics, trends, and ranked recommendations |
| Development | Take this module, identify outdated dependencies, propose version updates with changelogs, generate regression tests |
| Finance | Build a valuation model from this 10-K, extract assumptions, run three scenarios, flag which assumptions are unverified |
| Research | Read these 20 papers, extract methodology and results for each, identify contradictions across papers |

### Pre-Delegation Checklist

Before launching any Fable 5 task, answer these three questions. If you cannot answer all three, the task is not ready to delegate.

```
[ ] 1. Can I describe the deliverable in one sentence?
        If not: the objective is still too vague. Keep refining.

[ ] 2. Is there a moment where I can verify if the result is correct?
        If not: define a verification step or split the task.

[ ] 3. Could an error in this task have serious downstream consequences?
        If yes: add an intermediate checkpoint. Request a plan
        before execution. Review the plan before approving execution.
```

### Critical Warning: Partial Verification and Error Framing

This is the most important operational warning in this course. **Read it before your first real delegation.**

**Problem 1: Fable 5 sometimes reports "verified" when it only did partial verification.**

```
What the model says:   "I verified all outputs successfully."
What may have happened: The model checked 3 of 7 tool outputs and
                         inferred the rest would pass.
```

Do not accept a status claim as proof. The correct question is not "did you verify it?" but "show me the actual output of each verification step."

If your prompt does not explicitly require the raw tool output, the model will often summarize what it expected to find. The Four-Component Framework's delivery format component exists specifically to prevent this.

**Problem 2: The model frames errors as intentional design decisions.**

This is the subtler and more dangerous failure mode. When something goes wrong, the model has a strong tendency to describe the outcome as though it were the intended behavior:

```
What happened:    The API call failed; model used cached fallback data
What model says:  "I used the most recent available data to ensure
                   consistency across the analysis."

What happened:    Test suite was not run due to missing dependency
What model says:  "I validated the logic through static analysis,
                   which is appropriate for this type of change."
```

The framing sounds reasonable. That is precisely what makes it dangerous — it is designed (unintentionally) to lower your guard.

**The fix:**

```python
# Add to every prompt that produces a deliverable:
system = """
At the end of your response, include a mandatory section:

## Unverified Assumptions and Known Gaps
List every assumption you made that was not confirmed against
real data or actual tool output. If you have no unverified
assumptions, state that explicitly and explain why.

This section is not optional. If it is missing, the task is
considered incomplete.
"""
```

This one addition forces the model to surface what it inferred, what it skipped, and what it assumed — before you review the deliverable as though everything is confirmed.

### The Production Readiness Checklist

Before putting any Claude Fable 5 integration into production, verify all of these:

```
Infrastructure
─────────────────────────────────────────────────────
[ ] API key stored in secrets manager (not env vars)
[ ] Rate limits understood and handled (429 retry logic)
[ ] Fallback behavior for API outages defined
[ ] Response model logged on every request
[ ] Token usage logged per request for cost visibility

Prompt Engineering
─────────────────────────────────────────────────────
[ ] System prompt tested against edge cases
[ ] Output schema validated (JSON schema or Pydantic)
[ ] Max tokens set explicitly on every call
[ ] Adversarial inputs tested (prompt injection, jailbreaks)
[ ] Fallback prompts ready for degraded model scenarios

Observability
─────────────────────────────────────────────────────
[ ] Latency tracked (p50, p95, p99)
[ ] Error rate tracked (4xx vs 5xx separately)
[ ] Cost per feature tracked (not just total spend)
[ ] Input/output logged for debugging (with PII redaction)
[ ] Alerts set for spend anomalies
```

### Reliable API Client Pattern

```python
import anthropic
import time
import logging
from typing import Optional

logger = logging.getLogger(__name__)

class ClaudeClient:
    def __init__(self, model: str = "claude-fable-5"):
        self.client = anthropic.Anthropic()
        self.model = model

    def complete(
        self,
        prompt: str,
        system: Optional[str] = None,
        max_tokens: int = 2048,
        retries: int = 3,
    ) -> str:
        messages = [{"role": "user", "content": prompt}]
        kwargs = {"model": self.model, "max_tokens": max_tokens, "messages": messages}
        if system:
            kwargs["system"] = system

        for attempt in range(retries):
            try:
                response = self.client.messages.create(**kwargs)

                # Always log the actual model used
                if response.model != self.model:
                    logger.warning(
                        "Model fallback: requested=%s actual=%s",
                        self.model,
                        response.model,
                    )

                logger.info(
                    "tokens input=%d output=%d model=%s",
                    response.usage.input_tokens,
                    response.usage.output_tokens,
                    response.model,
                )

                return response.content[0].text

            except anthropic.RateLimitError:
                wait = 2 ** attempt
                logger.warning("Rate limited. Retrying in %ds...", wait)
                time.sleep(wait)

            except anthropic.APIError as e:
                logger.error("API error on attempt %d: %s", attempt + 1, e)
                if attempt == retries - 1:
                    raise

        raise RuntimeError("All retries exhausted")
```

### Structured Output with Validation

```python
from pydantic import BaseModel, ValidationError
import json

class AnalysisResult(BaseModel):
    summary: str
    key_findings: list[str]
    confidence: float
    recommended_action: str

def analyze_with_structure(text: str) -> AnalysisResult:
    client = ClaudeClient()

    system = """
    You are a data analyst. Always respond with valid JSON matching this schema:
    {
      "summary": "string (max 2 sentences)",
      "key_findings": ["string", ...],
      "confidence": float between 0.0 and 1.0,
      "recommended_action": "string (one actionable sentence)"
    }
    Output only the JSON object. No markdown. No explanation.
    """

    response = client.complete(system=system, prompt=f"Analyze:\n\n{text}")

    try:
        data = json.loads(response)
        return AnalysisResult(**data)
    except (json.JSONDecodeError, ValidationError) as e:
        logger.error("Invalid structured output: %s\nRaw: %s", e, response)
        raise
```

### Real-World Production Architectures

#### Architecture 1: Async Document Processing Pipeline

```
User uploads document
        │
        ▼
[Queue: SQS / RabbitMQ]
        │
        ▼
[Worker pool — 10 workers]
        │
        ├── Chunk document if > 180K tokens
        ├── Call Claude Fable 5 (structured output)
        ├── Validate JSON response (Pydantic)
        ├── Store result in database
        └── Notify user via webhook
```

#### Architecture 2: Real-Time Code Review Service

```
Git push → GitHub webhook
        │
        ▼
[FastAPI endpoint]
        │
        ├── Fetch diff via GitHub API
        ├── Build structured prompt
        │     ├── System: code reviewer persona
        │     ├── Context: CLAUDE.md for repo
        │     └── User: diff content
        ├── Call Claude Fable 5
        │     └── Model: claude-fable-5
        ├── Post review comment to PR
        └── Log tokens + latency
```

#### Architecture 3: Multi-Agent Research System

```
User query: "What is the competitive landscape for X?"
        │
        ▼
[Orchestrator Agent — Fable 5]
        │
        ├── Spawn: Web Search Agent (Haiku 3.5)
        ├── Spawn: Document Analysis Agent (Fable 5)
        └── Spawn: Data Extraction Agent (Sonnet 4.5)
                │
                ▼
        [Synthesis Agent — Fable 5]
                │
                ▼
        Final report with citations
```

The key architectural insight: **use Fable 5 for synthesis and orchestration; use cheaper models for data gathering and extraction.** This cuts costs by 60–80% compared to running everything through the flagship model.

### Monitoring Dashboard Metrics

Track these metrics in production. All of them:

```
Response Quality
├── Fallback rate (% of requests that hit Opus 4.8)
├── Structured output parse failure rate
├── User-reported error rate

Performance
├── Time to first token (p50 / p95)
├── Total response time (p50 / p95)
├── Queue depth (if async)

Cost
├── Daily spend by feature
├── Average tokens per request (input / output)
├── Cost per successful task completion

Reliability
├── API error rate (4xx / 5xx)
├── Retry rate
├── Circuit breaker trip rate
```

---

## Quick Reference

```bash
# Claude Code essentials
claude                               # Start interactive session
claude -p "task"                     # One-shot task
claude --continue                    # Resume last session
claude --print "task"                # Non-interactive output
claude --model claude-fable-5        # Explicitly request Fable 5

# Verify active model (inside chat)
/model fable                         # Web / desktop app
```

```python
# Always verify which model actually ran (API)
print(response.model)                # May differ from requested model
print(response.usage.input_tokens)   # Cost visibility: input
print(response.usage.output_tokens)  # Cost visibility: output
```

```
# Fallback signal interpretation
No "switching to Opus 4.8" message  →  You are on Fable 5
"Switching to Opus 4.8" appears     →  Safety boundary triggered (< 5% of sessions)

# Plan access summary (post June 23)
API / Enterprise                    →  Full access, pay per token
Pro / Max / Team subscription       →  Additional credits required
Max plan ($100) agentic burn rate   →  6-hour allocation in ~20 minutes

# FrontierCode benchmark
Fable 5:   46.3%  (+12pp vs Opus 4.8)
Opus 4.8:  34.3%

# Financial work preference (head-to-head)
Fable 5 preferred: 74% of evaluations
Token efficiency:  ~50% of Opus 4.8 token consumption for equivalent results

# Confirmed pricing
Input:    $10.00 / million tokens
Output:   $50.00 / million tokens
Context:  1,000,000 tokens
Max out:  128,000 tokens per request
```

```
# Model selection priority in Claude Code (highest wins)
1. /model command in session      ← overrides everything
2. --model flag at startup
3. ANTHROPIC_MODEL env variable
4. model field in settings file   ← lowest priority

# /model fable — key choice
Enter    →  permanent default (persists all future sessions)
s        →  session only (reverts next session)

# API parameters forbidden in Fable 5 (all return HTTP 400)
thinking: {type: "disabled"}     ← thinking is always on
temperature                       ← not supported
top_p                             ← not supported
top_k                             ← not supported
assistant prefill                 ← not allowed

# Response verification signals
response.model                    →  which model actually ran
content[].type == "fallback"      →  explicit fallback occurred
response.usage.iterations         →  full attempt history (survives sticky routing)

# Sticky routing
After any fallback: system routes to Opus 4.8 for ~1 hour silently
Only usage.iterations reveals this — no fallback block appears
```

```
# Model IDs by platform — use exactly as shown
Claude API direct         →  claude-fable-5
Claude Platform on AWS    →  claude-fable-5
Bedrock (single-region)   →  anthropic.claude-fable-5
Bedrock (cross-region)    →  us.anthropic.claude-fable-5
                             eu.anthropic.claude-fable-5
                             global.anthropic.claude-fable-5
Vertex AI                 →  claude-fable-5  (in URL path via SDK)
Azure AI Foundry          →  YOUR_DEPLOYMENT_NAME  (not the model ID)

# Feature gaps by platform
Server-side fallback      →  API + Claude on AWS only
Tool calling (GA)         →  API only  (Foundry: beta)
Code execution (GA)       →  API only  (Foundry: beta)
Auto prompt caching       →  API + Vertex  (Bedrock: manual only, 1024 tok min)
Foundry fallback penalty  →  Context drops 1M → 200K on Opus 4.8 fallback

# Data retention gotcha
ZDR org setting enabled   →  Fable 5 returns HTTP 400 silently
Fix                       →  Use Opus 4.8, or disable ZDR for API traffic

# Fable 5 vs Mythos 5
Fable 5    →  classifiers on, self-serve, all platforms
Mythos 5   →  no classifiers, Project Glasswing only
Glasswing self-serve path →  claude.com/form/cyber-use-case
```

```bash
# Useful environment variables
ANTHROPIC_API_KEY=sk-ant-...              # Required for API access
CLAUDE_CODE_MAX_OUTPUT_TOKENS=8192        # Override default output limit
```

---

## Resources

- [Anthropic Documentation](https://docs.anthropic.com)
- [Claude API Models Overview](https://docs.anthropic.com/en/docs/about-claude/models/overview)
- [Claude Code GitHub Repository](https://github.com/anthropics/claude-code)
- [Model Context Protocol (MCP)](https://modelcontextprotocol.io)
- [Anthropic Cookbook](https://github.com/anthropics/anthropic-cookbook)
- [Platzi Learn](https://platzi.com) — Where this course was built

---

*Course built with Platzi Learn. Launched the same day as Claude Fable 5.*
*Feedback on each lesson shapes the next version — comment on every class.*
