# AnZeng__ATP: ATP Player Performance Analysis

An end-to-end data analysis pipeline for scraping, processing, and visualizing ATP tennis player performance using custom $\delta$ (delta) and $\alpha$ (alpha) metrics.

This project scrapes player data from the official ATP website, preprocesses it to calculate custom performance scores, and then runs a series of analyses to generate visualizations for:
* Grand Slam final performance (Winners vs. Losers)
* Player career trajectories (grouped by career length)
* Heatmaps of performance distribution
* Individual player performance-over-time scatter plots

---

## Project Structure

This project is composed of several key scripts, designed to be run in order.

### 1. Data Collection & Preprocessing

* `1_scrape_player_data.py`:  Reads a master list of players (`master_player_list.xlsx`) and scrapes the ATP website for their birthdates and full match histories. Saves one `.xlsx` file per player into `data/scraped_player_data/`.
* `2_preprocess_atp_data.py`: Reads the raw match history files from the scraper, processes them to calculate `Total Points` and `Performance Index` for each tournament, and saves the cleaned, summarized results into `data/processed_player_data/`.

### 2. Data Analysis & Visualization

* `grand_slam_final_analysis.py`: Loads all match data and generates boxplots (`delta_values_boxplot.eps`, `alpha_values_boxplot.eps`) comparing the $\delta$ and $\alpha$ metrics of Grand Slam final winners and losers.
* `analyze_career_trajectories.py`: Analyzes player performance over their careers. Generates plots (`career_groups_subplot.eps`, `career_trajectory_combined.eps`) showing the $(\delta, \alpha)$ trajectory grouped by career span (e.g., 0-10 years, 10-15 years).
* `plot_player_performance.py`: A utility script to generate a detailed scatter plot (`[Player_Name]_performance.eps`) for a single player's performance index over time.
* `generate_performance_heatmap.py`: Uses a 1-year rolling window to calculate metrics and generates a heatmap (`heatmap_max_performance_avg.eps`) showing the *average max performance* for each $(\delta, \alpha)$ bin.
* `generate_distribution_heatmap.py`: Similar to the other heatmap, but generates a *count-based* plot (`heatmap_distribution_count.eps`) showing the *number* of data points in each $(\delta, \alpha)$ bin.

---

## Installation

This project relies on several Python libraries. You can install them using `pip`:

```bash
pip install pandas numpy matplotlib seaborn openpyxl scipy tqdm DrissionPage
