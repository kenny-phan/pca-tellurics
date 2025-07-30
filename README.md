# PCA Telluric Removal

Code based on M. Damiano, G. Micela, and G. Tinetti (2019). _[A Principal Component Analysis-based Method to Analyze High-resolution Spectroscopic Data on Exoplanets
](https://doi.org/10.3847/1538-4357/ab22b2)_

Originally developed for CRIRES+ data. Pipeline run time depends on the resolution and number of spectra and detectors in your dataset. For a dataset of 31 spectra and 14 detectors from CRIRES+, sampling to the optimal PCA components in the time-domain space takes 5-7 minutes. 

NOTE: This is close, but not exactly, how the code works as of 7/30/25. The code is structured as follows. All programs are .py files in the 'pcassie' folder. pipeline.py compiles the nessecary functions into one 'pipeline' function. The pipeline function optionally recalibrates the pixel-wavelength relation of the data spectrum to a telluric model from EsoSky (Noll et al. 2012, Jones et al. 2013), then will perform PCA subtraction on the data (from pca_subtraction.py) and cross-correlation with a user input simulated spectrum (from ccf.py). For the development of this codebase, I used MultiRex (Duque-Castaño et al. 2024), a straightforward implementation of TauRex (Al-Refaie et al. 2019). There are additional functions to inject the data with the simulated spectrum, create a S/N map, and perform a Welch's T-test in ccf.py.  

## Helpful Documents in order of relevance
Damiano (2018), Sec. 3.2, 5.3, 5.4, 5.5, 5.6. _[From space to ground (thesis)](https://discovery.ucl.ac.uk/id/eprint/10066066/7/Mario_Damiano_Thesis.pdf)_

Duque-Castaño et al. (2024). [Machine-assisted classification of potential biosignatures in Earth-like
exoplanets using low signal-to-noise ratio transmission spectra (MultiRex)](https://arxiv.org/pdf/2407.19167)

Kipping & Benneke (2025). _[Exoplaneteers Keep Overestimating Sigma Significances](https://arxiv.org/pdf/2506.05392)_

## Generally Helpful Links
[NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu/), helpful for exoplanetary parameters.

[ESO Exposure Time Calculator](https://www.eso.org/observing/etc/), helpful for identifying detectors on ESO instruments most affected by tellurics.

[ESO SkyCalc](https://www.eso.org/observing/etc/bin/gen/form?INS.MODE=swspectr+INS.NAME=SKYCALC), helpful to get a telluric model.
