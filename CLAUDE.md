# CLAUDE.md

This repository is the **Pegasus Workflow Toolkit** — a set of Claude Code skills, templates, and examples for creating [Pegasus WMS](https://pegasus.isi.edu/) workflows.

## Repository Structure

```
.claude/skills/          # 7 custom slash commands for Pegasus workflow development
pegasus-templates/       # Copy-paste-and-customize starting points for all file types
examples/                # Curated reference files from 5 production Pegasus workflows
Pegasus.md               # Comprehensive Pegasus development guide (knowledge base)
```

## Key Files

| File | Role |
|------|------|
| `Pegasus.md` | Knowledge base — all skills read this first for concepts, patterns, and pitfalls |
| `pegasus-templates/workflow_generator_template.py` | Starting point for new workflow generators |
| `examples/workflow_generator_tnseq.py` | Best example of per-sample parallelism, fan-in merge |
| `examples/workflow_generator_earthquake.py` | Best example of API fetch + region loops |
| `examples/workflow_generator_mag.py` | Best example of shell wrappers, `is_stageable=False`, micromamba, `--test` mode |
| `examples/workflow_generator_soilmoisture.py` | Best example of ML train-then-predict |
| `examples/workflow_generator_airquality.py` | Most feature-rich (dual pipeline, skip flags, multiple data sources) |

## Available Skills

Users invoke these via slash commands:

- `/pegasus-help` — Navigation: shows which skill to use
- `/pegasus-scaffold` — Create a complete workflow project from a pipeline description
- `/pegasus-wrapper` — Generate a wrapper script for a single pipeline step
- `/pegasus-dockerfile` — Generate a Dockerfile for the workflow's tool stack
- `/pegasus-convert` — Convert Snakemake/Nextflow to Pegasus
- `/pegasus-debug` — Diagnose workflow failures from error messages
- `/pegasus-review` — Review a workflow for common pitfalls

## Workflow Pattern Reference

| Pattern | Example Workflow |
|---------|-----------------|
| Per-sample parallelism | tnseq |
| API data fetch (no input files) | earthquake |
| Shell wrappers with output flattening | mag |
| `is_stageable=False` (container-embedded scripts) | mag |
| `--test` mode with auto-download | mag |
| Skip flags for conditional DAG | mag, airquality |
| ML train-then-predict (hub-and-spoke) | soilmoisture |
| Per-region/location loops | earthquake, soilmoisture, airquality |
| Fan-in merge / aggregation | tnseq, airquality |
| Dual pipeline architecture | airquality |
| Multiple data sources | airquality |
| Environment variable secrets | airquality |
| Micromamba container | mag |
| Per-tool resource dictionary | mag, earthquake |

## Public Workflow Repositories

The examples in this repo are excerpted from these public repositories:

- https://github.com/pegasus-isi/tnseq-workflow
- https://github.com/pegasus-isi/earthquake-workflow
- https://github.com/pegasus-isi/mag-workflow
- https://github.com/pegasus-isi/soilmoisture-workflow
- https://github.com/pegasus-isi/airquality-workflow
