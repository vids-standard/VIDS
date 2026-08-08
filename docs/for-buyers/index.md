# For Buyers

For organizations acquiring annotated medical imaging datasets — medical device manufacturers (medtech), AI/ML developers and startups, pharmaceutical companies, government health agencies, and academic groups commissioning external data work.

## The procurement gap

Medical imaging dataset procurement currently relies on vendor claims and manual post-delivery review. There is no shared, machine-checkable definition of what counts as documented provenance, adequate quality, or acceptance-ready structure.

Without an objective acceptance criterion, dataset quality is typically assessed after integration begins — when remediation is most expensive and timelines are already committed.

Our published benchmark found substantial documentation gaps across four widely used public medical imaging datasets, with provenance the weakest category throughout. The results, methodology and per-dimension scores are on the [published benchmark](../published-benchmark.md) page.

If established public datasets show gaps of this scale, buyers should not assume that privately commissioned datasets are fully documented without checking.

## Recommended action

**Include a VIDS validation requirement as an acceptance condition in your next dataset procurement.**

The reference contract language is drop-in. It defines acceptance as "zero failed rules under the VIDS Reference Validator at the specified Profile" — an objective, automated, vendor-agnostic criterion.

[**Reference Procurement Language →**](sow-addendum.md){ .md-button .md-button--primary }

CC BY 4.0. Free to use, adapt, and redistribute.

## How VIDS works for buyers

The buyer-side adoption surface has four parts. Each serves a defined role in procurement and documentation review.

**[Reference Procurement Language](sow-addendum.md)** — drop-in clauses that make VIDS PASS the acceptance condition for dataset deliveries.

**[Dataset Documentation Assessment](documentation-assessment.md)** — a diagnostic review against the published 22-dimension methodology, used to surface documentation gaps in already-acquired datasets or vendor samples before contracting. Diagnostic only; it does not determine VIDS conformance.

**[Assessment Methodology](assessment-methodology.md)** — the 22 published dimensions used in documentation assessments, the same ones behind the published benchmark. Open, so any score is traceable to documented criteria.

**[Validation Report](validation-report.md)** — the machine-readable validator output. A vendor attaches it to a delivery; a buyer reproduces it independently before accepting. Reproducibility is what makes it evidence.

## What VIDS gives a buyer

**An objective acceptance criterion.** The validator runs on the delivered dataset and produces a binary pass/fail result. No subjective interpretation, no checklist negotiation, no "trust us" deliveries.

**A reference framework for contracts and documentation review.** The EU AI Act, IMDRF Good Machine Learning Practice (GMLP), and the FDA AI/ML SaMD Action Plan all emphasize stronger governance of AI training data, including its origin, annotation, and documentation. VIDS supports these objectives through structured, machine-readable provenance.

**Vendor independence.** The specification is open (CC BY 4.0). The validator is open-source (Apache 2.0). No supplier lock-in at the standard level. Datasets curated under VIDS can be exported to nnU-Net, MONAI, COCO, or flat NIfTI without losing the underlying data or provenance.

**Lower cost of failure.** A vendor delivery that fails validation is identified at acceptance, not after integration. Remediation occurs while the contractual obligation is still active and the cost falls on the vendor.

**Scope of validation.** VIDS verifies that a dataset's documentation is present and structured: dataset structure, imaging metadata, annotation files and their provenance, quality documentation, and ML readiness. It does not assess the clinical correctness of individual annotations, the diagnostic accuracy of any model trained on the dataset, or suitability for a specific clinical use case. A passing result establishes that the required documentation exists and is where it should be, not that the underlying data is clinically correct or fit for any particular purpose.

## Who runs the validator

Anyone. The specification is published under CC BY 4.0 and the reference validator under Apache 2.0, so a buyer, a vendor, or a third party can run it and get the same result. Nothing about a VIDS result depends on who produced it, which is the property that makes it useful in a contract.

Princeton Medical Systems maintains the reference validator as steward of the standard, and separately offers documentation assessment as a commercial service using the published benchmark methodology. The service is not part of the standard, and no VIDS result depends on it. Those are different roles, and the standard does not depend on the service: no VIDS result requires our involvement, and we issue nothing that a buyer could not generate themselves.

For assessment requests or procurement-specific inquiries: [info@princetonmedicalsystems.com](mailto:info@princetonmedicalsystems.com)

## Reference materials

**[LIDC-Hybrid-100 reference dataset](https://doi.org/10.5281/zenodo.19582717){target="_blank" rel="noopener"}** — 100 lung CT volumes with consensus segmentations from four radiologist reads, scored 21/21 on the VIDS Full profile. The publicly available worked example of what a VIDS-compliant dataset looks like. CC BY 4.0.

**[VIDS arXiv preprint](https://arxiv.org/abs/2604.17525){target="_blank" rel="noopener"}** — "VIDS: A Verified Imaging Dataset Standard for Medical AI." Includes the published 22-dimension benchmark methodology, the analysis of four widely used public datasets, and the design rationale behind the validation profiles.
