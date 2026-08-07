## Kyle Disch

**Data engineer in Chicago.** Healthcare data by day — claims, clinical encounters, the
unglamorous reconciliation work. Reproducing recent AI-failure research by night, because the
fastest way to learn whether a claim holds is to try to measure it yourself.

Everything below links to a repo you can clone and run — except the one row marked *(private)*.

---

### AI-reliability research

> I built a repeatable reproduce-and-measure engine and ran it in two lanes — reproductions of
> recent agent-reliability papers, and a model-internals lineage built on an independently
> validated Jacobian lens — pre-registered, judge-free, real confidence intervals, **nulls
> reported as headlines**.

**Start here → [the portfolio index](https://github.com/ksdisch/portfolio)**, which frames all
eight projects as one body of work and states plainly what's unfinished.

**Model internals — the J-lens lineage** (build the instrument → map with it → audit with it):

| | |
|---|---|
| **[dim-stage](https://github.com/ksdisch/dim-stage)** | Is Anthropic's "global workspace" readable in *small* models? I rebuilt their Jacobian lens independently, validated it **bitwise against their reference**, and got a **pre-registered null** across Qwen2.5 0.5B–3B. |
| **[mute-map](https://github.com/ksdisch/mute-map)** | The one effect that survived every control in `dim-stage`: delete a concept's lens direction from the late band and the model **can't say that word** — 0/34 on the diagonal vs 363/374 off it. No paper behind this one, which the card says before you can. |
| **[hush-gauge](https://github.com/ksdisch/hush-gauge)** | Can you tell from the activations that a model is about to leak a secret it was ordered to keep — even on the trials where it never says it? **Complete (M0–M4).** The answer is no: **four pre-committed nulls, zero re-tuned bars** — the probe reads speech, not secrecy. |

**Agent reliability — behavioral reproductions:**

| | |
|---|---|
| **[forge-gap](https://github.com/ksdisch/forge-gap)** | How much does each reliability guardrail actually buy on multi-step tool-calling? 67.5% → 100%, **+32.5pp** [+17.3, +48.0]. The gap is *injected*, and the chart says so. |
| **[decay-pin](https://github.com/ksdisch/decay-pin)** | A safety rule in context is silently abandoned once compaction evicts it — **0/20 → 20/20** violations. Re-pinning the same ~50 tokens restores it to 0/40. |
| **[lossy-wall](https://github.com/ksdisch/lossy-wall)** | A memory note that keeps a wrong conclusion but drops its source is **worse than no memory** — the model re-emits the stale answer instead of abstaining. Cross-checked against the paper author's own harness: AGREE. |
| **[ghost-patch](https://github.com/ksdisch/ghost-patch)** | Do code LLMs knowingly follow a wrong-location repair instruction and compound it? **Two nulls, reported as headlines.** $1.42 against a $5 guard. |
| **[blind-cite](https://github.com/ksdisch/blind-cite)** | A RAG answer can pass every faithfulness and citation check and still attribute the wrong entity's evidence. **The headline is a reversal I caught against myself** — I reported a null at N=20, audited my own sample size, found it was sized for yield rather than power, and a pre-registered extension to N=80 found the failure at both surfaces. The measurement stands; the inference doesn't. |

---

### Tooling

| | |
|---|---|
| **[claude-config](https://github.com/ksdisch/claude-config)** | My version-controlled Claude Code setup — slash commands, skills, subagents, global instructions. |
| **[task-manager-mcp](https://github.com/ksdisch/task-manager-mcp)** | A local MCP server exposing Todoist to Claude. Built it after finding **87 of 102** of my own invocations were raw API calls for queries Zapier couldn't express. Tests are larger than the implementation. |
| **[constellation](https://github.com/ksdisch/constellation)** | Asymmetric two-player co-op: a Phaser platformer on the laptop, React puzzles on your phone, glued by a websocket relay. |
| **[stopwatch](https://github.com/ksdisch/stopwatch)** — [live](https://ksdisch.github.io/stopwatch/) | Offline-first PWA with retroactive start, Firestore sync behind per-user security rules, and a Capacitor iOS build. |

---

### Data engineering

| | |
|---|---|
| **[clinical-data-etl](https://github.com/ksdisch/clinical-data-etl)** | Three heterogeneous healthcare datasets → pandera validation → Postgres → dbt → **three independent star schemas**, orchestrated with Prefect. 56 pytest tests, 98 dbt tests, an SCD2 snapshot, and **10 ADRs** explaining why each design call went the way it did. |
| **personal-health-elt** *(private)* | Apple Health → Postgres → dbt (27 models) → Streamlit. Idempotent loaders, range-joined HR zones, training-load and recovery marts. The apex mart is a **versioned public API** with three downstream consumers, so schema changes move in lockstep. |

---

**Stack** — Python · SQL · dbt · PostgreSQL · Prefect · pandas · Streamlit · pytest · Docker · TypeScript · React

**Reach me** — [LinkedIn](https://linkedin.com/in/ksdisch)
