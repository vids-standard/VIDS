# CLI Reference

## Command

```
vids-validate <dataset_root> [options]
```

## Arguments

| Argument | Required | Description |
|----------|----------|-------------|
| `dataset_root` | Yes | Path to the VIDS dataset root directory |

## Options

| Option | Values | Default | Description |
|--------|--------|---------|-------------|
| `--profile` | `poc`, `full`, `auto` | `auto` | Validation profile. `auto` reads the `.vids` marker file. |
| `--json` | — | off | Output the full report as JSON to stdout |
| `--output` | file path | — | Write JSON report to the specified file (also prints human-readable summary) |
| `-h`, `--help` | — | — | Show help message |

## Exit Codes

| Code | Meaning |
|------|---------|
| `0` | Validation passed (zero FAIL rules) |
| `1` | Validation failed (one or more FAIL rules), or dataset path not found |

## Profile Detection

When `--profile auto` (the default), the validator reads the `.vids` marker file at the dataset root:

```text
profile: poc
vids_version: 1.0
```

- If the file contains `full`, Full profile rules are enforced (all 21 rules).
- If the file contains `poc` or is ambiguous, POC profile rules are enforced (15 rules; Q* and M* rules are skipped).
- If the `.vids` file is missing, the validator defaults to POC and reports S001 as FAIL.

## Output Formats

### Human-Readable (default)

```bash
vids-validate /path/to/dataset
```

Prints a formatted report with status icons, rule-by-rule results, and a summary.

### JSON

```bash
vids-validate /path/to/dataset --json
```

Outputs a JSON object with the following top-level fields:

| Field | Type | Description |
|-------|------|-------------|
| `VIDSVersion` | string | VIDS specification version (`"1.0"`) |
| `ValidatorVersion` | string | Validator version (`"1.1"`) |
| `DatasetPath` | string | Absolute path to the validated dataset |
| `Profile` | string | Profile used (`"poc"` or `"full"`) |
| `ValidationDate` | string | ISO 8601 UTC timestamp |
| `Summary` | object | Counts of passed, failed, warned, skipped rules and overall status |
| `Results` | array | Per-rule results with `rule`, `status`, and `message` |
| `Errors` | array | List of error messages (FAIL rules) |
| `Warnings` | array | List of warning messages (WARN rules) |

### JSON to File

```bash
vids-validate /path/to/dataset --output report.json
```

Writes the JSON report to the specified file and prints the human-readable summary to the console.

## Rules Reference

The validator enforces 21 rules organized into 6 categories:

| Category | Rules | Profiles |
|----------|-------|----------|
| Structure | S001–S006 | All |
| Imaging | I001–I004 | All |
| Annotation | A001–A005 | All |
| Quality | Q001–Q003 | Full only |
| ML | M001–M002 | Full only |
| Metadata | D001 | All (WARN only) |

See [Validation Rules](../specification/validation-rules.md) for detailed descriptions of each rule.

## Examples

```bash
# Basic validation with auto-detected profile
vids-validate ./lung-nodule-ct-100

# Force Full profile validation
vids-validate ./lung-nodule-ct-100 --profile full

# JSON output for CI pipeline
vids-validate ./lung-nodule-ct-100 --json

# Save report and view summary
vids-validate ./lung-nodule-ct-100 --output validation-report.json

# Python module invocation
python -m vids_validator ./lung-nodule-ct-100 --profile poc
```
