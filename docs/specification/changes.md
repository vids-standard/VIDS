# Changes & Errata

This page records changes to the VIDS validator and specification that adopters should be aware of. For the complete technical changelog, see [`CHANGES.md`](https://github.com/vids-standard/vids-standard/blob/main/CHANGES.md) in the standard repository.

## Validator v1.2.x — annotation-sidecar enforcement

!!! warning "Behavior change — a passing dataset may now fail"
    From validator **v1.2.0** (released 2026-05-21), a dataset carrying a `_bbox`, `_cls`, `_lm`, or `_roi` sidecar **without** `VIDSVersion` or a conformant `Provenance` block **passed under validator 1.1.x and fails under 1.2.x**.

**What changed.** Rules **A004** and **A005** were extended to check `VIDSVersion` and provenance completeness on *every* annotation sidecar, across all five spec-defined suffixes (`_seg`, `_bbox`, `_cls`, `_lm`, `_roi`). Earlier validators inspected only `*_seg.json`. Rules **A002** and **A003** were generalized to match.

**Why.** SPEC §10.1 has marked `VIDSVersion` and `Provenance` **REQUIRED** on every annotation sidecar since VIDS 1.0. Validator 1.2.0 expanded enforcement to match those existing requirements — a conformance correction for a previously under-enforced field, not a new requirement. The specification is authoritative; the validator implements it. See the erratum in [§15.3 Backward Compatibility](index.md#153-backward-compatibility).

**Who is affected.** Only datasets that were passing solely because an earlier validator did not inspect their non-segmentation sidecars. No published VIDS dataset is affected — LIDC-Hybrid-100 validates 21/21, and the IDRiD fundus reference implementation validates 15/21, under 1.2.1.

!!! tip "What to do"
    If you have datasets with `_bbox`, `_cls`, `_lm`, or `_roi` sidecars, make sure each sidecar includes:

    - `"VIDSVersion": "1.0"`, and
    - a `Provenance` block with `Annotator.ID` (or `Name`) and `AnnotationProcess.Date` (or `Tool`).

    Then re-run the [validator](../validator/index.md) to confirm. Datasets that already conform need no changes.

## Validator version history

| Version | Released | Notes |
|---------|----------|-------|
| 1.1.0 | 2026-03-28 | Initial public release |
| 1.1.1 | 2026-04-08 | Packaging-only update |
| 1.2.0 | 2026-05-21 | Annotation-sidecar enforcement widened to all five suffixes (see above) |
| 1.2.1 | 2026-06-09 | `D001` (`CHANGES.md`) scoped to the Full profile; current release |

The [online validator](../validator/online-validator.md) mirrors the current CLI release (`vids-validator` on PyPI). To pin a specific version, `pip install vids-validator==1.2.1`.
