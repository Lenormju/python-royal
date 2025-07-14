# Python Royal / Rambo Python

[![Project management: uv](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/uv/main/assets/badge/v0.json)](https://github.com/astral-sh/uv)
[![Code style & Static analysis: Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/ruff/main/assets/badge/v2.json)](https://github.com/astral-sh/ruff)
[![Type check: Mypy](https://www.mypy-lang.org/static/mypy_badge.svg)](https://mypy-lang.org/)
[![Pipeline status](https://gitlab.com/jgaffiot1/python-royal/badges/app-demo/pipeline.svg)](https://gitlab.com/jgaffiot1/python-royal/-/commits/app-demo)
[![Coverage report](https://gitlab.com/jgaffiot1/python-royal/badges/app-demo/coverage.svg)](https://gitlab.com/jgaffiot1/python-royal/-/commits/app-demo)
[![Latest release](https://gitlab.com/jgaffiot1/python-royal/-/badges/release.svg)](https://gitlab.com/jgaffiot1/python-royal/-/releases)

## Description

Sources for the EuroPython 2025 tutorial "Rambo Python".

## Objectives

Learn to write stylish and robust Python code! 

Python has a reputation for not being focused on software quality.
This was true 20 years ago, but since then, big names have been built on this
language: Instagram, Spotify, Reddit, Dropbox...
To achieve reliability, maintainability, scalability, and security (= the famous
Quality), you need to learn the language and its ecosystem. 

Let's discover together the structure of a Python project, the principles of the
language to respect, the tools to set up, and the practices to adopt to work
with Python with industrial quality.

## Prerequis

* Have the basics in Python
* Be able to install software on your machine (network access and rights)
* A shell
* If possible, a GitLab or GitHub account 

## Procedure

There are files for detecting X/gamma rays in this repository, let's display them!

- [ ] Fork the [GitLab project](https://gitlab.com/jgaffiot1/python-royal)
      or [GitHub project](https://github.com/Lenormju/python-royal) with your account
- [ ] Clone the fork on your own computer
- [ ] [Install `uv`](https://docs.astral.sh/uv/getting-started/installation/)
- [ ] Initialize a new project with `uv`
- [ ] Fill the `pyproject.toml`
- [ ] Add a dependency : [streamlit](https://streamlit.io/)
- [ ] Display the Streamlit "hello world"
- [ ] Add new dependencies : `pandas` and `plotly`
- [ ] Load a file and display its curve with Streamlit

And now, some tooling.

- [ ] Install `ruff`, `mypy`, and `pytest` as "dev" dependencies
- [ ] Format your code with `ruff`
- [ ] Analyze your code with `ruff`
- [ ] Check types with `mypy`
- [ ] Write a test with `pytest`
- [ ] Integrate these practices into your workflow with your IDE

Let's publish this code.

- [ ] Create a release and its tag on Git(Hub|Lab)
- [ ] Create a package (in "sdist" and "wheel" formats) with `uv`
- [ ] Integrate the tag into the package with `versioningit`
- [ ] Publish this code on the Git(Hub|Lab) package registry
- [ ] (Optional, build a Docker image containing the code and publish it)

Let's automate some of this.

- [ ] Check the code before committing with `pre-commit`
- [ ] Standardize the workflow with `doit` (or `make`)
- [ ] Launch automatic verification with GitLab CI / GitHub Actions

And anyway, let's document. 

- [ ] Install `sphinx` as dev dependencie
- [ ] Build the base of the documentation
- [ ] Extract docstrings and integrate them with `apidoc`

Continue the application as long as we can!

- [ ] Add a field to load a data file
- [ ] Extract the acquisition time and display the curves in impact/s
- [ ] Add a page to search for peaks on the curves
- [ ] Calibrate the curves in energy from reference curves (Na22, Cs137, Co60)
- [ ] Refactor by separating display, data reading, and processing
- [ ] Record the calibration values in the application state and use them for all curves
- [ ] Add an optional field to load a second file to subtract from the first
- [ ] Adjust the colors, add a logo (CSS optional)

## Data

The data comes from an X and gamma ray sensor (a more energetic version of
X-rays), used to measure the residual radioactivity of samples that we hope are
very pure, and therefore have very low radioactivity.

It works on a principle similar to solar panels, but instead of being exposed
to an astronomical amount of optical photons, it only receives an X or gamma
photon from time to time. The sensor therefore does not produce a continuous
current like a solar panel, but small peaks when an X or gamma photon happens
to hit it.

However, the sensor records these heights in a very, very raw way. It simply
counts the heights on a scale ranging from 1 to 16384. These are not even volts
or a unit of energy, just the number of channels of the analog-to-digital
converter, which encodes the heights on 14 bits (16384 = 2^14). Since the
sensor only counts impacts, we need to manually take into account the recording
time to know if the sample was slightly or very radioactive (how many impacts
per hour, for example?).

To recover the energy scale, we place known radioactive elements in front of
the sensor, so we know the energy of the peaks (keV = a unit of energy):

- Cobalt 60 (Co60) : 2 peaks at 1173.2 keV and 1332.5 keV
- Sodium 22 (Na22) : 2 peaks à 511 keV and 1274.5 keV
- Cesium 137 (CS137) : peak at 661.7 keV

Finally, X or gamma photons can come from the sample or the environment, which
is always slightly radioactive. To account for this, we need to subtract the
measurement of the sample's radioactivity from the measurement of the
environment's radioactivity, which we call the background noise. We have
measurements of two samples: "pmt" and "steel", and two background
noises: "bkg" and "bkg2".

To your keyboards!
