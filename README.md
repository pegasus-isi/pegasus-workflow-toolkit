# Pegasus Workflow Toolkit

A reusable toolkit for creating [Pegasus WMS](https://pegasus.isi.edu/) workflows with [Claude Code](https://claude.ai/code). It provides custom slash commands (skills), copy-paste templates, and curated examples from production workflows.

## What's Included

### Custom Skills (Slash Commands)

| Skill | Purpose |
|-------|---------|
| `/pegasus-help` | Navigation — shows which skill to use |
| `/pegasus-scaffold` | Create a complete workflow project from a pipeline description |
| `/pegasus-wrapper` | Generate a wrapper script for a single pipeline step |
| `/pegasus-dockerfile` | Generate a Dockerfile for the workflow's tool stack |
| `/pegasus-convert` | Convert Snakemake/Nextflow to Pegasus |
| `/pegasus-debug` | Diagnose workflow failures from error messages |
| `/pegasus-review` | Review a workflow for common pitfalls |

### Templates (`pegasus-templates/`)

Copy-paste-and-customize starting points:

| Template | Description |
|----------|-------------|
| `workflow_generator_template.py` | Workflow generator class with all patterns annotated |
| `wrapper_template.py` | Python wrapper script (subprocess, API fetch, analysis) |
| `wrapper_template.sh` | Shell wrapper script (output flattening, headless) |
| `Dockerfile_template` | Three base image options (pip, micromamba, Ubuntu) |
| `README_template.md` | Standard README structure for workflows |
| `run_manual_template.sh` | Manual test script for local validation |

### Knowledge Base

| File | Description |
|------|-------------|
| `Pegasus.md` | 1200+ line guide covering all Pegasus concepts, patterns, and pitfalls |

### Examples (`examples/`)

Real workflow generators and scripts from production Pegasus workflows:

| Example | Pattern Demonstrated |
|---------|---------------------|
| `workflow_generator_tnseq.py` | Per-sample parallelism, fan-in merge, R/JAR support files |
| `workflow_generator_earthquake.py` | API data fetch, per-region loops, no input files |
| `workflow_generator_mag.py` | Shell wrappers, `is_stageable=False`, micromamba, `--test` mode, skip flags |
| `workflow_generator_soilmoisture.py` | ML train-then-predict, per-polygon parallelism |
| `workflow_generator_airquality.py` | Dual pipeline, skip flags, multiple data sources, environment secrets |
| `wrapper_python_example.py` | Python subprocess wrapper (UMI clipping with Java tool) |
| `wrapper_shell_example.sh` | Shell wrapper with output flattening (MEGAHIT assembly) |
| `Dockerfile_pip_example` | Lightweight pip-based container (data science stack) |
| `Dockerfile_micromamba_example` | Micromamba container (complex bioinformatics stack) |
| `run_manual_example.sh` | Manual test script with Docker support and colored output |

## Setup

### Prerequisites

- [Claude Code](https://claude.ai/code) CLI installed
- A working directory for your new workflow project

### Option A: Clone and Work Inside This Repo

```bash
git clone https://github.com/pegasus-isi/pegasus-workflow-toolkit.git
cd pegasus-workflow-toolkit
claude
```

Claude Code will automatically discover the skills from `.claude/skills/`. Type `/pegasus-help` to get started.

### Option B: Copy Skills Into Your Own Repo

```bash
# Copy the skills directory into your project
cp -r pegasus-workflow-toolkit/.claude/skills/pegasus-* your-project/.claude/skills/

# Copy the knowledge base and templates
cp pegasus-workflow-toolkit/Pegasus.md your-project/
cp -r pegasus-workflow-toolkit/pegasus-templates your-project/
cp -r pegasus-workflow-toolkit/examples your-project/
```

## Quick Start

1. Launch Claude Code in this directory
2. Type `/pegasus-scaffold`
3. Describe your pipeline (tools, data sources, processing steps)
4. Claude generates a complete workflow project with all files

## Example Workflow Repositories

These production workflows were built using this toolkit and serve as the reference patterns:

| Repository | Domain | Key Features |
|------------|--------|-------------|
| [pegasus-isi/tnseq-workflow](https://github.com/pegasus-isi/tnseq-workflow) | Bioinformatics | Per-sample parallelism, Snakemake conversion |
| [pegasus-isi/earthquake-workflow](https://github.com/pegasus-isi/earthquake-workflow) | Geoscience | API data fetch, multi-region analysis |
| [pegasus-isi/mag-workflow](https://github.com/pegasus-isi/mag-workflow) | Metagenomics | Shell wrappers, micromamba, test mode |
| [pegasus-isi/soilmoisture-workflow](https://github.com/pegasus-isi/soilmoisture-workflow) | Agriculture | ML training/inference pipeline |
| [pegasus-isi/airquality-workflow](https://github.com/pegasus-isi/airquality-workflow) | Environmental | Dual pipeline, multiple data sources |

## How It Works

The skills guide Claude through Pegasus-specific decisions by:

1. **Reading `Pegasus.md`** for concepts, patterns, and pitfalls
2. **Reading examples** from production workflows as reference patterns
3. **Asking targeted questions** about your pipeline (data sources, tools, parallelism)
4. **Generating files** from templates, customized for your specific use case
5. **Validating** the generated code against a checklist of common issues

## License

Apache 2.0
