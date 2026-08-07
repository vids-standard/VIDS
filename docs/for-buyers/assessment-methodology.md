# Documentation Assessment Methodology

The 22 dimensions used in [dataset documentation assessments](documentation-assessment.md). These are the dimensions of the [published benchmark](../published-benchmark.md), applied to a single dataset rather than across four.

The same dimensions, the same three-valued scale, and the same definitions appear in the paper, in the benchmark repository, and here. A score produced in an assessment can be read directly against the published results.

!!! warning "An assessment score is not a conformance result"
    Assessment scores describe documentation coverage. The validator determines conformance. Where they appear to disagree, the validator governs.

## Scoring

| Score | Meaning |
|---|---|
| **1.0** | Satisfied |
| **0.5** | Partial |
| **0.0** | Absent |

Partial credit has a precise definition, quoted from the published methodology:

> Information is present in the dataset but not in a machine-readable or standardized form (e.g., provenance described in a companion paper but absent from the dataset files).

A dataset that describes its annotation process in an accompanying document has done something real, and something different from a dataset that documents nothing. It has also not done what VIDS asks, which is to put that information where a machine can find it. The middle value keeps those two apart.

## Reading a score

The score is reported as X / 22, with absent and partially satisfied dimensions identified separately. There is no threshold and no verdict. A dataset at 18 / 22 is not failing; it is a dataset with four documentation gaps, identified so they can be closed.

Whether the dataset conforms is answered by running the validator. That answer is binary, automated, and reproducible by anyone holding the dataset.

## The 22 dimensions

### Structure

| | Dimension |
|---|---|
| **S1** | Dataset marker |
| **S2** | Dataset description |
| **S3** | Participant registry |
| **S4** | Human-readable README |
| **S5** | Subject hierarchy |
| **S6** | Session hierarchy |

### Imaging

| | Dimension |
|---|---|
| **I1** | Standardized format (NIfTI) |
| **I2** | Per-image metadata sidecar |
| **I3** | Consistent file naming |

### Annotation

| | Dimension |
|---|---|
| **A1** | Structured annotation directory |
| **A2** | Segmentation masks |
| **A3** | Per-annotation metadata sidecar |
| **A4** | Machine-readable label map |

### Provenance

| | Dimension |
|---|---|
| **P1** | Annotator identity |
| **P2** | Annotator credentials |
| **P3** | Annotation tool |
| **P4** | Annotation date |
| **P5** | QC review documented |

Provenance is consistently the weakest category. Across the four datasets in the published benchmark it averaged 0.38 out of 5. It is also the category a downstream reader most needs when deciding whether to rely on a label.

### Quality

| | Dimension |
|---|---|
| **Q1** | Inter-annotator agreement |
| **Q2** | Quality summary |

### ML Readiness

| | Dimension |
|---|---|
| **M1** | Documented splits |
| **M2** | Split rationale |

## Applying the methodology

These are the dimensions as published. They were defined and applied to the datasets described in the paper, which included both segmentation and classification datasets.

Each dimension asks a specific question and records what it finds. A2 asks whether segmentation masks are present, so a dataset built for a different annotation task records 0.0 there. In the published benchmark, CheXpert scored 0.0 on A2 for that reason. That is the instrument reporting accurately rather than judging the dataset, and an assessment names the dimension alongside the score so a reader can see what was asked.

Whether the annotation dimensions should be generalized to task-appropriate annotation artifacts, while preserving comparability with the published benchmark, is an open question for a future specification release. It is recorded rather than answered here, because changing a published dimension is a governance decision and not a website edit.

## Additional buyer considerations

These are not scored and are not part of VIDS. They are questions worth asking, raised alongside an assessment rather than folded into a number.

- **Intended use.** Is the population, indication and setting the dataset was assembled for stated anywhere?
- **Known limitations.** Are the failure modes, exclusions and biases the curator is aware of written down?
- **Class distribution.** For a labelled dataset, is the distribution across classes documented, and does it match what your use requires?
- **Licensing.** Are the terms clear, and do they permit what you intend, including model training and redistribution?
- **Governance.** Who maintains the dataset, and what happens when a defect is found after delivery?

They are unscored deliberately. A score implies a defined criterion and a defensible cut-off; these are matters for judgement and discussion, and a number would obscure that rather than sharpen it.

## Provenance of this methodology

The dimensions and scoring are those published in:

> Muthu, J. S. and Shalen, J. *VIDS: A Verified Imaging Dataset Standard for Medical AI.* arXiv:2604.17525.

The per-dimension scores for the four benchmarked datasets, and a script that recomputes the totals from them, are in [vids-benchmarks](https://github.com/vids-standard/vids-benchmarks){target="_blank" rel="noopener"}.

The dimension definitions and per-dimension scores in `vids-benchmarks` are published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/){target="_blank" rel="noopener"}, so anyone may apply the same criteria. That is the point of publishing them: an assessment can be checked rather than taken on trust, and a buyer or vendor can reach their own conclusion from the same definitions.

## Related

- [Published Benchmark](../published-benchmark.md) — the same methodology applied to four public datasets
- [Dataset Documentation Assessment](documentation-assessment.md) — the service that applies it
- [Validation Report](validation-report.md) — the validator output, which determines conformance
