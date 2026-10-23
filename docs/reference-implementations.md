# Reference Implementations

Reference implementations are published datasets that show VIDS applied to real imaging data. Each one is archived on Zenodo with a DOI, so you can download it, run the validator yourself, and compare your result with the published one.

Under [MD-0003](governance/decision-records.md), accepted in July 2026, a VIDS reference implementation publishes the VIDS metadata layer and its documentation; source images stay with their original repository and are cited by DOI. LIDC-Hybrid-100 was published before that policy and includes the CT volumes.

## LIDC-Hybrid-100 (lung CT)

- **What it is**: 100 lung CT volumes from LIDC-IDRI with consensus nodule segmentations derived from four-radiologist annotations, structured as a VIDS dataset
- **Annotation type**: Segmentation
- **Validator result**: 21 of 21 rules PASS under the Full profile, validator 1.2.1
- **Licence**: CC BY 4.0
- **DOI**: [10.5281/zenodo.19582717](https://doi.org/10.5281/zenodo.19582717){target="_blank" rel="noopener"}

Check it yourself:

```bash
pip install vids-validator
vids-validate lidc-hybrid-100 --profile full
```

The [Validation Report](for-buyers/validation-report.md) page shows the full JSON output for this dataset.

## VIDS-Fundus 1.0 (fundus photography, IDRiD)

- **What it is**: The VIDS metadata layer for the Indian Diabetic Retinopathy Image Dataset (IDRiD): 443 fundus annotation sidecars covering grading and lesion segmentation
- **Annotation types**: Classification and segmentation
- **Validator result**: 15 of 21 rules PASS under validator 1.2.1
- **Source images**: Not redistributed. Cited by the IDRiD DOI [10.21227/H25W98](https://doi.org/10.21227/H25W98){target="_blank" rel="noopener"}
- **Licence**: CC BY 4.0
- **Reference implementation DOI**: [10.5281/zenodo.21511086](https://doi.org/10.5281/zenodo.21511086){target="_blank" rel="noopener"}
- **Fundus specification DOI**: [10.5281/zenodo.21488816](https://doi.org/10.5281/zenodo.21488816){target="_blank" rel="noopener"}

The fundus specification record defines the metadata model and annotation schema for fundus photography datasets and is the companion to the reference implementation above.

## What a reference implementation shows

A validator result shows that a dataset satisfies the machine-checkable requirements of the selected profile, within the checks the validator implements. VIDS verifies that documentation is present and structured; it does not certify a dataset. It does not judge the clinical accuracy of any annotation.

## Related

- [Published Benchmark](published-benchmark.md): documentation coverage across four widely used public imaging datasets.
- [Validator Quick Start](validator/quickstart.md): run the validator on your own dataset.
- [Changes & Errata](specification/changes.md): validator behaviour changes and how they affect published datasets.
