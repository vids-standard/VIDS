# Dataset Documentation Assessment

A dataset documentation assessment is a diagnostic review of a medical imaging dataset against the [published assessment methodology](scoring-rubric.md): the 22 dimensions and 1 / 0.5 / 0 scoring published in Muthu and Shalen, arXiv:2604.17525, applied to one dataset rather than four. It surfaces gaps across structure, imaging, annotation, provenance, quality, and ML readiness that might otherwise be discovered only after integration begins.

It is diagnostic, not determinative. An assessment explains what is missing and what it would take to close the gaps; it does not issue a conformance result.

**Assessment scores describe documentation coverage. The validator determines conformance. Where they appear to disagree, the validator governs.**

## When to request an assessment

Assessments are most useful in three scenarios:

**Pre-contract due diligence.** A vendor has provided a sample delivery as part of an RFP response. An assessment shows how completely the sample is documented, and what would need to change, before the full contract is awarded.

**Post-delivery review.** A dataset has already been received and integration is underway. An assessment produces a written record of what was delivered, enabling structured remediation discussions with the vendor.

**Internal portfolio assessment.** An organization holds multiple datasets from different sources or eras. Assessments across the portfolio identify which datasets carry the documentation an upcoming regulatory submission will call for, and which require remediation.

## What an assessment covers

Datasets are scored against the 22 published dimensions in six categories, described in the [assessment methodology](scoring-rubric.md):

| Category | Dimensions | What is checked |
|---|---|---|
| [Structure](scoring-rubric.md#structure) | 6 | Dataset marker, description, participant registry, README, subject and session hierarchy |
| [Imaging](scoring-rubric.md#imaging) | 3 | Standardized format, per-image metadata sidecar, consistent file naming |
| [Annotation](scoring-rubric.md#annotation) | 4 | Annotation directory, annotation artifacts, per-annotation sidecar, machine-readable label map |
| [Provenance](scoring-rubric.md#provenance) | 5 | Annotator identity, credentials, tool, date, QC review |
| [Quality](scoring-rubric.md#quality) | 2 | Inter-annotator agreement, quality summary |
| [ML Readiness](scoring-rubric.md#ml-readiness) | 2 | Documented splits, split rationale |

Each dimension is scored 1.0, 0.5 or 0.0 using the published definitions. The total and per-dimension findings describe documentation coverage. The validator separately determines VIDS conformance.

## What you receive

An assessment produces a structured report covering:

- **Executive Summary** — the validator result for the dataset, the assessment score (X / 22) as documentation coverage, and the largest gaps in 1–2 lines each
- **Documentation Coverage Breakdown** — per-category scores with notes on each dimension cluster
- **Operational Implications** — concrete impact on the dataset's usability for the intended use
- **Remediation Path** — the steps required to close the identified documentation gaps, with effort tier (low / moderate / significant) and primary dependency. Any validator failures are listed separately, since those are the ones that determine conformance
- **Context** — how the identified gaps compare with the [published benchmark](../published-benchmark.md) of four public datasets. The same methodology applies to both, so the comparison is direct

The validator's raw JSON output is included as an attachment for independent re-validation.

## Process

1. **Submit the dataset or its directory description.** A few sample sidecar JSONs are typically sufficient if the full dataset cannot be transferred.
2. **Specify the intended use** — prototyping, production, or regulatory submission. This determines the recommended Profile (POC or Full).
3. **Receive the report within 48 hours.** A typical assessment takes 1–2 hours of reviewer time once the dataset is accessible. The 48-hour SLA covers intake, scoring, and report production.

## Who performs an assessment

Princeton Medical Systems offers documentation assessment as a commercial service, using the VIDS Reference Validator and the published benchmark methodology. Both are open: the validator under Apache 2.0, the rubric under CC BY 4.0. Nothing in an assessment requires our involvement: a buyer or vendor can apply the same published criteria to the same inputs and compare their findings with ours.

What the service adds is time and interpretation, not authority.

[Request an assessment](mailto:info@princetonmedicalsystems.com?subject=Dataset%20documentation%20assessment%20request){ .md-button .md-button--primary }

## Related

- [Assessment Methodology](scoring-rubric.md) — the 22 published dimensions used in assessments
- [Validation Report](validation-report.md) — the validator output for any validation run, PASS or FAIL
- [Reference Procurement Language](sow-addendum.md) — contract clauses that make VIDS PASS the acceptance condition
