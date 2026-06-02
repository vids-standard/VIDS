# Online Validator

Validate your VIDS dataset directly in the browser. **No installation required. Your data never leaves your browser.**

Drag and drop a `.zip` archive of your VIDS dataset to check all 21 validation rules instantly.

!!! note "For larger datasets, use the CLI"
    The browser validator runs entirely in your browser, which caps usable dataset size at what the browser can hold in memory. For production clinical datasets, install the CLI validator (`pip install vids-validator`) instead. Same 21 rules, no memory constraints.

    See the [CLI Reference](cli-reference.md) for usage.

<iframe src="../online.html" width="100%" height="900px" frameborder="0" style="border: 1px solid #e0e0e0; border-radius: 8px;"></iframe>
