# Validation Attestation

A VIDS Validation Attestation is the signed artifact issued for datasets that achieve a successful PASS on the VIDS Reference Validator at the specified Profile. It is the document a vendor attaches to a dataset delivery and a buyer forwards internally as proof of acceptance, supported by the underlying machine-readable Validation Report.

## Issuance control

VIDS Validation Attestations are issued by approved evaluation operators following successful validation using the VIDS Reference Validator. Princeton Medical Systems is the current sole operator.

**Self-issued attestations, attestations issued by parties other than approved operators, or attestations modified after issuance do not constitute VIDS validation.** Buyers receiving an attestation from an unrecognized issuer should request the underlying `validation_report.json` and re-run the Reference Validator independently to verify the result.

## Sample attestation

Below is a worked example showing what a VIDS Validation Attestation looks like for the [LIDC-Hybrid-100 reference dataset](https://doi.org/10.5281/zenodo.19582717){target="_blank" rel="noopener"} — the publicly available 21/21 PASS dataset that demonstrates Full Profile compliance.

---

<div style="border: 2px solid #1F3864; padding: 2em; margin: 2em 0; background: #FAFAFA;">

<h3 style="text-align: center; color: #1F3864; margin-top: 0;">VIDS</h3>
<h4 style="text-align: center; color: #1F3864; font-weight: normal; margin-top: -1em;">Validation Attestation</h4>

<hr style="border-top: 2px solid #1F3864;">

| | |
|---|---|
| **Dataset** | LIDC-Hybrid-100 |
| **Version** | 1.0.0 |
| **Provider** | Princeton Medical Systems |
| **Date of Validation** | 12 April 2026 |
| **VIDS Profile** | Full |
| **VIDS Version** | 1.0 |
| **Validator** | VIDS Reference Validator v1.1 |
| **Validation Artifact** | `validation_report.json` (attached) |

<p style="text-align: center; color: #4A4A4A; font-weight: bold; margin-top: 2em;">VALIDATION RESULT</p>

<p style="text-align: center; color: #2E7D32; font-size: 3em; font-weight: bold; margin: 0;">PASS</p>

<p style="text-align: center; color: #4A4A4A; font-style: italic;">21 / 21 rules passed at the Full profile</p>

<hr style="border-top: 1px solid #1F3864;">

<p><strong>Scope of Validation</strong></p>
<p>This attestation confirms that the dataset structure, metadata, annotation provenance, and quality documentation meet all requirements defined under the VIDS Full profile at the time of validation.</p>

<p><strong>Conditions</strong></p>
<ul>
<li>This validation applies only to the dataset version specified above.</li>
<li>Any modification to dataset contents or structure invalidates this attestation.</li>
<li>This attestation does not assess the clinical correctness of annotations.</li>
<li>Verification: re-run the VIDS Reference Validator on the dataset to reproduce this result.</li>
</ul>

<hr style="border-top: 1px solid #1F3864;">

<p style="color: #4A4A4A; font-size: 0.9em; margin-bottom: 0;">Issued by</p>
<p style="color: #1F3864; font-weight: bold; margin-top: 0.2em;">Princeton Medical Systems</p>
<p style="color: #4A4A4A; font-size: 0.9em;">info@princetonmedicalsystems.com &nbsp;•&nbsp; https://vidsstandard.org</p>

</div>

---

## What is on the attestation

A VIDS Validation Attestation carries seven identifying fields:

- **Dataset name and version** — identifies the exact dataset to which the attestation applies. A new version requires a new attestation.
- **Provider** — the organization delivering the dataset.
- **Date of validation** — when the validator was run.
- **VIDS Profile** — POC (15 rules) or Full (21 rules).
- **VIDS Version** — currently 1.0.
- **Validator and version** — the specific tool used. Future re-validations against newer validator versions may produce different results.
- **Validation Artifact** — the `validation_report.json` file that supports the attestation. Always attached or referenced.

## How buyers use the attestation

When a vendor delivers a dataset under a contract that includes the [VIDS Reference Procurement Language](sow-addendum.md), the attestation accompanies the delivery as evidence of compliance. The buyer's acceptance process is:

1. Receive the dataset, the attestation, and the supporting `validation_report.json`.
2. Independently re-run the VIDS Reference Validator on the delivered dataset.
3. Confirm that the buyer's re-validation produces the same result reported on the attestation.
4. If results match, accept the delivery. If results differ, treat as a failed validation and trigger the remediation clause in the SOW.

The attestation is only as authoritative as the underlying validator output. Buyers should always verify rather than trust on face value.

## When an attestation is invalidated

The attestation ceases to apply if any of the following occurs:

- The dataset is modified in any way (additions, removals, restructuring, metadata changes).
- A new VIDS Specification version introduces breaking changes that the dataset has not been re-validated against.
- An error is later discovered in the validator that would have changed the original PASS result.

In each case, a new validation must be performed and a new attestation issued for the modified dataset version.

## Related

- [Compliance Evaluation](evaluation.md) — diagnostic assessment for datasets that have not yet achieved PASS
- [Scoring Rubric](scoring-rubric.md) — the criteria that underlie validator rules
- [Reference Procurement Language](sow-addendum.md) — contract clauses that require attestation delivery as a condition of acceptance
- [VIDS Reference Validator](https://github.com/vids-standard/vids-standard){target="_blank" rel="noopener"} — the open-source tool that produces the underlying validation result
