# FPL-Metric-Analysis
## Overview

The **FPL Metric Analysis** project was created to determine which metrics are most effective for selecting players in Fantasy Premier League (FPL). There is a long-standing debate among FPL managers over the importance of fixture difficulty versus individual performance metrics such as recent form, expected goals (xG), expected assists (xA), and the composite ICT index. This project compares these metrics to identify which ones provide the best insights when deciding on players for your team.

## Live Dashboard

You can view the interactive Tableau dashboard showcasing the analysis here:  
[**View the FPL Metric Analysis Dashboard**](https://public.tableau.com/your_dashboard_link)  
*(Replace the URL above with your actual Tableau Public link.)*

## Data Collection

Data for this project was collected directly from the official FPL API endpoints:

- **Bootstrap Static Endpoint:**  
  `https://fantasy.premierleague.com/api/bootstrap-static/`  
  This endpoint provided overall player and team data, including pricing, basic statistics, and fixture difficulty ratings.

- **Player Element Summary Endpoint:**  
  `https://fantasy.premierleague.com/api/element-summary/{player_id}/`  
  This endpoint was used to collect detailed historical performance data for each player, such as gameweek points, xG, xA, minutes played, and more.

## Data Cleaning and Preparation

The raw API data was processed using Python and pandas with the following key steps:

- **Conversion and Parsing:**  
  - API responses were converted into pandas DataFrames.
  - Numeric fields (e.g., `expected_goals`, `expected_assists`) were explicitly converted to numeric values using `pd.to_numeric()` to ensure accurate calculations.
  
- **Filtering:**  
  - Players with fewer than 180 minutes played were excluded to ensure that only reliable, consistent data was analyzed.
  - The "Manager" position was removed to focus solely on the FPL players.

- **Metric Calculations:**  
  - **Form:** Calculated as the average total points over the last 6 fixtures.
  - **Expected Goals (xG) and Expected Assists (xA):** Computed for both the last 6 fixtures (short-term form) and for the entire season (total expected performance).
  - **Gameweek Aggregations:** Total points and minutes played were aggregated over various gameweek ranges (e.g., 1–6, 7–12, 13–18).
  - **Fixture Difficulty Ratings (FDR):** Integrated by merging team-level FDR data with player performance data.
  - **ICT Index:** Included as an additional metric to gauge overall player impact.

## Analysis and Conclusions

**Key Insights:**

- **Individual Metrics vs. Fixture Difficulty:**  
  The analysis revealed that fixture difficulty rarely has a meaningful connection to how much a player scores. In many cases, standout players score consistently well even when facing tougher fixtures. As a result, individual metrics like recent form and xG/xA are generally better predictors of performance.

- **The Role of xG/xA and Form:**  
  Both short-term (last 6 games) and season-long calculations of xG and xA provide critical insight into a player's expected contributions, often aligning closely with their actual performance. Recent form further refines this insight, helping to identify in-form players.

- **ICT Index:**  
  The ICT index, as a composite metric, also demonstrated value in assessing player impact, supporting its use as part of a balanced metric approach.

**Conclusions:**

- A data-driven approach that emphasizes **individual performance metrics**—such as form, xG, and xA—is more reliable than relying solely on fixture difficulty.
- Standout players often maintain high performance even in challenging fixtures, so a focus on personal metrics (and complementary composite metrics like ICT) yields better decision-making insights.
- Combining season-long data with short-term trends allows for a nuanced understanding of player performance, supporting more informed team selection.

## Project Files

This repository includes:
- **Python Scripts:** Code for data collection, cleaning, and metric calculations (backend work).
- **Excel Files:** Processed data used for analysis.
- **Tableau Dashboard:** The final interactive dashboard is available on Tableau Public via the link above.

*Note: The project files are provided as a reference to show the backend process. The live interactive experience is available on Tableau Public.*

## Future Enhancements

- Integrate additional advanced metrics (e.g., points per 90 minutes, cost efficiency).
- Extend the analysis with predictive modeling or simulation-based optimization.
- Enhance the Tableau dashboard with further filters and dynamic visualizations for real-time insights.

## Contact

For any questions or feedback, please contact me at ajvelu7@gmail.com.
