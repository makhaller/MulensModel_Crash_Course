### MulensModel Crash Course

A beginner-friendly exploration of MulensModel, a Python package for modeling gravitational microlensing events.

This repository documents my initial familiarization with MulensModel and its application to microlensing (with exoplanets). It progresses from installing and testing the package to working with real data and comparing different physical microlensing models.

## My Contribution and Use of AI

This project is based on tutorial code from the official MulensModel documentation. I located the relevant tutorials, selected and organized the examples, and debugged and tested the notebooks to confirm that they ran correctly.

I used ChatGPT to help write and adapt parts of the code, troubleshoot errors, and generate line-by-line comments and explanations. The code is commented on heavily for my own benefit so that I can follow each step and better understand how the models, parameters, and functions work. I reviewed the generated code and explanations, tested the notebooks, and made changes where needed. The underlying examples and scientific methods come from the cited MulensModel tutorials.

## Purpose and scope

The notebooks in this repository replicate and go into depth about examples from the official MulensModel documentation using published datasets and model parameters.

The goal is to understand:

- how microlensing observations are stored and plotted;

- how theoretical light curves are calculated;

- how models are compared with telescope measurements;

- how chi-squared and residuals are used to evaluate a fit;

- how a planetary binary-lens model can improve upon a single-lens model;

- how finite-source effects and annual parallax enter microlensing analyses.

This repository is a learning project, not an independent exoplanet-discovery analysis! 

## Notebooks

1) Install_and_Import_MulensModel.ipynb

Introduces the initial setup process:

- Installing MulensModel;

- Importing the package;

- Checking the installed version;

- Creating a basic point-source, point-lens model;

- Plotting a theoretical microlensing light curve.

2) MulensModel_Real_Data_Crash_Course.ipynb

Uses real microlensing observations to demonstrate:

- Loading and inspecting telescope data with MulensData.

- Fitting a point-source, point-lens model with SciPy.

- Comparing a one-lens model with a star + planet binary-lens model.

- Combining data from several telescopes and examining finite-source effects.

- Comparing models with and without annual microlensing parallax.

The notebook also introduces the main MulensModel objects:

- MulensData: stores observation times, brightness measurements, and uncertainties.

- Model: stores physical microlensing parameters and calculates magnification.

- Event: connects a model to one or more observational datasets.

- Event.get_chi2(): evaluates the disagreement between a model and the data.

## Installation

Download or clone this repository, then install the required packages:

pip install -r requirements.txt

Open Jupyter:

jupyter notebook

Run the notebooks in numerical order.

The notebooks use MulensModel version 3.11.0. You can confirm the installed version with:

import MulensModel as mm

print(mm.__version__)

## Example data

The real-data notebook uses observational files distributed with the MulensModel source release. A setup cell downloads the data directory that matches the installed MulensModel version and stores it locally beside the notebook.

The downloaded data directory is intentionally not included in this repository!

## Sources and Development of the Code

The links below were the main reference materials provided to ChatGPT while developing this crash course. They supplied the example datasets, published model parameters, and the main MulensModel methods demonstrated in the notebooks. However, they are not the direct source of every line of code in this repository.

The crash-course notebooks contain more code than appears on the linked pages because ChatGPT helped combine, adapt, and expand the examples into a single instructional notebook. Additional code was written to organize the examples, load and check files, display intermediate results, compare models, calculate or present fit statistics, create plots, and make the notebook easier to run one section at a time. 

Therefore, the linked sources should be understood as the scientific and technical starting points for the project rather than as line-by-line sources for the complete notebook. Some code follows or adapts the official examples, while other portions were generated or reorganized with ChatGPT based on those examples and my requests. I reviewed and tested the notebook, but AI assistance was used in writing both the code and its explanations.

## Real-data examples and sources

OGLE-2008-BLG-092 / OB08092

Used for loading real photometry and fitting a point-source, point-lens model.

MulensModel fitting tutorial:https://rpoleski.github.io/MulensModel/tutorial_fit_pspl.html

OGLE event page:https://ogle.astrouw.edu.pl/cont/4_main/epl/ob08092/

OGLE-2003-BLG-235 / MOA-2003-BLG-53

Used to compare a single-lens model with a planetary binary-lens model. The official tutorial states that the example photometry came from the NASAExoplanet Archive.

MulensModel tutorial:https://rpoleski.github.io/MulensModel/tutorial.html

MOA-2008-BLG-310

Used to demonstrate observations from multiple telescopes and finite-source effects. The official example attributes the data and model parameters to Janczak et al. (2010), The Astrophysical Journal, 711, 731.

Official MulensModel example:https://github.com/rpoleski/MulensModel/blob/master/examples/example_05_MB08310.py

OGLE-2005-BLG-086

Used to compare a point-lens model without annual parallax with two parallax solutions.

MulensModel annual-parallax tutorial:https://rpoleski.github.io/MulensModel/tutorial_fit_pi_E.html

## Important interpretation notes

The published planetary and higher-order model parameters used in these examples are supplied as inputs from the cited tutorials. The notebook demonstrates how MulensModel evaluates those models; it does not independently recover every published parameter! 

A lower chi-squared generally indicates a better match to the observations, but a complete scientific detection also requires consideration of model complexity, alternative explanations, parameter degeneracies, observational systematics, and physical plausibility! 

