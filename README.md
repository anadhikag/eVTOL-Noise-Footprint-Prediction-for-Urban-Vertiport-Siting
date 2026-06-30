Data Source (real):
NASA ANOPP (Aircraft Noise Prediction Program) output examples available in research papers. - https://ntrs.nasa.gov/api/citations/19970005047/downloads/19970005047.pdf
Eurocontrol Noise Model data for helicopters (similar to eVTOL). Simulation: Use spherical spreading directivity + ground attenuation.  - https://www.researchgate.net/publication/361272520_Generation_of_noise_exposure_contours_for_eVTOL_aircraft_including_transition
Modified Assignment:
Part A-Noise Propagation Physics

Simulate: Source level Lw= 95 dBA at 1m. Spherical loss: Lp= Lw-20log10(d) -8-ad (a=0.005 dB/m air absorption). Compute at distances 50-500m. Add directivity (+3 dB in climb direction).

Part B-Spatial Interpolation
Generate 50 random measurement points (angle, distance) with added Gaussian noise (±2 dB). Use Inverse Distance Weighting to create 20 contour map (100x100 grid). Use scipy, interpolate.

Part C-Population Exposure

Overlay dummy residential grid: population density 5000/(km²) near city center, decreasing outward. Compute number of people exposed >55 dBA

Part D-Siting Recommendation
Three candidate sites with different population densities and background noise.
Choose best.
Where to find real acoustic data:
Search "Helicopter noise measuremerits FAA" - many CSV files available.

Simulation code for Part B:
python
from scipy.interpolate import RBF Interpolator
coordinates of 50 measurement points
rhf RBFInterpolator(xy points, noise valves)
grid.x, grid ymp.ngrid[0:500:100), 8:50:13
