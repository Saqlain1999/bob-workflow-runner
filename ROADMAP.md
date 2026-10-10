# Roadmap

The current design preview is published. Later milestones describe proposed work, not available executable features or delivery dates.

## 0. Design preview — current

The architecture, transitions, example contract, source notes, and evaluation criteria are published. Resolve disagreements about scope and evidence before introducing executable behavior. No runtime evaluation has been performed.

## 1. Offline contract and state core

Implement strict input validation, canonical contract digests, a single-writer state store, transition guards, and atomic recovery records. Reject placeholders and unsupported schema versions. Test illegal transitions, modified state records, interruption, and stale evidence without Bob or a network connection.

Exit condition: local tests demonstrate that a task cannot become `review_ready` through a model-authored status field or stale verification record.

## 2. Local command supervisor

Add reviewed command profiles, explicit argument vectors, time and output budgets, cancellation, process containment, and snapshot-based validation. Begin with one documented operating system. Reject unsupported containment requirements rather than imply portability.

Exit condition: the local failure fixtures in the evaluation plan pass, including descendant cleanup, hung pipes, output floods, and concurrent workspace changes.

## 3. Version-qualified Bob adapter

Specify a narrow adapter and a test protocol before making any live calls. A volunteer must explicitly authorize their own credentials, spending limit, isolated test workspace, and network use. No contribution should require sharing a key with this project.

Exit condition: published, redacted evidence identifies the exact Bob version and tested options, session termination behavior, observed cost accounting, applicable approval semantics, and remaining gaps. Unsupported or changed client behavior blocks launch.

## 4. Evaluated alpha

Run repeated, small tasks with and without the controller, using the companion evaluation definitions. Report failures and overhead alongside success, and publish no aggregate improvement claim without a reproducible method and results.

Only after these gates should this repository offer installation instructions, supported-platform claims, or a stable contract schema. Hooks, parallel execution, multiple agents, automatic publishing, and additional client adapters remain outside the initial scope.
