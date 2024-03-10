# AppleStore-Analysis


## Project Overview

This data analysis project aims to provide insight into the top rated apps. By analayzing ratings data, we seek to identify trends and make data-driven recommendations to help guide marketing strategy for a new developer.

We will be able to answer key questions, such as:

- What app categories are most popular?
- What price should the app be set to?
- How can user ratings be maximized?

### Data Sources
Mobile App Statistics (Apple iOS app store)
The ever-changing mobile landscape is a challenging space to navigate. . The percentage of mobile over desktop is only increasing. Android holds about 53.2% of the smartphone market, while iOS is 43%. To get more people to download your app, you need to make sure they can easily find your app. Mobile app analytics is a great way to understand the existing strategy to drive growth and retention of future user.

With million of apps around nowadays, the following data set has become very key to getting top trending apps in iOS app store. This data set contains more than 7000 Apple iOS mobile application details. The data was extracted from the iTunes Search API at the Apple Inc website. R and linux web scraping tools were used for this study.

### Tools
- SQL - Data Analysis

### Exploratory Data Analysis

EDA involved exploring the app data to understand the characteristics of the data, structure, and reveals issue in the dataset. These issues can include missing values and outliers. 

In the initial data EDA phase, we performerd the following tasks:

- Check for any missing values in key fields
- Find out the number of apps per genre
- Get an overview of the apps' ratings

### Data Analysis
  
  (Some interesting code/features worked with)

``` SQL  
--Determine wether paid apps have higher ratings than free apps

SELECT CASE
		WHEN price > 0 THEN 'Paid'
		ELSE 'Free'
	END AS App_Type,
	AVG(user_rating) AS Avg_Rating
FROM AppleStore
GROUP BY 
    CASE
        WHEN price > 0 THEN 'Paid'
        ELSE 'Free'
    END;

--Check if apps with more supported languages have higher ratings

SELECT CASE
		WHEN LEN(app_desc) < 500 THEN 'Short'
		WHEN LEN(app_desc) BETWEEN 500 AND 1000 THEN 'Medium'
		ELSE 'Long'
	END AS description_length_bucket,
	AVG(user_rating) AS average_rating
FROM AppleStore as A
JOIN appleStore_description_combined AS b
ON a.id = b.id
```

### Results/Findings

The analysis results are summarized as follow:
1. Apps with longer descriptions have higher ratings
2. Paid apps have higher ratings
3. Apps with more languages supported have higher ratings

### Recommendations

Based on the analysis, we recommend the following actions:
- Charge for the app to ensure better quality
- Offer more language support
- Give as much detail possible when describing the app
- Build an app in an unsaturated market 


### References

1.  [Kaggle Dataset](https://www.kaggle.com/datasets/ramamet4/app-store-apple-data-set-10k-apps)
2.  [Lore So What](https://www.youtube.com/watch?v=EKOWoInn46A&t=790s)     
