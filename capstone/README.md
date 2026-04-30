### Project Title

**Author** Harish Ramakrishnan

### Executive Summary
This project aims to build a personalized recommendation system for an e-commerce platform. Using exploratory data analysis (EDA), matrix factorization, and user clustering, the project evaluates whether segment-aware, personalized models can meaningfully outperform non-personalized, popularity-based baselines to improve user engagement and sales. 

### Rationale
Today, most e-commerce platforms show every customer the same “top sellers” or “trending now” lists, which leads to missed sales, disengaged customers, and higher churn. Tailoring recommendations to individual behavior allows businesses to capture lost revenue, improve click-through rates, and enhance the overall user experience.

### Research Question
*“Can a personalized recommendation system, built using collaborative filtering and customer segmentation, meaningfully outperform a non-personalized baseline in predicting the next best product for e-commerce users and which user segments benefit most from personalization?”* 

### Data Sources
The dataset is sourced from [Kaggle](https://www.kaggle.com/datasets/alfarisbachmid/personalized-recommendation-systems-dataset) and contains 150,000 user interaction records. It includes 5,000 unique users and 2,000 products. Key features include User ID, Item ID, Item Category, User Rating (1.0-5.0), Interaction Timestamp, Item Price, Platform (Web, Mobile App, Smart TV, Tablet), and Continent-level Location.

### Methodology
1. **Exploratory Data Analysis & Cleaning:** Handling missing values, removing duplicates, feature extraction from timestamps, and identifying outliers in pricing.
2. **Visualizations:** Distribution analysis of user ratings, platforms, and categories to understand platform usage and price sensitivity.
3. **Baseline Modeling:** A Linear Regression model is established as a non-personalized baseline to predict user ratings based on contextual features (price, platform, category).
4. **Advanced Modeling (Next Steps):** Implementing Funk SVD/Matrix Factorization for collaborative filtering, K-Means clustering for user segmentation, and Gradient Boosting for refined rating prediction.

### Results
* EDA revealed the distribution of item prices and identified categorical trends across distinct platforms (Web vs. Mobile App vs. Smart TV). 
* A baseline Linear Regression model was developed to predict user ratings, setting an initial Root Mean Squared Error (RMSE) to evaluate the upcoming collaborative filtering model against.

### Next Steps
* Implement **Funk SVD and Matrix Factorization** to generate personalized product recommendations.
* Apply **K-Means clustering** to discover 3-5 distinct behavioral segments (e.g., price-sensitive browsers vs. loyal buyers).
* Train a **Gradient Boosting** model to predict ratings and compare its performance to the baseline Linear Regression model.

### Outline of Project
* [Project EDA Link](https://github.com/Harish7882/UCB_ML_CLASS/blob/main/capstone/harish_capstone_recommendation.ipynb)

### Contact and Further Information
For further information, please contact Harish Ramakrishnan or visit the GitHub repository.
