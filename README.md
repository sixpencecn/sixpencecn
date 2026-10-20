<div align="center">
  <img src="https://cdn.jsdelivr.net/gh/sixpencecn/sixpencecn@main/assets/banner.svg" alt="sixpencecn — AI Engineer, LLM applications and agent systems" width="100%" />
</div>

<br/>

<div align="center">

  <a href="https://github.com/sixpencecn"><img alt="GitHub" src="https://img.shields.io/badge/GitHub-sixpencecn-181717?style=for-the-badge&logo=github&logoColor=white" /></a>
  <img alt="Focus" src="https://img.shields.io/badge/FOCUS-LLM%20APPLICATIONS-2F81F7?style=for-the-badge" />
  <img alt="Profile views" src="https://komarev.com/ghpvc/?username=sixpencecn&style=for-the-badge&color=2F81F7&label=VIEWS" />

</div>

## Hi, I'm sixpencecn

I build **LLM-powered applications** — agent orchestration, retrieval pipelines, and the
unglamorous tooling that keeps them dependable once real users show up.

I care more about evaluation, failure modes and cost per answer than about demo-day magic.

```python
@pipeline
def answer(question: str) -> str:
    context = retrieve(question, k=8)        # grounding beats guessing
    draft   = synthesize(question, context)
    return verify(draft) or escalate(question)
```

## Focus

- **Agent systems** — tool use, planning loops, and the guardrails that keep them bounded
- **Retrieval that holds up** — chunking, hybrid search, and measuring whether the retrieved context was actually right
- **Evaluation & observability** — offline suites, trace review, and knowing *why* an answer failed

## Featured

<table>
  <tr>
    <td width="47%" valign="middle">
      <a href="https://sixpencecn.github.io/neon-snake/">
        <img src="https://cdn.jsdelivr.net/gh/sixpencecn/sixpencecn@main/assets/neon-snake.png" alt="Neon Snake — gameplay" width="100%" />
      </a>
    </td>
    <td width="53%" valign="top">
      <h3><a href="https://sixpencecn.github.io/neon-snake/">Neon Snake</a></h3>
      <p>
        A dependency-free canvas Snake, built for feel rather than for a framework:
        interpolated motion on a fixed-step simulation, a two-deep input buffer so fast
        turns are never dropped, runtime-synthesised audio, and touch controls.
      </p>
      <p>
        Three files, no build step, and 19 assertions that actually run.
      </p>
      <p>
        <a href="https://sixpencecn.github.io/neon-snake/"><img alt="Play Neon Snake" src="https://img.shields.io/badge/PLAY-2F81F7?style=for-the-badge&logo=html5&logoColor=white" /></a>
        <a href="https://github.com/sixpencecn/neon-snake"><img alt="Source" src="https://img.shields.io/badge/SOURCE-181717?style=for-the-badge&logo=github&logoColor=white" /></a>
      </p>
    </td>
  </tr>
</table>

### Product specification

The same project ships with a full PRD rather than a feature list — problem framing with
evidence, eight explicit non-goals, P0 requirements written as `Given/When/Then`, a
three-layer metric tree with counter-metrics, RICE scoring, a trade-off matrix where every
option has a decisive reason, and a rollout plan that states its rollback SLA.

<a href="https://github.com/sixpencecn/neon-snake/blob/main/docs/PRD.md"><img alt="Read the PRD" src="https://img.shields.io/badge/READ%20THE%20PRD-2F81F7?style=for-the-badge&logo=readthedocs&logoColor=white" /></a>
<img alt="12 sections" src="https://img.shields.io/badge/12%20SECTIONS-181717?style=for-the-badge" />
<img alt="6 ADRs" src="https://img.shields.io/badge/6%20ADRs-181717?style=for-the-badge" />

## Toolkit

<p align="left">
  <img src="https://skillicons.dev/icons?i=python,fastapi,pytorch,docker,postgres,redis,linux,git,typescript,react&theme=dark&perline=10" alt="Python, FastAPI, PyTorch, Docker, PostgreSQL, Redis, Linux, Git, TypeScript, React" />
</p>

## Now

- Shipping a small agent runtime — tool calling, bounded loops, trace logging
- Writing an evaluation harness I can actually trust before adding more features

## Connect

<div align="center">

  <a href="https://github.com/sixpencecn"><img alt="GitHub" src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" /></a>
  <a href="https://github.com/sixpencecn/sixpencecn/issues/new"><img alt="Open an issue" src="https://img.shields.io/badge/Open%20an%20issue-2F81F7?style=for-the-badge&logo=github&logoColor=white" /></a>

</div>

<br/>

<p align="center"><sub>Always measuring. Rarely guessing.</sub></p>
