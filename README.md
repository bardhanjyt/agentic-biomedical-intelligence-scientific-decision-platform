# Agentic Biomedical Intelligence & Scientific Decision Platform

A versioned scientific decision system for mechanistic discovery. It turns heterogeneous biomedical evidence into falsifiable mechanism hypotheses, directionally constrained intervention candidates, validation plans, and an append-only decision record. The unit of value is not generated prose. It is a signed decision whose evidence, transforms, gates, uncertainty, and human authority can be replayed.

**Thesis.** Deterministic scientific spine, agentic side branches. Foundation models may author and challenge. They do not own causal eligibility, direction, safety, approval, or a released snapshot.

**Intended use.** Internal mechanistic discovery and intervention prioritisation. Not a diagnostic device. Not an autonomous prescription. Not a regulatory submission by itself.

| | |
|---|---|
| Architecture | [Principal architecture (PDF)](docs/architecture/Agentic-Biomedical-Intelligence-Scientific-Decision-Platform.pdf) |
| Walkthrough | [Narrated console demo, 4:00, 1600×900](docs/walkthrough/veridia-scientific-decision-walkthrough.mp4) |
| Console | Veridia — the human operating surface in this repository |
| Author | Jyotirmoy Bardhan |

[![Command desk on the released snapshot](docs/images/command.png)](docs/walkthrough/veridia-scientific-decision-walkthrough.mp4)

*Click the image to open the narrated walkthrough.*

## What this repository is

Two artifacts, kept separate on purpose.

1. **The architecture** specifies the production platform: an AWS multi-account scientific landing zone, immutable snapshots, a canonical system of record, governed graph and retrieval projections, a point-in-time feature platform, a model portfolio, and a bounded agent fabric. Pages 1–24 are the end-to-end design. Pages 25–75 are fifty-six decision packets (DE-01 to DE-56), one per irreversible or safety-significant choice.
2. **The console** is a runnable demonstration of the decision loop a scientist actually operates: snapshot alias, candidate queue, hard gates, evidence with a contradiction quota, a bounded graph path, agent manifests, human disposition, a validation package, and an append-only record. Biology in the fixture is illustrative. It is not a therapeutic claim and not a customer program.

This repository does **not** deploy Neptune, OpenSearch, Aurora, SageMaker, Bedrock, or Step Functions. Those are the specified substrate. The console runs against a signed snapshot fixture so the control semantics can be inspected without pretending a model reasoned its way there.

## Decision flow

One released snapshot binds lakehouse inputs, canonical facts, graph and search projections, feature views, model and prompt versions, rule bundles, and evaluation evidence. Compile builds that snapshot. Serve reads the alias. A released snapshot is never mutated in place.

```text
source release
  → harmonise identifiers and context
  → materialise graph + point-in-time features
  → causal eligibility          PASS | FAIL | INDETERMINATE
  → direction                   ACTIVATE | INHIBIT | UNKNOWN
  → monotone rank + calibration (only if eligible and directed)
  → independent review          typed defects, no gate writes
  → deterministic safety        PASS | BLOCK | INDETERMINATE
  → human disposition           advance | hold | shelve
  → validation package          protocol, custody, QC, adjudication
  → scientific decision record  append-only; corrections supersede
```

Hard constraints, enforced before any narrative:

- No model owns regulated or safety-critical state.
- No candidate is ranked before causal eligibility.
- No direction-dependent claim survives `UNKNOWN` polarity.
- Safety is not a rank feature and cannot be overridden by a reviewer.
- No retrieval result is evidence without source identity, admissibility, and temporal applicability.
- No release is valid without replay, rollback, and accountable human approval.
- Partner data does not enter shared training by default.
- A raw review click is not a training label.

Domain errors stay domain states: `EVIDENCE_INSUFFICIENT`, `DIRECTION_UNKNOWN`, `SAFETY_BLOCKED`, `SNAPSHOT_MISMATCH`, `LICENCE_DENIED`, `STALE_FEATURE`, `VALIDATION_QUARANTINED`, `POLICY_DENIED`. They are not collapsed into a generic failure and not talked away by an agent.

## Worked example on the console

Serving alias `SNAP-2026.09.18-R4`, endotype **E-1842** (senescent alveolar epithelial program, pulmonary fibrosis). The endotype is authored drug-blind: the author cannot see intervention tables while writing the taxonomy, and missing evidence is declared rather than filled in.

| Candidate | Causal gate | Direction | Rank | What the console refuses |
|---|---|---|---|---|
| Integrin αvβ6 | PASS on genetic, colocalisation, and functional axes | INHIBIT | 0.86, calibration reported separately (0.62, interval 0.48–0.74) | Awaiting a named human. The click does not train a model. |
| TGFBR1 | PASS, colocalisation indeterminate | INHIBIT | Ranked, but safety is INDETERMINATE | On-target liability and a timed-out dependency fail closed. Reviewer cannot clear it. Permitted recovery is hold. |
| LOXL2 | INDETERMINATE | INHIBIT where evidence exists | Not ranked | A passing functional assay does not outvote a missing genetic axis. Safety does not run to rescue it. |
| PDE4B | PASS | UNKNOWN | Not ranked | Activator and inhibitor precedent conflict. Association is not direction. |

![Candidate desk with gate trace](docs/images/decision.png)

Evidence for αvβ6 keeps the contradicting fibroblast-only assay (**EU-19002**) under a contradiction quota. It is not dropped because a supporting passage scored higher. The passage stays visible and is marked inadmissible as positive support, because that assay has no epithelial source of latent TGF-β.

![Evidence dossier with contradiction retained](docs/images/evidence.png)

## Console surface

| View | What it shows |
|---|---|
| Command | Released snapshot, hash, alias, human queue, hard-gate and wrong-direction sentinels |
| Decisions | Endotype, candidate, causal / direction / rank / review / safety trace, disposition |
| Evidence | Evidence units with source, licence, effective interval, support, and admissibility |
| Graph | Approved path template only. The model may narrate a path. It may not invent an edge. |
| Agents | Capability-bound manifests. Add an agent with authority, tools, route, budgets, and locks |
| Snapshots | Serving alias and prior alias. Rollback is a preview, not an in-place edit |
| Validation | External validation package bound to the snapshot |
| Records | Append-only decision records. A correction supersedes; it does not overwrite |
| Models | Portfolio routes. Agents name capabilities, not model IDs |

The walkthrough follows that order without jumping screens: open αvβ6, compare LOXL2 and PDE4B, step the gates, open the contradiction, traverse the approved graph path, register a contradiction-miner agent, record a human advance, open the validation package, preview rollback, and land on the new decision record.

### Agent manifest

An agent is a bounded task inside a durable workflow, not a principal. Step Functions (in the architecture) owns anything that must survive a deploy, wait for a person, compensate a side effect, or be the authoritative history. The agent assembles admissible context and proposes a typed artifact.

| Capability | Authority | May emit | May not |
|---|---|---|---|
| Disease evidence scout | Read-only | Dossier with applicability and gaps | Write gates or state |
| Endotype author | Generate hypothesis only | Schema-valid, drug-blind proposal | See intervention tables while authoring |
| Causal verifier | Deterministic veto | PASS, FAIL, or INDETERMINATE per axis | Be a language model |
| Mechanism matcher | Deterministic scoring | Rank-ready set with feature lineage | Rank an ineligible pair |
| Direction resolver | Deterministic, abstaining | ACTIVATE, INHIBIT, or UNKNOWN | Guess polarity from association |
| Bounded reviewer | Capped challenge | Typed defects, bounded rank note | Write a gate |
| Safety gate | Non-LLM, non-overridable | PASS, BLOCK, or INDETERMINATE | Be folded into the rank score |
| Evidence clerk | Deterministic | Sealed card and controlled package | Replace records with prose |
| Triage copilot | Draft only | Advance / hold / shelve memorandum | Sign the disposition |

Every invocation carries tenant, snapshot, intended use, context manifest, allowed routes, tool capabilities, and token, step, time, cost, and repair budgets. Cycle detection and a repair cap stop open-ended self-reflection. New agents enter on a shadow route. They do not receive write locks on causal, direction, safety, approval, or snapshot state.

Adding an agent on the console collects the fields the architecture treats as the contract: name, capability class, authority, output contract, intended use, model route, tool allow-list, budgets, and locked writes.

## Reference architecture

Specified substrate. Not what `npm run dev` starts.

| Plane | Implementation | Responsibility |
|---|---|---|
| Scientific data | S3 Object Lock, Apache Iceberg, Glue, Lake Formation, Athena, EMR Serverless | Immutable source and transform history, point-in-time datasets, replay |
| Canonical state | Aurora PostgreSQL, RDS Proxy, transactional outbox | Entities, mappings, approvals, workflow state, decision records |
| Knowledge | Neptune, OpenSearch | Typed evidence graph, bounded GraphRAG, lexical and vector retrieval, contradiction mining |
| Feature and model | SageMaker Feature Store, Pipelines, Training, MLflow, Registry, endpoints | Point-in-time features, custom training, calibration, governed promotion |
| Agentic control | Bedrock, Guardrails, AgentCore | Capability routing, constrained generation, isolated sessions, policy-mediated tools |
| Workflow | Step Functions, EventBridge, SQS/SNS, API Gateway, Lambda / Fargate | Snapshot compiler, human waits, validation exchange, canonical APIs |
| Security and operations | IAM Identity Center, KMS, CloudTrail, GuardDuty, Security Hub, CloudWatch | Zero trust, immutable audit, scientific SLOs, incident evidence |

Storage semantics stay singular even when a fact is projected many times. S3/Iceberg is replay authority. Aurora is canonical transactional state. Neptune is a relationship projection. OpenSearch is a retrieval projection. Feature Store is historical and hot feature access. Source identity and snapshot lineage do not fork.

GraphRAG uses reviewed path templates and node, hop, and time budgets. Every traversed edge hydrates to admissible source evidence. Semantic similarity is not causal truth.

### Canonical contracts

| Contract | Invariant |
|---|---|
| `EvidenceUnit` | One admissible fact, passage, or path. Immutable source, applicability, policy, support status |
| `EndotypeProposal` | Drug-blind authoring boundary. Missing evidence is declared |
| `CandidateScore` | No surfaced candidate without the exact gate artifacts |
| `ValidationPackage` | Package hash binds hypothesis, protocol, materials, assays, endpoints, acceptance, approvals |
| `ValidationResult` | No training label before maturity and adjudication |
| `RegulatoryEvidencePackage` | Deterministic traceability matrix. Generated prose cannot replace records |
| `ScientificDecisionRecord` | Append-only. Corrections supersede |

### Guardrails, outside the model

| Layer | Enforcement |
|---|---|
| Authority | Manifests prohibit writes to causal, direction, safety, approval, and released-snapshot state |
| Syntax | JSON Schema, ontology, identifier, unit, range, and cross-field checks |
| Grounding | Field-level source support, entailment, and contradiction status |
| Security | Instruction/data separation, tool allow-list, capability token, egress and injection checks |
| Regulatory | Intended-use library, prohibited claims, controlled templates, approval checks |
| Economics | Preflight estimate and token, step, retrieval, graph, and time budgets |

### Model portfolio

Causal fusion, direction, ranking, and safety are not one generative model.

| Capability | Control | Release bar |
|---|---|---|
| Causal fusion | Calibrated stacker over independent evidence axes | Temporal and group splits, calibration, sentinel recovery |
| Direction | Signed rules and network propagation with abstention | Zero wrong-direction on the sentinel set |
| Ranking | Monotone ranker with a decomposed trace | NDCG, novelty, monotonicity. Calibration is a separate artifact |
| Uncertainty | Isotonic or conformal | Coverage, including subgroups |
| Safety | Deterministic rule engine | Gate recall, false-block analysis, mutation tests, dependency outage |
| Generative | Separate author, reviewer, and narrator families | Schema, grounding, contradiction, injection. Never causal or safety authority |

Promotion is a different workflow from training. It requires scientific, model-risk, security, quality, and operational evidence. Leakage controls cover code, data, entity lineage, time, retrieval, foundation-model cut-off, and publication. Aggregate accuracy is not a release decision.

### Scientific SLOs

Uptime is not the SLO that matters.

- Decision trace completeness for every surfaced candidate.
- Zero hard-gate bypass in release, replay, and adversarial suites.
- Zero wrong-direction promotion. `UNKNOWN` is preserved.
- Grounded generation above the approved citation and contradiction floor.
- Snapshot reproducibility from the manifest and artifact tuple.
- Validation labels linked to protocol, run, raw data, QC, deviation, and adjudication.
- Prior signed snapshot still served when the model control plane fails.

Incident severity follows scientific harm, data rights, and evidence integrity. Gate bypass, fabricated provenance, cross-tenant disclosure, systematic unsupported claims, wrong direction, corrupt validation results, and an unrecoverable snapshot each have a kill switch and an evidence-preservation path.

### Delivery sequence

| Phase | Exit evidence |
|---|---|
| 0 Control foundations | Threat model, isolation tests, immutable audit |
| 1 Snapshot evidence core | Rebuild and atomic rollback |
| 2 Graph and feature compiler | Golden fixtures, skew and leakage tests |
| 3 Deterministic scientific models | Sentinel, subgroup, calibration, and hard-gate suites |
| 4 Governed generation | Grounding, authority, injection, budget, and trajectory suites |
| 5 Human operating model | Reviewer usability and audit completeness |
| 6 Validation closed loop | Chain of custody and a prospective validation run |
| 7 Regulatory readiness | Mock audit of the evidence package |

Acceptance criterion: every scientific conclusion can be traced to admissible evidence, reconstructed from a released snapshot, challenged by independent controls, bounded by uncertainty and safety, approved by an accountable human, and carried into validation without trusting a model’s narrative about its own reasoning.

Release is vetoed for unresolved tenant or licence exposure, untraceable evidence, a causal or safety bypass, a wrong-direction sentinel failure, invalid point-in-time evaluation, missing rollback, an incomplete decision record, unbounded agent authority, an unquarantined validation defect, or an unowned critical dependency.

## Decision engineering index

Each packet records the decision, why, where, when, execution mechanics, the rejected alternative, degraded mode, validation evidence, and the revisit trigger. Full text is in the [architecture PDF](docs/architecture/Agentic-Biomedical-Intelligence-Scientific-Decision-Platform.pdf).

<details>
<summary>DE-01 to DE-56</summary>

**Snapshot, time, and evaluation**

- DE-01 Immutable scientific snapshot compiler
- DE-03 S3 and Iceberg as replay authority
- DE-04 Aurora PostgreSQL as canonical system of record
- DE-07 Point-in-time feature platform
- DE-21 Point-in-time dataset compiler
- DE-22 Grouped temporal scientific evaluation
- DE-23 Validation outcome as a context-rich label

**Graph and retrieval**

- DE-05 Neptune as a governed evidence-graph projection
- DE-06 OpenSearch hybrid biomedical retrieval
- DE-25 Retrieval policy before similarity scoring
- DE-26 Hybrid retrieval with a contradiction quota
- DE-27 Bounded GraphRAG path templates

**Agents, routes, and training**

- DE-08 Durable workflow separated from agent reasoning
- DE-09 AgentCore identity and tool mediation
- DE-10 MCP internally, signed agent-to-agent at the boundary
- DE-11 Scientific context compiler
- DE-12 Capability-based model routing
- DE-13 Independent author and reviewer model families
- DE-14 Schema-constrained scientific generation
- DE-24 Model, data, prompt, rule, and agent registries
- DE-45 Prospective shadow validation before autonomy
- DE-46 Human review as a training-data product
- DE-47 No partner data in shared training by default
- DE-48 Custom training with reproducible recipes
- DE-49 Distillation only after trace-quality proof

**Gates**

- DE-15 Deterministic causal eligibility gate
- DE-16 Abstaining direction resolver
- DE-17 Post-review deterministic safety gate
- DE-18 Monotone learning-to-rank with a decomposed trace
- DE-19 Ranking separated from calibrated uncertainty
- DE-20 Value-of-information triage
- DE-50 Safety and scientific rule bundles as code

**Rights, isolation, and records**

- DE-02 Multi-account scientific landing zone
- DE-28 Tenant isolation at every persistence and compute layer
- DE-29 Encryption context and cryptographic deletion
- DE-30 No shared semantic cache for confidential evidence
- DE-31 Immutable audit and decision lineage
- DE-32 Electronic approval as a domain primitive
- DE-37 Prompt-injection defence outside the model
- DE-38 Scientific data-poisoning controls
- DE-39 Licence-aware derivation and release packaging
- DE-40 Deletion across derived AI artifacts
- DE-51 Canonical scientific decision record
- DE-52 Validation exchange as a controlled supply chain
- DE-53 Regulatory-ready electronic records without over-claiming

**Resilience, cost, and governance**

- DE-33 Risk-tiered multi-Region resilience
- DE-34 Graceful AI degradation
- DE-35 Decision-level cost ledger
- DE-36 Denial-of-wallet protection
- DE-41 Regulatory evidence assembled from the decision graph
- DE-42 Controlled change-impact graph
- DE-43 Artifact-level progressive delivery
- DE-44 Scientific SLOs over generic uptime
- DE-54 Roadmap gated by control maturity
- DE-55 Principal architecture veto and exception process
- DE-56 Architecture evidence as a continuously generated product

</details>

## Run the console

Requires Node.js 22.

```bash
npm install
npm run dev
```

The dev server listens on port 8080. The scientific state lives in `src/components/platform/seed.ts` and the in-memory store in `src/components/platform/store.tsx`. Dispositions and new agents persist for the browser session. They are not a system of record.

```bash
npm run typecheck
npm run build
```

## Layout

```text
docs/architecture/     principal architecture
docs/walkthrough/      narrated UI walkthrough
docs/images/           console stills
src/components/platform/   console screens, fixture, and store
```

## Status

The console demonstrates control semantics on a fixture: signed snapshot, gate refusal, contradiction retention, bounded agents, human signature, and append-only records. It does not certify a medical device, reproduce a production landing zone, or claim measured clinical performance. Quality-attribute scenarios, the production verification matrix, and the game-day catalogue in the architecture are the acceptance tests for a real deployment, not results this repository has executed.
