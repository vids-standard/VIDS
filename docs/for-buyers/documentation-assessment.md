# Dataset Documentation Assessment

A dataset documentation assessment is a diagnostic review of a medical imaging dataset against the [scoring rubric](scoring-rubric.md), a Princeton Medical Systems methodology. It surfaces structural, provenance, quality, and ML-readiness gaps that would otherwise be discovered after integration begins.

It is diagnostic, not determinative. An assessment explains what is missing and what it would take to close the gaps; it does not issue a conformance result.

**Assessment scores describe documentation coverage. The validator determines conformance. Where they appear to disagree, the validator governs.**

## When to request an assessment

Assessments are most useful in three scenarios:

**Pre-contract due diligence.** A vendor has provided a sample delivery as part of an RFP response. An assessment shows how completely the sample is documented, and what would need to change, before the full contract is awarded.

**Post-delivery review.** A dataset has already been received and integration is underway. An assessment produces a written record of what was delivered, enabling structured remediation discussions with the vendor.

**Internal portfolio assessment.** An organization holds multiple datasets from different sources or eras. Assessments across the portfolio identify which datasets carry the documentation an upcoming regulatory submission will call for, and which require remediation.

## What an assessment covers

Datasets are scored against the 22 dimensions defined in the [scoring rubric](scoring-rubric.md):

| Category | Dimensions | What is checked |
|---|---|---|
| [Structure](scoring-rubric.md#a-structure-5-dimensions) | 5 | Directory layout, naming conventions, dataset metadata |
| [Annotation Provenance](scoring-rubric.md#b-annotation-provenance-6-dimensions) | 6 | Annotator identity, role, timestamp, tool, protocol, multi-annotator tracking |
| [Quality Documentation](scoring-rubric.md#c-quality-documentation-5-dimensions) | 5 | QA process, results, inter-annotator agreement, validation evidence, class distribution |
| [ML Readiness](scoring-rubric.md#d-ml-readiness-6-dimensions) | 6 | Label consistency, format compatibility, completeness, intended use, limitations, splits |

Each dimension scores binary (1 if the pass criterion is met, 0 otherwise). The total score and per-dimension breakdown are reported alongside the [VIDS Reference Validator](https://github.com/vids-standard/vids-standard){target="_blank" rel="noopener"} output, which establishes the binary PASS/FAIL outcome at the chosen Profile.

## What you receive

An assessment produces a structured report covering:

- **Executive Summary** — the validator result for the dataset, the rubric score (X / 22) as documentation coverage, and the largest gaps in 1–2 lines each
- **Documentation Coverage Breakdown** — per-category scores with notes on each dimension cluster
- **Operational Implications** — concrete impact on the dataset's usability for the intended use
- **Remediation Path** — the steps required to close the identified documentation gaps, with effort tier (low / moderate / significant) and primary dependency. Any validator failures are listed separately, since those are the ones that determine conformance
- **Context** — how the identified gaps compare with what is commonly missing in public datasets, drawn from the [published benchmark](../published-benchmark.md). The two use different instruments, so this is orientation rather than a like-for-like score comparison

The validator's raw JSON output is included as an attachment for independent re-validation.

## Process

1. **Submit the dataset or its directory description.** A few sample sidecar JSONs are typically sufficient if the full dataset cannot be transferred.
2. **Specify the intended use** — prototyping, production, or regulatory submission. This determines the recommended Profile (POC or Full).
3. **Receive the report within 48 hours.** A typical assessment takes 1–2 hours of reviewer time once the dataset is accessible. The 48-hour SLA covers intake, scoring, and report production.

## Who performs an assessment

Princeton Medical Systems offers documentation assessment as a commercial service, using the VIDS Reference Validator and its own published scoring rubric. Both are open: the validator under Apache 2.0, the rubric under CC BY 4.0. Nothing in an assessment requires our involvement: a buyer or vendor can apply the same published criteria to the same inputs and compare their findings with ours.

What the service adds is time and interpretation, not authority.

[Request an assessment](mailto:info@princetonmedicalsystems.com?subject=Dataset%20documentation%20assessment%20request){ .md-button .md-button--primary }

## Related

- [Scoring Rubric](scoring-rubric.md) — the criteria used in assessments
- [Validation Report](validation-report.md) — the validator output for any validation run, PASS or FAIL
- [Reference Procurement Language](sow-addendum.md) — contract clauses that make VIDS PASS the acceptance condition
