# Clustering Analysis of Student Habits and Mental Health

## Overview

This project performs a clustering analysis on a dataset of student habits and mental health ratings to identify distinct groups or profiles of students based on their behaviors. The analysis involves data preparation, dimensionality reduction using Principal Component Analysis (PCA), determining the optimal number of clusters, applying K-Means clustering, and visualizing the results.

## Project Structure

## Data

The dataset I used for this analysis (<https://www.kaggle.com/datasets/jayaantanaath/student-habits-vs-academic-performance>) contains information on student study hours per day, social media hours, Netflix consumption, sleep hours, exercise frequency, and mental health ratings. The original dataset also included numeric variables such as age, attendance percentage, and exam scores. However, for this particular analysis, I focused on the six variables directly related to student habits and mental health. Age and exam scores were not directly included in the clustering but could be relevant for further analysis of the identified student profiles.

## Analysis

I performed the analysis using the R programming language and several key packages: `tidyverse` for data manipulation, `ggplot2` for visualization, `cluster` for clustering algorithms, `factoextra` for clustering analysis and PCA visualization, and `car` for checking multicollinearity.

The `Clustering student Habits.Rmd` file contains the complete analysis, which includes the following steps:

1.  **Data Loading and Preparation:** load the dataset and selected the following six numeric variables for clustering: `study_hours_per_day`, `social_media_hours`, `netflix_hours`, `sleep_hours`, `exercise_frequency`, and `mental_health_rating`. My primary research goal was to identify student profiles based on their daily habits and self-reported mental well-being, and these six variables directly address this focus. I then scaled the data to ensure each variable contributed equally to the distance calculations in the clustering algorithm.

2.  **Exploratory Data Analysis:** I generated histograms to examine the distributions of the scaled variables.

3.  **Checking for Multicollinearity:** I calculated Variance Inflation Factors (VIF) for the six selected variables to assess the level of multicollinearity. The low VIF values indicated that multicollinearity was not a significant issue.

4.  **Principal Component Analysis (PCA):** Performed PCA on the scaled data to reduce dimensionality and to facilitate visualization. The first four principal components explained approximately 85% of the total variance and were used for the K-Means clustering. The first two principal components were used for visualization.

5.  **Determining the Number of Clusters:** Using the Elbow Method, implemented using the `factoextra` package on the first four principal components, which suggested an optimal number of clusters (k) of 4.

6.  **K-Means Clustering:** Applying the K-Means algorithm to the first four principal components with the determined number of clusters (k=4). The `nstart` parameter was set to 10 to ensure a robust solution by running the algorithm with multiple random initializations.

7.  **Visualization of Clusters:** Visualized the resulting clusters in the 2D space of the first two principal components using the `fviz_cluster` function from `factoextra`. Confidence ellipses were added to represent the spread of each cluster. Additionally, variable loadings from the PCA were overlaid on the scatter plot to help interpret the clusters in terms of the original variables.

8.  **Interpretation of Clusters:** Based on the PCA loadings and the centroids of the four clusters in the PCA space, I identified the following behavioral profiles:

    -   **Cluster 1:** Characterized by higher mental health ratings and higher exercise frequency, potentially with higher study hours and more sleep.
    -   **Cluster 2:** Characterized by lower mental health ratings and lower exercise frequency, potentially with higher study hours and more sleep.
    -   **Cluster 3:** Characterized by higher mental health ratings and lower exercise frequency, potentially with lower study hours and less sleep.
    -   **Cluster 4:** Characterized by lower mental health ratings and higher exercise frequency, potentially with lower study hours and less sleep.

## Methodological Rationale

In this section, I will detail the key methodological choices made during the clustering analysis.

### Variable Selection for Clustering

I selected the following six numeric variables for clustering: `study_hours_per_day`, `social_media_hours`, `netflix_hours`, `sleep_hours`, `exercise_frequency`, and `mental_health_rating`. This was driven by my primary research goal of identifying student profiles based on their daily habits and self-reported mental well-being. These variables are conceptually linked to daily behaviors and psychological state, allowing for the identification of holistic behavioral patterns. I chose not to include `age` as it's a demographic characteristic, and including it might group students primarily by age. Similarly, I excluded `exam_score` as it's an outcome variable that could be influenced by habits, and including it might lead to clusters based on academic performance rather than the habits themselves.

### Scaling of Data

I scaled the selected numeric variables before applying PCA and K-Means to ensure that variables with larger original ranges did not disproportionately influence the cluster assignments.

### Principal Component Analysis (PCA)

I employed PCA to reduce the dimensionality of the data and to facilitate visualization. I used the first four principal components for K-Means clustering, as they captured approximately 85% of the variance. The first two principal components were used for visualization.

### Determining the Number of Clusters (Elbow Method)

I used the Elbow Method on the first four principal components, which suggested that k=4 was the optimal number of clusters.

### K-Means Clustering Algorithm

I applied the K-Means algorithm with k=4 and `nstart = 10` to ensure a robust clustering solution.

### Visualization and Interpretation

I visualized the resulting clusters using `fviz_cluster` on the first two principal components, (confidence ellipses and overlaid variable loadings to aid interpretation) could be implemented.

## Running the Analysis

To reproduce this analysis, please ensure you have R and RStudio installed. Install the necessary packages by running `install.packages(c("tidyverse", "ggplot2", "cluster", "factoextra", "car", "knitr"))` in the R console. Place your data file (named `your_student_data.csv` or your actual filename) in the same directory as the `student_clustering.Rmd` file. Open the R Markdown file in RStudio and click "Knit" to generate the analysis report.

## Findings

My clustering analysis identified four distinct groups of students based on their reported habits and mental health. These profiles suggest different patterns of well-being and lifestyle choices within the student population.
