# Bob Workflow Runner

**Design preview: specifications and examples only. There is no executable runner, supported installation command, or tested Bob integration in this repository.**

This project explores a small controller for bounded coding tasks delegated to IBM Bob. The goal is to make a workflow's scope, stage transitions, budgets, and verification evidence inspectable. A controller could eventually decide when a task may advance; a prompt alone cannot provide that guarantee.

The central proposed rule is straightforward: a successful agent session and a passing command are separate observations. A task may reach `review_ready` only when the required checks pass against the exact recorded candidate state, the state remains current, and the process and budget records are complete. `review_ready` would mean ready for human review, not approved, merged, or deployed.

## What is available

| Document | Purpose |
| --- | --- |
| [Architecture](docs/architecture.md) | Components, authority boundaries, command supervision, and workspace identity |
| [State transitions](docs/state-transitions.md) | Proposed guards and failure paths |
| [Task contract](docs/task-contract.md) | Meaning and validation requirements of a future contract |
| [Example contract](examples/task.example.json) | Deliberately incomplete template with explicit placeholders |
| [Evaluation plan](docs/evaluation-plan.md) | Observable acceptance criteria and failure fixtures |
| [Roadmap](ROADMAP.md) | Evidence required before implementation or compatibility claims |
| [Source notes](docs/sources.md) | IBM primary references checked on 2026-10-09 |

Start with the architecture, then trace one task through the state table. Review the example contract as a proposal; no application here consumes it.

## Proposed shape

The controller would validate a task contract, capture a baseline, request a bounded plan, run one authorized implementation stage, and independently supervise repository checks. A failed relevant check could permit a bounded repair attempt. A changed candidate would invalidate earlier verification.

The first implementation should support one task and one isolated workspace at a time. Repository commands must come from a reviewed project profile. This avoids treating `npm test`, `pytest`, or another conventional command as a universal definition of correctness.

IBM documents that `bob run` pre-approves tool calls. The proposed adapter must consequently obtain applicable authorization before launching a session and qualify the restrictions it relies on. See the [primary source and capability notes](docs/sources.md); this preview does not change Bob's approval settings.

## Current limits

- No executable controller, parser, state store, supervisor, or Bob adapter is included.
- No evidence of enforcement, compatibility, reliability improvement, or benchmark performance has been collected.
- No API keys, paid model calls, credential setup, global configuration changes, hooks, or external integrations are needed to review this repository.
- The design is not a security sandbox. A future implementation must separately qualify process containment, filesystem isolation, and its supported operating systems.

## Companion projects

- [bob-workflow-kit](https://github.com/Saqlain1999/bob-workflow-kit): instruction and skill starter kit.
- [bob-workflow-evals](https://github.com/Saqlain1999/bob-workflow-evals): evaluation definitions and evidence discipline.
- [awesome-bob-workflows](https://github.com/Saqlain1999/awesome-bob-workflows): curated workflow references.

The runner is optional. These specifications do not make the companion kit enforce a fixed execution pathway.

## Contributing and license

See [CONTRIBUTING.md](CONTRIBUTING.md). Original repository documentation and examples are available under the [MIT license](LICENSE). IBM software, product names, and linked documentation retain their respective rights and terms. This is an independent community project, without a claim of IBM endorsement.
