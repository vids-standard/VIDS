# Compliance Evaluation

A VIDS Compliance Evaluation is a diagnostic assessment of a medical imaging dataset against the [22-dimension VIDS scoring rubric](scoring-rubric.md). It surfaces structural, provenance, quality, and ML-readiness gaps that would otherwise be discovered after integration begins.

## When to request an evaluation

Evaluations are most useful in three scenarios:

**Pre-contract due diligence.** A vendor has provided a sample delivery as part of an RFP response. An evaluation establishes whether the sample meets VIDS requirements before the full contract is awarded.

**Post-delivery audit.** A dataset has already been received and integration is underway. An evaluation produces an objective record of what was delivered, enabling structured remediation discussions with the vendor.

**Internal portfolio assessment.** An organization holds multiple datasets from different sources or eras. Evaluations across the portfolio identify which datasets are audit-ready for upcoming regulatory submissions and which require remediation.

## What an evaluation covers

Datasets are scored against the 22 dimensions defined in the [VIDS Compliance Scoring Rubric](scoring-rubric.md):

| Category | Dimensions | What is checked |
|---|---|---|
| [Structure](scoring-rubric.md#a-structure-5-dimensions) | 5 | Directory layout, naming conventions, dataset metadata |
| [Annotation Provenance](scoring-rubric.md#b-annotation-provenance-6-dimensions) | 6 | Annotator identity, role, timestamp, tool, protocol, multi-annotator tracking |
| [Quality Documentation](scoring-rubric.md#c-quality-documentation-5-dimensions) | 5 | QA process, results, inter-annotator agreement, validation evidence, class distribution |
| [ML Readiness](scoring-rubric.md#d-ml-readiness-6-dimensions) | 6 | Label consistency, format compatibility, completeness, intended use, limitations, splits |

Each dimension scores binary (1 if the pass criterion is met, 0 otherwise). The total score and per-dimension breakdown are reported alongside the [VIDS Reference Validator](https://github.com/vids-standard/vids-standard){target="_blank" rel="noopener"} output, which establishes the binary PASS/FAIL outcome at the chosen Profile.

## What you receive

An evaluation produces a structured report covering:

- **Executive Summary** — VIDS validation status (PASS / FAIL), rubric score (X / 22), and the largest gaps in 1–2 lines each
- **Compliance Breakdown** — per-category scores with notes on each rule cluster
- **Operational Implications** — concrete impact on the dataset's usability for the intended use
- **Remediation Path** — the steps required to bring the dataset into compliance, with effort tier (low / moderate / significant) and primary dependency
- **Comparative Reference** — how the dataset compares to public benchmark datasets

The validator's raw JSON output is included as an attachment for independent re-validation.

## Process

1. **Submit the dataset or its directory description.** A few sample sidecar JSONs are typically sufficient if the full dataset cannot be transferred.
2. **Specify the intended use** — prototyping, production, or regulatory submission. This determines the recommended Profile (POC or Full).
3. **Receive the report within 48 hours.** A typical evaluation takes 1–2 hours of evaluator time once the dataset is accessible. The 48-hour SLA covers intake, scoring, and report production.

## Operator

VIDS Compliance Evaluations are performed by approved evaluation operators using the VIDS Reference Validator and the published scoring rubric. Princeton Medical Systems is the current sole operator.

[Request an evaluation](mailto:info@princetonmedicalsystems.com?subject=VIDS%20compliance%20evaluation%20request){ .md-button .md-button--primary }

## Related

- [Scoring Rubric](scoring-rubric.md) — the 22-dimension framework used in evaluations
- [Validation Certificate](certificate.md) — issued for datasets that pass full validation
- [Reference Procurement Language](sow-addendum.md) — contract clauses that make VIDS PASS the acceptance condition
