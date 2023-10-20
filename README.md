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
### Python: 
The primary programming language used for data retrieval, analysis, and visualization.
### Lightkurve:
A vital tool for working with astronomical time series data from missions like TESS.
### NumPy and SciPy:
Essential libraries for data manipulation and scientific computing.
### Periodogram Analysis: 
Techniques like Box Least Squares (BLS) are employed for period detection.
### Data Visualization:
Matplotlib aids in creating informative plots and visualizations.
### Stellar Variability Mitigation:
Robust techniques are applied to remove noise from light curves.


 We'll combine the individual frames into a lightcurve # Aperture masks make the image look better for analysis lc = pixelFile.to_lightcurve(aperture_mask=pixelFile.pipeline_mask) lc.plot() # We may find it easier to spot the pattern if we flatten the curve flat_lc = lc.flatten() flat_lc.plot() # Phase-fold the light curve to verify that the period and transit time # correspond to the transit signal # This puts the frequency spikes on top of each other if we get the period right folded_lc = flat_lc.fold(period=3.5225) folded_lc.plot() # How to discover the correct period? # Use a periodogram to show all the repetitive patterns in usr graph # Gives us the most likely candidate period = np.linspace(1, 5, 10000) # BLS = Box Least Squares bls = lc.to_periodogram(method='bls', period=period, frequency_factor=500) bls.plot() # Period value corresponding to the highest peak in the periodogram planet_x_period = bls.period_at_max_power planet_x_t0 = bls.transit_time_at_max_power planet_x_dur = bls.duration_at_max_power # Folding can yield a lot of information about the planet # The depth can tell us about the size, etc ax = lc.fold(period=planet_x_period, epoch_time=planet_x_t0).scatter() ax.set_xlim(-2,2) print(planet_x_period) print(planet_x_t0) print(planet_x_dur)
3.522652265226523 d
353.60132485035285
0.1 d












