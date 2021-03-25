## NLP Project 

<p><img src="/images/businessbanner.webp" alt="Header"></p>

# Using Reviews to Predict Company Ratings
Authors: [Jiji Craynock](https://github.com/DataOnATangent)

<p align="center"><img width="360" height="300" src="/images/gdlogo.png" alt="glasdoor_logo"></p>


## Overview 
The process of finding a job is quite the undertaking with many factors to consider. Among the most important is deciding which companies to apply to in the first place. Ratings from current and former employees can play a key role in whether or not a candidate chooses to apply. However, these ratings come into question when you realize that often they can be incongruent with the written reviews left. In this project I attempt to close the gap using a translation of qualitative reviews into a quantitative metric that, when combined with machine learning can predict the review score currently available through sites like glassdoor. This will allow candidates and employees to be able to trust the simple ratings to a greater degree as they will be more reflective of the reviewer's true impression of the company. This may also help companies better understand what their trouble areas are since they maybe more nuanced than what the ratings currently indicate.

## Approach

### Project Roadmap:

1. **Data Aquisition:** Using a glassdoor webscraper developed by Matthew Chatham (sourced below), I scraped 14k+ reviews from 150 companies of various industries and ratings from the glassdoor site.

2. **Preprocessing & Exploratory Data Analysis:** My data contains to groups of features the text columns and non text columns. These were handled seperately in two different notebooks. 
    
    2a.The non text data was cleaned, recatagorized, and visualized in order to better understand some general characteristics about the reviewing such as the distribution of location, opnion of CEO, and outlook. 
    2b. The text columns were cleaned, and explored by rating to understand the make up of the text itself thru features like sentiment, average word count, and rating distribution. 

3. **Processing NLP:** Having a clean dataframe and having explored all the features, the next step was to prepare the text for modeling through NLP. This involved steps like removing stop words, removing punctuation, stemming, and vectorizing.

4. **Modeling:** Laslty, I tested several models in order to find the best fit for my data. 

### Models tested:

* KNN
* Decision Tree 
* Random Forests 
* XG Boosting 
* LGBM


## Findings

During the preprocessing stage it became immediately clear that the data had quite a bit of class imbalance among ratings. This imbalance was was also seen thruout the various categorical features.

<p align="center"><img src="/images/rating_dist_donut.png" alt="donut_chart"></p>

When looking a what the most popular word is 'helpfu' which might speak to what people are looking for in their work environment. 

<p align="center">
    <img src="/images/word_cloud_all.png" alt="word_cloud">
</p>

When looking at unique words, we can see that there is not much overlap between the reviews rated one, three, and five. This should help the models better distinguish between rating catagories.

<p align="center"> <img width="550" height="600" src="/images/venn.png" alt="venn_chart"></p>

Notably there was also a distinction in word count among rating groups. It seems the worse a company the more the employee had to see about it on average.

<p align="center"><img width="500" height="350" src="/images/avg_word_rating.png" alt="avg_word_chart"></p> 

## Conclusion and Next Steps

In the end my best model was XGBoost with 59% accuracy. This indicates it was able to accurately classify reviews 59% percent of the time. This indicates that machine learning could be a better way to score company reviews and this the overall company rating versus relying on a self reported score. For my next steps I will try to improve on my two best models using grid search to see if I can improve accuracy scores. I also hop to eventually look at deep learning techniques which I feel are more likely to perform better with this kind of data in general.


## Sources

Alll data was webscraped from Glassdoor.com. The webscraper used to acquire the data was originally built by [Matthew Chatham](https://github.com/MatthewChatham/glassdoor-review-scraper). The scraper is currently a bit out of date and was altered for the purpose of my project.

## Repository Structure
    
    ├── data                              Contains intial data files copies 
    ├── model_tests                       Contains original and resampled model testing noteboks    
    ├── modeling                          Contains notebook where models were ceated and tested
    ├── images                            Contains all images used
    ├── preprocessing_eda                 Contains the two notebooks used to preprocess and complete eda
    ├── presentation_deck                 Contains the presentation deck associated with this project
    ├── README.md                         ReadMe
    └── webscrape                         Contains the scraper, bashfile, and notebook used for the webscraping the reviews