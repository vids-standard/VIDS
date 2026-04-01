# Validator

The VIDS Validator is a zero-dependency Python tool that checks a dataset against all 21 VIDS compliance rules. It produces a binary PASS/FAIL determination — if any rule fails, the dataset is non-compliant.

---

## Installation

=== "pip (recommended)"

    ```bash
    pip install vids-validator
    ```

=== "From source"

    ```bash
    git clone https://github.com/vids-standard/vids-standard.git
    cd vids-standard
    pip install .
    ```

!!! info "Requirements"
    Python 3.8 or later. No external dependencies — the validator uses only the Python standard library.

---

## Verify Installation

```bash
vids-validate --help
```

Expected output:

```
usage: vids-validate [-h] [--profile {poc,full,auto}] [--json] [--output OUTPUT] dataset_root

VIDS 21-Rule Compliance Validator

positional arguments:
  dataset_root          Path to dataset root

options:
  -h, --help            show this help message and exit
  --profile {poc,full,auto}
                        Validation profile (default: auto-detect)
  --json                Output JSON
  --output OUTPUT       Write JSON report to file
```

---

## Usage Methods

The validator can be invoked three ways:

```bash
# CLI entry point (recommended)
vids-validate /path/to/dataset

# Module invocation
python -m vids_validator /path/to/dataset

# Direct script
python validate_vids.py /path/to/dataset
```

All three produce identical output.

---

## Next Steps

- [Quick Start →](quickstart.md) — validate your first dataset in 2 minutes
- [CLI Reference →](cli-reference.md) — all flags and output formats
