# VNL 2025: Advanced Performance Analytics & Tactical Modeling

## Project Overview
This repository contains a deep-dive Exploratory Data Analysis (EDA) of the 2025 Volleyball Nations League (VNL). The objective was to move beyond surface-level statistics to identify the true drivers of match outcomes, specifically focusing on offensive efficiency and service pressure.

By auditing the raw dataset, I identified a critical miscalculation in standard efficiency metrics caused by mislabeled "Attacking Attempt" data. This project documents the process of data validation, feature engineering, and the application of weighted statistical models to provide a standardized view of elite international performance.

## Technical Deep Dive & Key Insights

### 1. Data Integrity & The "True Attempt" Correction
During initial analysis, Hitting Percentages were yielding impossible values (including `inf` and results > 1.0). An audit revealed that the "Attacking Attempts" column only recorded "in-play" rallies, excluding Kills and Errors.
* **The Fix:** Engineered a `True_Total_Attempts` feature by aggregating `Kills + Attacking Errors + Attacking Attempts`.
* **The Impact:** This correction shifted team rankings significantly, revealing that high-volume teams like Poland actually led in efficiency despite lower "per-player" averages.

### 2. Positional Efficiency Variance
A comparative analysis across five distinct roles highlighted the specialized nature of international play:
* **Middle Blockers (.465 Hitting %):** Demonstrated elite efficiency as tactical options, scoring nearly 1 out of every 2 swings.
* **Pin Attackers (.296 - .321 Hitting %):** Showed lower efficiency but significantly higher volume, carrying the burden of out-of-system plays.



### 3. Serving Strategy: Risk vs. Reward
Using Ace-to-Error ratios, I segmented the league's serving profiles:
* **Aggressive/Risky:** High Ace Rate (>15%) and High Error Rate (>25%). Examples include Kai (JPN) and Leon (POL).
* **Tactical/Conservative:** Low Error Rate (<5%). Examples include Wang H.B. (CHN), focusing on stability and forcing long rallies.
* **The Age Factor:** Discovered a negative correlation between player age and error rates; younger players (18-21) average a 44.8% error rate compared to veteran players who prioritize tactical placement.

### 4. Statistical Methodology: Ratio of Totals
To prevent the "Average of Averages" bias—where a substitute with one kill can skew a team's efficiency—this project utilizes the **Ratio of Totals** method for all team and positional metrics:

$$
Team\ Efficiency = \frac{\sum Kills - \sum Errors}{\sum (Kills + Errors + InPlay)}
$$

## Technologies & Tools
* **Python Ecosystem:** Pandas for data wrangling, NumPy for mathematical modeling.
* **Visualization:** Matplotlib and Seaborn for distribution analysis and positional boxplots.
* **Jupyter:** Used for iterative development and documenting the analytical workflow.

## Repository Structure
* `vb_EDA.ipynb`: The primary analysis notebook containing all data cleaning and visualizations.
* `player_stats_data.csv`: The raw 2025 VNL dataset.

## Author
**Noah George**
* https://www.linkedin.com/in/noah-george05212006/
* https://github.com/Noahgeorge21
