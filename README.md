# Data Science Research: How does extracurricular involvement versus study effort affect students' exam grades?

## Project Overview

This project investigates the relationship between students' study effort, extracurricular involvement, and their academic performance. As university students divide their time between academics and extracurricular activities, a critical question arises: How does study effort actually impact one's academic performance, and do activities outside the classroom distract from or contribute to academic success?

Our hypothesis is that greater study effort leads to higher academic performance, while extracurricular involvement may present a time trade-off. We aim to move beyond mere correlation and conduct a Diagnostic Analysis to determine the mathematical nature of these impacts, investigating whether study effort provides constant linear returns or suffers from diminishing marginal returns.

## Data Sources

The analysis relies on three datasets sourced from Kaggle:
1.  **DS1: Student Performance Factors**
    * Dataset containing 6,608 records.
    * Variables include `Hours_Studied`, `Attendance`, `Tutoring_Sessions` (study effort indicators), `Extracurricular_Activities`, `Physical_Activity` (extracurricular indicators), and `Exam_Score`.
    * *Source: [Student Performance Factors (Kaggle)](https://www.kaggle.com/datasets/lainguyn123/student-performance-factors/data)*
2.  **DS2: Student Performance Predictions**
    * Synthetic dataset containing 1,000 records.
    * Variables include `StudyHoursPerWeek`, `AttendanceRate`, `ExtracurricularActivities`, `ParentalSupport`, and `FinalGrade`.
    * Used to check if patterns observed in DS1 apply to other dataset variations.
    * *Source: [Student Performance Predictions (Kaggle)](https://www.kaggle.com/datasets/haseebindata/student-performance-predictions)*
3.  **DS3: Student Habits vs Academic Performance**
    * Dataset containing 1,000 records.
    * Variables include `study_hours_per_day`, `attendance_percentage`, `extracurricular_participation`, and `exam_score`.
    * Used to test the sensitivity of our findings to specific methodological choices (e.g., using Min-Max scaling instead of Z-scores).
    * *Source: [Student Habits vs Academic Performance (Kaggle)](https://www.kaggle.com/datasets/jayaantanaath/student-habits-vs-academic-performance)*

## Methodology

### 1. Data Preparation & Exploration
* Loaded datasets using Pandas.
* Explored data distributions using `describe()` and visualized key factors using Seaborn and Matplotlib (histograms, etc.).
* Identified data quality issues (e.g., maximum exam score of 101 in DS1) to be addressed in the cleaning phase.
* Profiled missing values in the datasets (e.g., in DS2).

### 2. Feature Engineering & Composite Indices
To quantify the multiple factors into two main attributes for exploration, we constructed composite indices:
* **Study Effort Index:** A weighted sum of standardized variables like `Hours_Studied`, `Attendance`, `Tutoring_Sessions`, `Motivation_Level`, and `Peer_Influence`. Weights reflect semantic importance (e.g., Study Hours and Attendance have higher weights).
* **Extracurricular Participation Index:** A weighted sum of standardized variables like `Extracurricular_Activities` and `Physical_Activity`.
* **Standardization:** Applied Z-score standardization (for DS1 and DS2) and Min-Max scaling (for DS3) to ensure weights are applied to comparable scales.

### 3. Analysis & Modeling
* **Polynomial Regression:** Applied Polynomial Regression (degree=2) to the constructed indices to model the relationship and check for non-linear effects or diminishing returns.
* **Evaluation:** Evaluated models using standardized coefficients to interpret the impact of study effort, extracurricular participation, and their interactions on the predicted score.
* **Visualization:** Generated contour plots to visualize the predicted scores across different levels of study effort and extracurricular participation.

## Considerations & Limitations
* **Accuracy Risks:** The `Hours_Studied` variable is self-reported and susceptible to social desirability bias (Representation Failure), potentially leading to inaccuracies.
* **Data Privacy & Security:** The Kaggle datasets do not contain personally identifiable information (PII). However, synthetic and simulated datasets may still inherit structural patterns from real data.
* **Documentation:** Detailed logging of data transformations and proper citation of synthetic data generation methods are crucial for transparency and reproducibility.

## Repository Structure
* `Report.ipynb`: The main Jupyter Notebook containing the full data analysis, visualization, and modeling workflow.
* *(Add links or descriptions to other scripts or data files if present in your repository)*

## Author
* **Dai Jingxing** **Zhang Zexuan** **Fang Xinqin** - Nanyang Technological University (DSAI)
