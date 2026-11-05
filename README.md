# Supplementary S2 Results and supporting material

Supporting material for *Reducing MILP Calls in Exact Pareto Enumeration through Lexicographic Objective Aggregation*.

Supplementary S1 code: **[GITHUB_SUPPLEMENTARY_S1_URL]**  
Supplementary S2: **[GITHUB_SUPPLEMENTARY_S2_URL]**

Start with **Supplementary_S2_Notes.docx**. The former supplementary sections are now **Notes 1–6**, to distinguish their numbering from the two repositories. The current manuscript cites these notes and the two repository links. Older documents and version labels retained inside provenance folders describe their original source snapshots.

## Primary records

| Cohort | Inputs | Runs | Completed | Time limited |
| --- | ---: | ---: | ---: | ---: |
| Main panel | 85 | 510 | 510 | 0 |
| Independent-reference twelve-city TSP | 1 | 6 | 2 | 4 |
| Fixed-budget inputs | 10 | 60 | 15 | 45 |
| Larger inputs | 6 | 36 | 6 | 30 |
| Total | 102 | 612 | 533 | 79 |

The methods use matching budgets within each method–worker pair. A time-limited point count records accepted nondominated images found by the common deadline. It does not claim complete-front enumeration. Oracle-stage optimality and completion of the whole enumeration are separate properties. Sensitivity repeats, archived errors, and software tests remain outside the 612 primary rows.

The 85 main-panel reference sets are supplied with the benchmark evidence. The extra TSP3-12-1 reference was generated independently by exhaustive C++ enumeration for this study, with 403 nondominated images. Complete independent reference fronts are not supplied for the fixed-budget and larger-input cohorts. Their checks include feasible binary witnesses, objective values, observed-set nondominance, and matching solution sets in completed method pairs.

## Contents

| Location | Contents |
| --- | --- |
| `Supplementary_S2_Notes.docx` | Notes 1–6 on times, repeats, pairing, fixed budgets, larger inputs, and implementation provenance |
| `tables/primary_runs.csv` | Unified index of 612 primary runs, status, counts, times, counters, hashes, and terminal paths |
| `tables/input_registry.csv` | JSON inputs and their immutable identities; original KP/AP text inputs are in the archived benchmark folders |
| `tables/01_...csv` through `09_...csv` | Frozen primary statistical analysis and sensitivity tables |
| `tables/11_FIXED_BUDGET_PAIRS.csv` | Readable method-paired view of the 60 fixed-budget records |
| `tables/12_LARGER_INPUT_PAIRS.csv` | Readable method-paired view of the 36 larger-input records |
| `tables/fixed_budget_*.csv` | Fixed-budget checkpoints, summaries, and separate repeat index |
| `records/main_panel/` | Original main-panel supporting data, audits, and repeat evidence |
| `records/fixed_budget/` | Fixed-budget inputs, terminals, journals, and checkpoints |
| `records/larger_inputs/` | Expanded larger-input archives, grouped by cohort |
| `archive_code_data/` | Data and metadata from the original code distribution; paired with S1 archived code for reconstruction |
| `figures/manuscript/` | Figure assets embedded in the supplied manuscript |
| `provenance/` | Source-to-publication mapping, source-manifest checks, software tests, primary audit, and original package metadata |

`time_s` in the unified table is a completion time for completed runs and an observation duration otherwise. Raw terminal and method labels remain separately recorded. Shutdown can add a small overhead to the nominal cap. Checkpoint tables report the scheduled budget observations. The four time-limited TSP3-12-1 terminals store their vectors in final journals, identified by `point_vectors_record_path`.

## Verification and reproduction

Place this directory beside `Supplementary_S1`, then follow the S1 README:

```bash
cd ../Supplementary_S1
python reproduce.py verify --results ../Supplementary_S2 --out ../../verification_output
python reproduce.py analyze --results ../Supplementary_S2 --out ../../analysis_output
```

Verification checks the complete file manifests and source-byte identities, all 612 selected terminal records, 516 reference-set comparisons, 265 completed method pairs, and 41,614 binary witnesses. Analysis regeneration must reproduce the nine archived CSV files exactly. Neither command performs optimization. Archived elapsed seconds are observations from their recorded execution environments; fresh runtimes vary.

Large text records use **lossless gzip** so that individual repository files remain manageable. Read `.json.gz` with Python `gzip.open(path, 'rt')`; Incomplete temporary write snapshots are listed in `provenance/omitted_transient_files.csv`; canonical terminal, checkpoint, and journal records are retained. Original source manifests and their successful verification reports are preserved.

AP p=4, n=30 is a synthetic derived input formed by adding a generated fourth objective to the official three-objective input.
