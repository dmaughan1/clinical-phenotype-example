# Clinical Phenotype Example — Hypertension

A small, independent example project built with the packaged
[`@oml/clinical-phenotype-project`](https://github.com/dmaughan1/clinical-phenotype-project)
methodology, which it installs as a dependency. It models a synthetic **essential hypertension**
phenotype: four intended criteria, three computable criteria, four clinical concepts, two datasets,
and a couple of synthetic patients.

This repository contains **no copy of the methodology source**. The vocabulary, the Markdown editor
templates, and the `phenotype-report` generator are all resolved from the installed package under
`deps/`.

## Setup

1. Make sure the methodology package is in your local registry: start the registry (the `verdaccio`
   helper repo) and publish `@oml/clinical-phenotype-project@0.2.0` to it.
2. Install the dependency into this repository:
   ```bash
   oml install -r http://localhost:4873
   ```
   It is installed into `deps/@oml/clinical-phenotype-project/`.

## Use

From the command line:

```bash
oml start
oml lint
oml reason
oml validate
oml codegen -c phenotypeReport
oml stop
```

`oml codegen -c phenotypeReport` uses the generator that ships with the methodology package and
writes `build/docs/Phenotype-Readiness.md` for the hypertension phenotype.

The authoring notebooks in `src/md/Hypertension/Authoring/` (`Intent.md`, `Realization.md`,
`Terminology.md`, `Datasets.md`, `Adjudication.md`) compose the methodology's installed editor
templates and target the description ontologies in `src/oml/example.org/htn/description/`. Open them
in OML Code to add or edit model elements through the table editors.

## Layout

```
.oml/settings.yml                     dependency + render config
src/oml/example.org/htn/
    description/{data,terminology,definition,cohort,bundle}.oml
    codegen.oml                       binds the installed generator to this model
src/md/Hypertension/Authoring/*.md    pages composing the installed editor templates
```
