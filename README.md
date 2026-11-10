# California Solar Generation and Grid CO₂ Intensity

Final project for my Computing for Climate course at Columbia University.

## Question
California has dramatically increased its share of solar generation since 2014. Does the relationship between solar energy share and grid CO₂ intensity weaken in winter, when solar output is lower?

My hypothesis was that the regression slope between solar share and CO₂ intensity would be weaker in winter than in summer, because lower solar output increases the need for backup fossil fuel generation.

## Data
- EIA monthly state-level electricity generation by energy source (eia.gov/electricity/data.php)
- CAISO monthly historical CO₂ emissions (caiso.com/todays-outlook/emissions)

The analysis covers 144 months from January 2014 to December 2025. CAISO manages about 80% of California's grid while the EIA data covers the whole state, so the CO₂ intensity values are an approximation.

## Methods
- Calculated monthly solar share as solar generation divided by total generation (EIA)
- Calculated monthly CO₂ intensity as CAISO emissions divided by total generation
- Fit a separate ordinary least squares regression for each season, with the OLS function written by hand in NumPy, including p-values and 95% confidence intervals on the slopes
- Compared slopes between winter (December to February) and summer (June to August)
- Checked residuals over time and re-ran the winter and summer slopes with an expanding window of years

## Key findings
- The hypothesis was not supported. The winter slope (-0.77) was slightly steeper than the summer slope (-0.73), and the 95% confidence intervals overlapped for all four seasons.
- The fit is noisier in winter, with an R² of 0.54 compared with 0.83 in summer.
- In the expanding window analysis, summer had the steeper slope in earlier years. The two lines converged and crossed in later years, so the relationship is not stable over time. One possible explanation is the build-out of battery storage and grid infrastructure, which I did not test directly.

## Files
- `Final Computing Project.ipynb` contains the full analysis and figures
- To run it, download the EIA and CAISO data from the links above and place them in the same folder as the notebook, with the file names used in the notebook

## Tools
Python, pandas, NumPy, SciPy, Matplotlib
