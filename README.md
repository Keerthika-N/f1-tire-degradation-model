# Formula 1 Comparative Tire Degradation Model 
**An end-to-end data analytics project modeling time-series telemetry from the 2024 Abu Dhabi Grand Prix using Python, Pandas, and NumPy.**

## Project Overview 
In Formula 1 racing, tire management is the ultimate diffrentior between winning and losing. This project extracts high-frequency lap data using the `FastF1` API to construct a statistical regression model that quantifies and compares the tire degradation rates of Scuderia Ferrari teammates Charles Leclerc and Carlos Sainz during their opening race stints in 2024 at Abu Dhabi Grand Prix.

## Key Analytical Insights
* **The Strategic Delta:** While Charles Leclerc exhibited a standard linear degradation curve, Carlos Sainz maintained a near-zero slope baseline pace. This mathematically demonstrates elite tire management where Sainz's conservation techniques perfectly offset the mechanical grip loss as fuel weight decreased.
* **Environmental Noise:** Residual variance analysis highlights significantly higher lap-time volatility for Sainz, capturing the physical realities of operating within a DRS train and navigating aerodynamic "dirty air" traffic compared to Leclerc’s clean-air stint.

## Final Visualization
Below is the optimized performance model mapping driver stint consistency against mathematical linear trends:
<img width="932" height="547" alt="image" src="https://github.com/user-attachments/assets/8c6df750-3f39-4819-a884-f020968cd035" />

## Challenges
1. **Race-Start Outlier Filtering:** Initial race-start congestion and heavy-fuel formation laps caused massive spikes (>113s) in early time-series data. Implemented a filtering threshold to remove laps above 95 seconds to isolate true racing pace.
2. **In-Lap Anomaly Removal:** Pit lane deceleration loops artificially inflate the final lap time of a stint. Isolated and dropped in-laps to ensure the linear regression (`np.polyfit`) captured pure rubber degradation rather than operational pit-stop noise.
3. **API Pipeline Resilience:** Handled upstream live-timing server dropouts and connection timeouts by configuring explicit local caching mechanisms (`fastf1.Cache`), ensuring local runtime stability despite fluctuating external network endpoints.

## Techical Stack 
* **Language:** Python
* **Data Libraries:** Pandas (Time-delta processing, feature slicing), NumPy (Polynomial regression modeling)
* **Visualization:** Matplotlib (Custom thematic styling, data-point alpha blending, multi-series overlays)
* **Data Source:** FastF1 API (Official F1 Live Timing Client)
