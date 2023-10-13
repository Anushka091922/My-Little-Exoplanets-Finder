# My-Little-Exoplanets-Finder
# Exoplanet Finder: Unveiling New Worlds Beyond
The Exoplanet Finder project is a thrilling journey into the cosmos, driven by a passion for discovering new worlds beyond our own. By combining the power of data analysis and astronomical insights, this project is dedicated to identifying exoplanets – celestial bodies orbiting stars beyond our solar system. Here's a glimpse into the remarkable process:

## Detecting Exoplanets with Precision
### Step 1: Data Retrieval
The quest begins with the retrieval of astronomical data using specialized tools like Lightkurve. By pinpointing specific target stars or regions of interest, we gather valuable light curve data from missions like TESS.

### Step 2: Light Curve Analysis
The heart of the project lies in the analysis of light curves. We utilize techniques to isolate and study the minute variations in a star's brightness over time. These variations may hold the key to uncovering exoplanetary transits.

### Step 3: Stellar Variability Mitigation
To ensure the accuracy of our findings, we employ methods to mitigate stellar variability. This involves the removal of noise and anomalies caused by phenomena other than exoplanetary transits.

### Step 4: Periodogram Analysis
By subjecting our pre-processed light curves to periodogram analysis, we search for periodic signals that could indicate the presence of exoplanets. The periodogram reveals potential exoplanetary candidates.

### Step 5: Confirmation and Characterization
The most promising candidates undergo rigorous examination to confirm their exoplanetary nature. Additional data and analysis techniques help us characterize these newfound exoplanets, unveiling their properties and orbital dynamics.

## Technology at Our Disposal
Python: The primary programming language used for data retrieval, analysis, and visualization.
Lightkurve: A vital tool for working with astronomical time series data from missions like TESS.
NumPy and SciPy: Essential libraries for data manipulation and scientific computing.
Periodogram Analysis: Techniques like Box Least Squares (BLS) are employed for period detection.
Data Visualization: Matplotlib aids in creating informative plots and visualizations.
Stellar Variability Mitigation: Robust techniques are applied to remove noise from light curves.


Project:
lc.remove_nans().flatten(window_length=401).fold(period=3.5225).bin(binsize=10).plot();

![Screenshot 2023-10-13 234402](https://github.com/Anushka091922/My-Little-Exoplanets-Finder/assets/114327511/635ac94f-13d5-45e9-960d-54d29343c6a3)

import numpy as np
periodogram = flat_lc.to_periodogram(method="bls", period=np.arange(0.3, 10, 0.001))
periodogram.plot();

![Screenshot 2023-10-13 234549](https://github.com/Anushka091922/My-Little-Exoplanets-Finder/assets/114327511/5974a3a0-b718-4f56-a043-c356e5e5ba32)


best_fit_period = periodogram.period_at_max_power
print('Best fit period: {:.5f}'.format(best_fit_period))

Best fit period: 3.52200 d

In [ ]:
tpf = search_targetpixelfile('EPIC 212593538', campaign=6).download()
lc = tpf.to_lightcurve(aperture_mask='all')
lc.plot();
![Screenshot 2023-10-13 234608](https://github.com/Anushka091922/My-Little-Exoplanets-Finder/assets/114327511/202e4728-8864-4b66-a6ea-b83a8a9a48ef)

In [ ]:
from lightkurve import search_targetpixelfile
search_result = lk.search_targetpixelfile('Pi Mensae', mission='TESS', sector=1)
tpf = search_result.download(quality_bitmask='default')

In [ ]:
tpf.mission
tpf.targetid 

Out[ ]:
261136679
In [ ]:
tpf.plot(aperture_mask=tpf.pipeline_mask);

![Screenshot 2023-10-13 234625](https://github.com/Anushka091922/My-Little-Exoplanets-Finder/assets/114327511/808de74b-6d5f-4181-9dbe-9e5aaa2af462)

lc = tpf.to_lightcurve()
lc.scatter();
![Screenshot 2023-10-13 234640](https://github.com/Anushka091922/My-Little-Exoplanets-Finder/assets/114327511/69a94cdb-2520-43d7-9b35-bb117493a6e5)

