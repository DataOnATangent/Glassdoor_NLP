## NLP Project 

<p><img src="/images/businessbanner.webp" alt="Header"></p>

# Using Reviews to Predict Company Ratings
Author: [Jiji Craynock](https://github.com/DataOnATangent)

<p align="center"><img width="360" height="300" src="/images/gdlogo.png" alt="glasdoor_logo"></p>


## Overview 
The process of finding a job is quite an undertaking with many factors to consider. Among the most important is deciding which companies to apply to in the first place. Ratings from current and former employees can play a key role in whether or not a candidate chooses to apply. However, these ratings come into question when you realize they often can be incongruent with the written reviews. In this project, I attempt to close the gap using a translation of qualitative reviews into a quantitative metric that, when combined with machine learning can predict the review score currently available through sites like glassdoor. This will allow candidates and employees to be able to trust the simple ratings to a greater degree as they will be more reflective of the reviewer's true impression of the company. This may also help companies better understand what their trouble areas are since they may be more nuanced than what the ratings currently indicate.

## Approach 

### Project Roadmap:

1. **Data Aquisition:** Using a glassdoor webscraper developed by Matthew Chatham (sourced below), I scraped 14k+ reviews from 150 companies of various industries and ratings from the glassdoor site.

2. **Preprocessing & Exploratory Data Analysis:** My data contains two groups of features, the text columns and non text columns. These were handled seperately in two different notebooks. 
    
    2a.The non text data was cleaned, recatagorized, and visualized in order to better understand some general characteristics about the reviewing such as the distribution of location, opinion of CEO, and outlook. 
    
    2b. The text columns were cleaned, and explored by rating to understand the make up of the text itself through features like sentiment, average word count, and rating distribution. 

3. **Processing NLP:** Having a clean dataframe and having explored all the features, the next step was to prepare the text for modeling through NLP. This involved steps like removing stop words, removing punctuation, stemming, and vectorizing.

4. **Modeling:** Laslty, I tested several models in order to find the best fit for my data. 

### Models tested:

* KNN
* Decision Tree 
* Random Forests 
* XG Boosting 
* LGBM


## Findings

During the preprocessing stage it became immediately clear that the data had quite a bit of class imbalance among ratings. Out of 14,896 reviews 46% were 5 star ratings with every subsequent class being around half of the previous. This imbalance was was also seen thruout various categorical features.

<p align="center"><img width="400" height="350" src="/images/rd_donut.png" alt="donut_chart"></p>

Looking at the most common words we see that ‘helpfu’ appears as the most popular word across all reviews indicating that reviews spoke a good amount about what they did and did not find helpful. 

<p align="center">
    <img width="800" height="500" src="/images/word_cloud_all.png" alt="word_cloud">
</p> 

Turning our attention to some of the other ratings provided we can see here that despite rating things like work/life balance, managements, culture, etc. one way this ratings were not highly correlated with the overall rating given.  

<p align="center">
    <img width="400" height="250" src="/images/removed_col.png" alt="removed_columns_correlation_chart">
</p> 

When looking at unique words, we can see that there is not much overlap between the reviews rated one, three, and five. This should help the models better distinguish between rating catagories.

<p align="center"> <img width="250" height="400" src="/images/vennu.png" alt="venn_chart"></p>

Additionally, when looking at average words it becomes clear that the reviews tied to lower ratings where substantially longer than the reviews with higher ratings, indicating that the worse an employees experience, the more they had to say about it.   

<p align="center"><img width="400" height="250" src="/images/aw_rating.png" alt="avg_word_chart"></p>  

## Modeling

For the modeling process 5 models were tested including decision tree, random forest, xgboost, knn, and light gbm. Amount the best performing were KNN with 46% accuracy and Random Forest, and Light GBM. With with 58% accuracy. After performing a few grid searches he best overall model was xgboost with 59% accuracy across 5 classes.    

  <p align="center"><img src="/images/conf_mtrx_gs.png" alt="confusion_matrices"></p>  

## Conclusion and Next Steps

In the end, my models show that classification are viable way to derive rating from reviews people leave rather than relying on users to choose a rating that is truly representative of how they feel about their employers. In future iterations of this project I hope to increase my sample size to better balance the classes as well as try out some deep learning models.


## Sources

Alll data was webscraped from [Glassdoor.com](https://glassdoor.com). The webscraper used to acquire the data was originally built by [Matthew Chatham](https://github.com/MatthewChatham/glassdoor-review-scraper). The scraper is currently a bit out of date and was altered for the purpose of my project.

## Repository Structure
    
    ├── data                              Contains intial data files copies 
    ├── model_tests                       Contains original and resampled model testing noteboks    
    ├── modeling                          Contains notebook where models were ceated and tested
    ├── images                            Contains all images used
    ├── preprocessing_eda                 Contains the two notebooks used to preprocess and complete eda
    ├── presentation_deck                 Contains the presentation deck associated with this project
    ├── README.md                         ReadMe
    └── webscrape                         Contains the scraper, bashfile, and notebook used for the webscraping the reviews