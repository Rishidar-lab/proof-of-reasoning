# Proof-of-Reasoning (POR)

## Status

**HISTORICAL RESEARCH / FAILED HYPOTHESIS / LESSONS LEARNED** — not maintained, not implemented, not deployed.

This repository preserves a February 2026 design paper for a Bittensor reasoning-verification subnet exactly as written, followed by a restoration note and a criticism matrix added in October 2026. It is kept because the failure mode is instructive, not because the protocol works. Nothing below the original paper should be read as a claim that any part of it was built. See [Criticism matrix](#criticism-matrix-added-2026-10-22) and [Lessons](#lessons-added-2026-10-22) at the end.

---

## Overview

Proof-of-Reasoning (POR) is a structured reasoning verification subnet designed for the Bittensor network.

It introduces a consensus-backed mechanism for validating logical reasoning rather than probabilistic output similarity. POR aims to establish reasoning as a verifiable primitive within decentralized AI infrastructure.

This project explores how structured proof submission, validator scoring, and incentive-aligned emissions can collectively enable reproducible and audit-ready reasoning validation.

---

## Problem Statement

Decentralized AI networks currently reward output similarity, performance benchmarks, or response quality heuristics.

However:

- There is no formalized primitive for verifying logical reasoning correctness.
- Validators often assess outputs without structured proof decomposition.
- Incentive mechanisms do not explicitly reward structured logical validity.
- There is no reproducible consensus mechanism for reasoning evaluation.

As AI systems become more infrastructure-critical, probabilistic validation is insufficient for applications requiring logical rigor.

---

## Proposed Solution

Proof-of-Reasoning (POR) introduces a structured validation layer consisting of:

1. **Structured Proof Submission**
   - Miners submit reasoning in a standardized, decomposed format.
   - Proofs are broken into explicit logical steps.
   - Each step references prior premises or derivations.

2. **Validator Scoring Rubric**
   - Validators independently evaluate:
     - Logical coherence
     - Step validity
     - Premise consistency
     - Conclusion correctness
   - Scoring follows a predefined rubric to minimize subjectivity.

3. **Consensus Aggregation**
   - Validator scores are aggregated using median-based statistical consensus.
   - Outlier detection reduces impact of collusion or malicious scoring.
   - Stake-weighted adjustments refine emission alignment.

4. **Incentive-Aligned Emissions**
   - Emissions are distributed based on validated reasoning accuracy.
   - Validators are rewarded for alignment with consensus.
   - Malicious or consistently deviating actors face reduced influence.

---

## System Architecture (High-Level)

### 1. Miner Layer
- Accepts structured reasoning queries.
- Produces decomposed proof chains.
- Submits proofs to validation pool.

### 2. Validator Layer
- Independently evaluates proof steps.
- Applies standardized scoring rubric.
- Reports structured evaluation results.

### 3. Aggregation Layer
- Computes median consensus score.
- Detects statistical deviation.
- Adjusts validator influence weights.

### 4. Emission Layer
- Allocates rewards based on:
  - Proof validity score
  - Validator alignment accuracy
  - Stake-weighted influence

---

## Core Design Principles

- **Structured Reasoning over Output Matching**
- **Consensus-backed Logical Validation**
- **Incentive Alignment**
- **Anti-Collusion Safeguards**
- **Reproducibility**
- **Minimal Subjectivity in Evaluation**

---

## Anti-Collusion Considerations

- Median-based aggregation reduces validator cartel influence.
- Statistical deviation penalties discourage coordinated bias.
- Stake-weighted scoring prevents low-stake manipulation.
- Historical validator reliability may adjust influence over time.

---

## Example Reasoning Flow

1. Query: Logical or mathematical problem.
2. Miner submits structured proof:
   - Step 1: Premise
   - Step 2: Derived inference
   - Step 3: Transformation
   - Final Conclusion
3. Validators independently score each step.
4. Aggregator computes consensus score.
5. Emission distributed proportionally.

---

## Potential Use Cases

- Mathematical proof verification
- Formal logic validation
- Regulatory reasoning compliance
- On-chain reasoning audits
- AI reasoning benchmarking

---

## Current Status

Conceptual architecture and incentive design phase.  
Hackathon submission prototype stage.

Planned next steps:

- Formal proof schema specification
- Validator rubric formalization
- Emission simulation modeling
- Bittensor subnet technical integration draft
- Adversarial simulation testing

---

## Vision

Proof-of-Reasoning aims to move decentralized AI from probabilistic validation toward structured, auditable, and reproducible reasoning verification.

The long-term goal is to establish reasoning consensus as a first-class primitive within decentralized AI networks.

---

## Author

Rishidar D  
Nexus Layer 1 Prover  
Independent AI Infrastructure Researcher

---
## Current status (restoration note, added 2026-10-22)

This document is the historical project paper restored from commit `3299580` (`2026-02-21`, author Rishidar D / "Nexus Layer 1 Prover"). It is the substantive Proof-of-Reasoning (POR) paper that preceded the generic template now at `main` (`153c9cf`, `2026-07-04`).

**What was proposed.** A structured reasoning-verification subnet for Bittensor: miners submit decomposed logical proofs; validators score logical coherence, step validity, premise consistency and conclusion correctness using a predefined rubric; scores are aggregated by median-based consensus; emissions align with validated accuracy. Anti-collusion safeguards (median aggregation, deviation penalties, stake-weighted scoring) are listed as principles, but no concrete commit-reveal or commitment mechanism is specified. Status at the time: "Conceptual architecture and incentive design phase. Hackathon submission prototype stage."

**What implementation evidence exists.** None in this repository. `README.md` is the only path in every commit (`12cd75f`, `3299580`, `153c9cf`). There are no source files, tests, schema, contracts, or deployed instances here. The five planned next steps (formal proof schema, validator rubric formalization, emission simulation modeling, Bittensor subnet technical integration draft, adversarial simulation testing) were not completed.

**What remains unvalidated.** Every strong operational claim attributed to POR elsewhere (subnet registration, validator/miner run, emission formulas, confidence fields, budget conservation, 30-second latency, slashing, unstake cooldown, novelty, inevitability, adoption) is not established by this document and remains pending inspection of the separately recovered `POR_FINAL_SUBMISSION_1.md`, which is not available in this environment. No experiment, competition outcome, or causal history is claimed. The characterization of POR as a failed attempt is the project owner's own account; technical shortcomings above are stated individually with reference to this document.

## Criticism matrix (added 2026-10-22)

Each criticism that has been raised against POR is checked against **this document only** (the 4,529-byte paper restored from `3299580`). "Unresolved" means the criticism targets a separate, later submission file (`POR_FINAL_SUBMISSION_1.md`) that is not available in this repository or on the preserving machine; its byte count and contents are unverified and no conclusion that depends on it is asserted here.

| # | Criticism | Verdict against this paper | Basis in the text |
|---|---|---|---|
| F1 | The "validator rubric" is a judgement procedure, not a verifier; it cannot establish logical validity. | **Partially supported** | A scoring rubric (coherence, step validity, premise consistency, conclusion correctness) is proposed; "validator rubric formalization" is listed as *future* work. No formal verifier is specified. |
| F2 | Rewarding validator "alignment with consensus" is a conformity incentive, exploitable by coordinated scoring. | **Supported** | §Proposed Solution 3–4: median consensus plus explicit reward for alignment with consensus. No mechanism separates "correct" from "agreeing". |
| F3 | No concrete anti-collusion mechanism (commit–reveal, commitments, randomised assignment). | **Partially supported** | §Anti-Collusion Considerations lists median aggregation, deviation penalties and stake weighting as *principles*; no commitment scheme or assignment protocol is specified. |
| F4 | No stated precedence among competing scoring signals. | **Not supported** | The paper describes a single median aggregation path; the multi-signal precedence problem does not arise in this text. |
| F5 | Conflicting emission formulas / confidence-bonus fields between sections. | **Unresolved** | No formulas or confidence fields exist in this paper. The criticism targets the unavailable submission file. |
| F6 | Specific Bittensor runtime claims (registration, latency, slashing, unstake cooldown) are unsubstantiated. | **Unresolved** | This paper positions POR as a Bittensor subnet but makes no runtime claims. The criticism targets the unavailable submission file. |
| F7 | Novelty / readiness claims exceed the artifact. | **Supported (as a gap)** | The paper's own status line reads "Conceptual architecture and incentive design phase. Hackathon submission prototype stage." Any stronger claim made elsewhere is not supported by this document. |

## Lessons (added 2026-10-22)

Derived only from the matrix above; no experiment or competition outcome is claimed.

1. **A rubric is not a verifier.** Scoring "logical coherence" with human-style criteria produces opinions, not proofs. Reasoning validity needs a checkable object (a proof term, a trace against a formal system, or an executable test), not a score.
2. **Do not pay for agreement.** Any reward for alignment with consensus makes consensus the objective. If the aggregate can be gamed by coordinating, the mechanism measures coordination, not correctness.
3. **"Anti-collusion" must be a protocol, not a principle.** Commit–reveal, randomised validator assignment and stake-at-risk are concrete; "median aggregation" alone is not.
4. **State the artifact's maturity in the artifact.** The paper's own status line was honest; the gap opened when later descriptions exceeded it. Status should travel with the document.

These lessons shaped later work in this account that uses deterministic verification (signature/digest checks, test suites, on-chain invariants) in place of consensus-scored judgement.
