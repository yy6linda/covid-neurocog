# Investigating new-onset neurocognitive complications in COVID-19 patients

<!-- usage note: edit the H1 title above to personalize the manuscript -->

[![HTML Manuscript](https://img.shields.io/badge/manuscript-HTML-blue.svg)](https://jaybee84.github.io/covid-neurocog/)
[![PDF Manuscript](https://img.shields.io/badge/manuscript-PDF-blue.svg)](https://jaybee84.github.io/covid-neurocog/manuscript.pdf)
[![GitHub Actions Status](https://github.com/jaybee84/covid-neurocog/workflows/Manubot/badge.svg)](https://github.com/jaybee84/covid-neurocog/actions)
[![Travis Build Status](https://travis-ci.com/jaybee84/covid-neurocog.svg?branch=main)](https://travis-ci.com/jaybee84/covid-neurocog)
<!-- usage note: delete CI badges above for services not used by your manuscript -->

## Introduction and Rationale
The physiological impact of the newly identified Coronavirus disease 2019 (COVID-19) on various segments of the population has been divergent. While some COVID-positive patients have developed serious pulmonary complications, others have shown relatively mild pulmonary symptoms. Whether the pulmonary symptoms are the only effect of COVID-19 on the human body is still under investigation. 

Recent studies in the UK and Spain have noted that a notable percentage of patients showed significant impact to the central nervous system1,2. Whether these impacts only affected the patients in the short term, or if they have longer term consequences is still not well understood. According to the data collected through a portal set up in the early stages of the pandemic in the UK, 62% of tracked patients showed the presence of a cerebrovascular event3. More notably, a higher fraction of younger patients showed altered mental status compared to cerebrovascular events, suggesting a possible predisposition of the younger population towards the neurocognitive effects. Altered mental status was the second most common symptom often occurring in younger patients. Identification of such cases in the UK was fuelled by the ABN RADAR portal and the situation continues to be monitored 4,5 . 

Recent reports suggest that neurological complications of COVID-19 also exist in the US population and may be at a higher prevalence than seen in Europe6–8. While this has been systematically studied in Europe where the arrival of the virus predated that in the US, there remains a need to examine the prevalence of these patterns in the US population in greater detail. Moreover, neuropsychiatric effects can cause long term changes in the quality of life of the patients and their caregivers. Thus early identification of clinical features that may be predictive of such effects in US patients is critical.
We plan to use machine learning and other computational methods to identify features that may be predictive of the new-onset neurocognitive complications in people who tested positive for COVID-19. We expect this population to be relatively small, and thus will identify and implement computational methods that are specifically robust towards rare outcomes9. This project will lay the foundation to preemptively identify and monitor above mentioned neurocognitive complications due to COVID-19 and assist patients in receiving appropriate and necessary prophylactic care.

## Objectives
Is there an association between COVID-19 (various severity levels) and new onset neurocognitive dysfunction? 
What are some clinical and demographic features that are predictive of COVID-19 related new onset neurocognitive changes?
Are there factors that make these specific populations more vulnerable than the general population?

## Analytical Plan
 
### Aim 1: 
Is there an association between COVID-19 (various severity levels) and new onset neurocognitive dysfunction? While various neurocognitive effects have been reported in relation to the COVID-19 pandemic, there is a need to understand effects caused by the unusual life changes due to the social restrictions of the pandemic and those caused by biological interventions of the virus. To address this aim, we will first define the phenotypes of “COVID19 related new onset neurocognitive dysfunction” using longitudinal health record data. Additionally we will use various clinical features to perform causal inference analysis to determine validity of the defined phenotypes.

### Aim 2: 
What are some clinical and demographic features that are predictive of COVID19 related new onset neurocognitive changes? New onset neuro-cognitive changes in COVID-19 positive individuals with no prior neurocognitive history may require active monitoring or follow up to understand their short and long term effects. Identifying factors that may indicate increased risk of a population of healthy individuals towards conditions that may become chronic if not treated promptly, can help direct prophylactic help towards these populations. We expect the population of such vulnerability to be quite sparse. We will implement machine learning methods that robust towards small imbalanced datasets, providing valuable insights while reducing the risk of misinterpretation when implemented on sparse datasets. Our goal is to find features that can predict a probability score or likelihood of risk for a new patient so that they can be directed to prophylactic treatment as soon as possible.

### Aim 3: 
Are there factors that make these specific populations more vulnerable than the general population? Generalizability of the features identified in any analysis is key for establishing good practices for practical implementation. To understand how the features identified in the N3C cohort may generalize in other populations, we will compare summary statistics from the identified experimental and population in the N3C COVID cohort with summary statistics from other population level cohorts like AllofUs, and global.health. We will then examine whether the features or trends identified in the N3C cohort are recapitulated independently in the other cohorts.



## Manuscript description

<!-- usage note: edit this section. -->

This repository is a template manuscript (a.k.a. rootstock).
Actual manuscript instances will clone this repository (see [`SETUP.md`](SETUP.md)) and replace this paragraph with a description of their manuscript.

## Manubot

<!-- usage note: do not edit this section -->

Manubot is a system for writing scholarly manuscripts via GitHub.
Manubot automates citations and references, versions manuscripts using git, and enables collaborative writing via GitHub.
An [overview manuscript](https://greenelab.github.io/meta-review/ "Open collaborative writing with Manubot") presents the benefits of collaborative writing with Manubot and its unique features.
The [rootstock repository](https://git.io/fhQH1) is a general purpose template for creating new Manubot instances, as detailed in [`SETUP.md`](SETUP.md).
See [`USAGE.md`](USAGE.md) for documentation how to write a manuscript.

Please open [an issue](https://git.io/fhQHM) for questions related to Manubot usage, bug reports, or general inquiries.

### Repository directories & files

The directories are as follows:

+ [`content`](content) contains the manuscript source, which includes markdown files as well as inputs for citations and references.
  See [`USAGE.md`](USAGE.md) for more information.
+ [`output`](output) contains the outputs (generated files) from Manubot including the resulting manuscripts.
  You should not edit these files manually, because they will get overwritten.
+ [`webpage`](webpage) is a directory meant to be rendered as a static webpage for viewing the HTML manuscript.
+ [`build`](build) contains commands and tools for building the manuscript.
+ [`ci`](ci) contains files necessary for deployment via continuous integration.

### Local execution

The easiest way to run Manubot is to use [continuous integration](#continuous-integration) to rebuild the manuscript when the content changes.
If you want to build a Manubot manuscript locally, install the [conda](https://conda.io) environment as described in [`build`](build).
Then, you can build the manuscript on POSIX systems by running the following commands from this root directory.

```sh
# Activate the manubot conda environment (assumes conda version >= 4.4)
conda activate manubot

# Build the manuscript, saving outputs to the output directory
bash build/build.sh

# At this point, the HTML & PDF outputs will have been created. The remaining
# commands are for serving the webpage to view the HTML manuscript locally.
# This is required to view local images in the HTML output.

# Configure the webpage directory
manubot webpage

# You can now open the manuscript webpage/index.html in a web browser.
# Alternatively, open a local webserver at http://localhost:8000/ with the
# following commands.
cd webpage
python -m http.server
```

Sometimes it's helpful to monitor the content directory and automatically rebuild the manuscript when a change is detected.
The following command, while running, will trigger both the `build.sh` script and `manubot webpage` command upon content changes:

```sh
bash build/autobuild.sh
```

### Continuous Integration

Whenever a pull request is opened, CI (continuous integration) will test whether the changes break the build process to generate a formatted manuscript.
The build process aims to detect common errors, such as invalid citations.
If your pull request build fails, see the CI logs for the cause of failure and revise your pull request accordingly.

When a commit to the `main` branch occurs (for example, when a pull request is merged), CI builds the manuscript and writes the results to the [`gh-pages`](https://github.com/jaybee84/covid-neurocog/tree/gh-pages) and [`output`](https://github.com/jaybee84/covid-neurocog/tree/output) branches.
The `gh-pages` branch uses [GitHub Pages](https://pages.github.com/) to host the following URLs:

+ **HTML manuscript** at https://jaybee84.github.io/covid-neurocog/
+ **PDF manuscript** at https://jaybee84.github.io/covid-neurocog/manuscript.pdf

For continuous integration configuration details, see [`.github/workflows/manubot.yaml`](.github/workflows/manubot.yaml) if using GitHub Actions or [`.travis.yml`](.travis.yml) if using Travis CI.

## License

<!--
usage note: edit this section to change the license of your manuscript or source code changes to this repository.
We encourage users to openly license their manuscripts, which is the default as specified below.
-->

[![License: CC BY 4.0](https://img.shields.io/badge/License%20All-CC%20BY%204.0-lightgrey.svg)](http://creativecommons.org/licenses/by/4.0/)
[![License: CC0 1.0](https://img.shields.io/badge/License%20Parts-CC0%201.0-lightgrey.svg)](https://creativecommons.org/publicdomain/zero/1.0/)

Except when noted otherwise, the entirety of this repository is licensed under a CC BY 4.0 License ([`LICENSE.md`](LICENSE.md)), which allows reuse with attribution.
Please attribute by linking to https://github.com/jaybee84/covid-neurocog.

Since CC BY is not ideal for code and data, certain repository components are also released under the CC0 1.0 public domain dedication ([`LICENSE-CC0.md`](LICENSE-CC0.md)).
All files matched by the following glob patterns are dual licensed under CC BY 4.0 and CC0 1.0:

+ `*.sh`
+ `*.py`
+ `*.yml` / `*.yaml`
+ `*.json`
+ `*.bib`
+ `*.tsv`
+ `.gitignore`

All other files are only available under CC BY 4.0, including:

+ `*.md`
+ `*.html`
+ `*.pdf`
+ `*.docx`

Please open [an issue](https://github.com/jaybee84/covid-neurocog/issues) for any question related to licensing.
