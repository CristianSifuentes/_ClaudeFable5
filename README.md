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

### Prompting Anti-Patterns to Avoid

| Anti-Pattern | Why It Fails | Fix |
|---|---|---|
| "Be concise" at the end | Model already drafted the response | Put constraints at the top |
| Vague role: "You are a helpful assistant" | No signal for the model to calibrate | Use a specific, expert role |
| Over-praising in prompts | Correlated with lower-quality outputs | Be neutral and professional |
| "Do your best" | Zero information content | Specify the success criterion |
| Mixing multiple tasks in one prompt | Attention splits across tasks | One task per prompt |

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

### Token Pricing Model

Anthropic prices all Claude models on a per-token basis, split between input and output:

```
Input tokens:  text you send in (prompt + context + tools)
Output tokens: text the model generates (response + tool calls)

Output tokens are priced 3–5× higher than input tokens.
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

### The Expensive Mistakes (and How to Avoid Them)

| Mistake | Cost Impact | Fix |
|---|---|---|
| Passing full codebase on every turn | High — input tokens × turns | Cache static context; only pass diffs |
| Streaming without token counting | No visibility into spend | Log token usage per request |
| Using Fable 5 for simple classification | Overkill — pay flagship prices for haiku-level tasks | Route simple tasks to Haiku 3.5 |
| Retrying on hallucination instead of constraining | Doubles cost for the same task | Add output validation before retry |
| Ignoring context window limits | Truncation = invisible data loss | Always track token count in context |

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
```

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
Claude Fable 5     ── Flagship: maximum capability
```

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
claude                          # Start interactive session
claude -p "task"                # One-shot task
claude --continue               # Resume last session
claude --print "task"           # Non-interactive output

# Useful environment variables
ANTHROPIC_API_KEY=sk-ant-...    # Required for API access
CLAUDE_CODE_MAX_OUTPUT_TOKENS=8192   # Override default output limit

# Check which model ran (Python)
print(response.model)           # May differ from what you requested
print(response.usage)           # Always log this
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
