# For Buyers

For organizations acquiring annotated medical imaging datasets — pharmaceutical companies, medical device manufacturers, AI startups, government health agencies, and academic groups commissioning external data work.

## The procurement gap

Medical imaging dataset procurement currently relies on vendor claims and manual post-delivery review. There is no shared, machine-checkable definition of what counts as documented provenance, adequate quality, or acceptance-ready structure.

Without an objective acceptance criterion, dataset quality is typically assessed after integration begins — when remediation is most expensive and timelines are already committed.

A compliance benchmark of four widely used public medical imaging datasets, scored against the VIDS specification, illustrates the scale of the gap:

| Dataset | VIDS Compliance |
|---|---|
| BraTS | 39% |
| MSD | 30% |
| LIDC-IDRI | 27% |
| CheXpert | 20% |

Source: [VIDS benchmarks repository](https://github.com/vids-standard/vids-benchmarks).

If publicly maintained reference datasets score in this range, privately commissioned datasets — which receive far less external scrutiny — are unlikely to score higher.

## Recommended action

**Include a VIDS validation requirement as an acceptance condition in your next dataset procurement.**

The reference contract language is drop-in. It defines acceptance as "zero failed rules under the VIDS Reference Validator at the specified Profile" — an objective, automated, vendor-agnostic criterion.

[**Reference Procurement Language →**](sow-addendum.md){ .md-button .md-button--primary }

CC BY 4.0. Free to use, adapt, and redistribute.

## How VIDS works for buyers

The buyer-side adoption surface has four parts. Each is purpose-built and citable in contracts and audits.

**[Reference Procurement Language](sow-addendum.md)** — drop-in clauses that make VIDS PASS the acceptance condition for dataset deliveries.

**[Compliance Evaluation](evaluation.md)** — diagnostic assessment of an existing dataset against the 22 VIDS dimensions. Used to surface gaps in already-acquired datasets or vendor sample deliveries before contracting.

**[Scoring Rubric](scoring-rubric.md)** — the 22-dimension scoring framework used in compliance evaluations. Published openly so any score is traceable to documented criteria.

**[Validation Certificate](certificate.md)** — issued for datasets that pass full validation. The artifact a vendor attaches to a delivery and a buyer forwards internally as proof of acceptance.

## What VIDS gives a buyer

**An objective acceptance criterion.** The validator runs on the delivered dataset and produces a binary pass/fail result. No subjective interpretation, no checklist negotiation, no "trust us" deliveries.

**A reference framework citable in contracts and audits.** EU AI Act, IMDRF GMLP, and the FDA AI/ML SaMD Action Plan all point toward machine-readable provenance. VIDS provides the structure that makes those requirements concrete.

**Vendor independence.** The specification is open (CC BY 4.0). The validator is open-source (Apache 2.0). No supplier lock-in at the standard level. Datasets curated under VIDS can be exported to nnU-Net, MONAI, COCO, or flat NIfTI without losing the underlying data or provenance.

**Lower cost of failure.** A vendor delivery that fails validation is identified at acceptance, not after integration. Remediation occurs while the contractual obligation is still active and the cost falls on the vendor.

## About operators

VIDS is an open standard. Compliance evaluations and certificate issuance are performed by approved evaluation operators. Princeton Medical Systems is the current sole operator and maintains the reference validator, evaluation rubric, and certificate format.

For evaluation requests or procurement-specific inquiries: [info@princetonmed.systems](mailto:info@princetonmed.systems)
