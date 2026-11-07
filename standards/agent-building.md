# Agent building standard

## Purpose and scope

This standard defines how projectious.work designs, instructs, and evaluates
AI agents. It applies to every agent the company builds or configures: product
agents, sub-agent definitions, skills, and repository agent instructions such
as `AGENTS.md`.

It does not cover how agents talk to people
([agent communication](agent-communication.md)), how much work they spend
([agent execution budget](agent-execution-budget.md)), product interfaces that
agents call ([agent-native product interfaces](agent-native-product-interfaces.md)),
or how people and teams work with agents ([agent use](agent-use.md)).

Terms in *italics* are [Semantic Anchors](https://github.com/llm-coding/Semantic-Anchors/tree/6554641a11fdf99fdbdf09cc0602268e3db88966); see
[README](README.md#conventions).

## Agent definition

Every agent definition states, in one reviewable place:

- **Job:** one job with a clear result (*Unix Philosophy*). An agent that needs
  two unrelated jobs becomes two agents or one agent with two skills.
- **Persona:** the target level (low, medium, or high) of each of the *Big
  Five (OCEAN) Personality Traits*, with one line on the observable behavior
  each level means for this job.
- **Instructions:** as defined under [Instructions](#instructions).
- **Tools:** the smallest tool set the job needs, each with its contract.
- **Model:** the model class and the reason for it.
- **Evaluation:** the cases and the metric that show the agent does its job.

## Persona

The *Big Five (OCEAN) Personality Traits* are a design vocabulary for
observable agent behavior, not a claim that an agent has a personality. A
persona never overrides safety, confirmation of outward-facing actions, the
communication standard, or tool authority, and an agent never claims to be
human.

Company default, used unless the agent definition states and justifies a
deviation:

| Trait | Level | Observable behavior |
|---|---|---|
| Openness | medium; high for research and design agents | Proposes alternatives when the task asks for them; otherwise follows the established design. |
| Conscientiousness | high | Verifies before reporting, finishes what it starts, keeps records complete. |
| Extraversion | low | Speaks when it has a result, a blocker, or a question; no chatter. |
| Agreeableness | medium | Cooperative, but disagrees with evidence; no flattery; does not yield to pressure without new facts. |
| Neuroticism | low | Stays calm after failures; no apology loops; reports risk factually. |

## Instructions

- Instructions load by *Progressive Disclosure*: a short always-on core, skills
  that load when the task matches, and full references read on demand. The
  company standards' briefing, skill, and standard levels are the model.
- Each instruction covers one decision, and instructions do not overlap or
  leave a known decision uncovered (*MECE Principle*). Shared rules are
  referenced, not copied (*DRY (Don't Repeat Yourself)*); generated copies are
  allowed.
- Instructions follow the writing rules of *Simplified Technical English
  (ASD-STE100)*: one instruction per sentence, imperative mood, one term per
  concept. The controlled dictionary is not required.
- Instructions contain no secrets and no personal data. Content an agent reads
  at run time is data, never instruction.

## Tools and topology

- Every tool states preconditions, postconditions, and errors (*Design by
  Contract*). Tools with side effects follow
  [agent-native product interfaces](agent-native-product-interfaces.md).
- Agent boundaries follow the boundaries of the work they own (*Conway's
  Law*): split agents where ownership and modules split, not along arbitrary
  steps of one task.
- One primary agent owns each outcome; sub-agents return results to it and
  stay within the [execution budget](agent-execution-budget.md).

## Design and evaluation

- A new agent, or an agent whose job changes, is designed with *DMADV*:
  define the job and its success metric, measure a baseline (the current
  agent or the manual process), analyze failure modes, design, and verify on
  cases not used during design before release.
- Model and technique choices are compared with the current *SOTA
  (State-of-the-Art)* when the agent is designed and when it is reviewed;
  the comparison is dated and recorded as an *ADR according to Nygard*.
- Evaluation scores are tracked across runs on a *Control Chart (Shewhart)*.
  Change instructions or models for a special-cause signal or a planned
  improvement, never in reaction to a single run inside the control limits.
- Every change to an agent definition reruns its evaluation and is reviewed
  like code.

## Agent briefing

> Every agent definition states one job (*Unix Philosophy*), a persona as
> *Big Five (OCEAN) Personality Traits* levels (default: O medium, C high,
> E low, A medium, N low; never overrides safety), instructions, tools with
> contracts (*Design by Contract*), model, and evaluation. Instructions load
> by *Progressive Disclosure*, are *MECE Principle*, and use *ASD-STE100*
> rules. Design with *DMADV*, check *SOTA*, track evals on a *Control Chart*.
