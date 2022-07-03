# Vine Bias Analysis

## Overview of Analysis

The purpose of this analysis was to review the paid Amazon Vine Program and determine if there is a bias inherent in the program. The data was publically available data sourced from AWS at [this url]("https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt")

There were 50 separate datasets available to review. The dataset utilized in this analysis was the "Video Games" dataset, which can be found at the following [hyperlink.](https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Video_Games_v1_00.tsv.gz)

The ETL process was used to extract and transform the data, which was then loaded to a connected pgAdmin database. Then additional review was conducted on the data using PySpark within Google Colab.

## Results

The "Video Game" dataset was transformed to only consider reviews that had 20 or more "helpful reviews" at least 50% of the time. This was done to avoid any downstream mathematical issues and to ensure the data population encompassed reviews that had the most impact.

The reviews were then split between "paid" and "unpaid" reviews."Paid" reviews are reviews that were supported by the Amazon Vine Program. While "unpaid" reviews were any review meeting the above criteria completed by the typical user. The results for both are below:

**Paid Reviews**

![alt text](https://github.com/sever1sd/Amazon_Vine_Analysis/blob/bed85c7c947d22496c90d9a49b93044e1327952d/Resources/Images/Paid_Reviews.png)

<ins>Paid Notes<ins>
* Paid reviews accounted for 94 of the total selected population
* Of those 94 reviews, 48 reviews had a 5 star rating
* Which results in a positive review of ~51%.

**Unpaid Reviews**

![alt text](https://github.com/sever1sd/Amazon_Vine_Analysis/blob/bed85c7c947d22496c90d9a49b93044e1327952d/Resources/Images/Unpaid_Reviews.png)

<ins>Unpaid Notes<ins>
* Unpaid reviews had a substantially higher overall count of 40,471 reviews. 
* Of those reviews, 15,663 had a 5 star rating
* Which results in a positive review percentage of ~39%.

## Summary

Reviewing the analysis above, it seems clear that there is a strong bias toward positive reviews when the reviewer is apart of the paid Amazon Vine Program. This is because the overall percentage of 5 star reviews in relation to the total number of views for paid vs. unpaid reviews is substiantally higher for paid reviews than unpaid reviews. This results in a positivity bias for paid reviews specifically. Notably, the population of unpaid reviews seems to be significantly larger than paid reviews. This could result in a skewing of the results. Additional analysis of each of the databases should be conducted to determine if this potential postivity bias is ubiquitous across all categories or if it is a phenomenon unique to the Video Game dataset. To further determine if there is truly a positivity bias inherent in the Amazon Vine Program, statistical analysis -- such as t-tests -- could be used to determine if the difference in reviews is statistically significant.
