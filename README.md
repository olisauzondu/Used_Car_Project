# Developing a Recommendation and Price Prediction System for Used Cars on Craigslist
A quantitative study comprising used car sales data scrapped from all over the United States between April to May of 2021.

## TABLE OF CONTENTS
 - Summary
 - Objective
 - Data Collection
 - Data Cleansing
 - Exploratory Data Analysis
 - Recommendation System
 - Data Modeling (price prediction)
 - Insights
 - Conclusion
 - Challenges and Future Work
## SUMMARY
The market for used cars has seen growth over the years. During the pandemic, about 61% of car buyers prefered to buy from a dealership.

Over time, the recorded data has shown that the total auto sale of second-hand vehicles has increased two-fold when compared to new car sales in the US

With the number available used vehicles out there, buyers are faced with an abundance of options to choose from. This analysis seeks to understand the historical preferences of buyers and how that can be leveraged to improve the craigslist algorithm to assist buyers and seller alike.

## OBJECTIVE
To improve used car sales listed on craigslist by creating a recommender system to show buyers similar listings to the one they currently view
To create a price prediction model to assist buyers and sellers on a ballpark price to expect for specific models and features
## DATA COLLECTION
The used car data was scraped and compiled into one place by a data contributor, Austin Reese, on kaggle website. The data contains all relevant information that craigslist provides on car sales in the United States such as vehicle price, condition, manufacturer, location, and 16 other categories.
## DATA CLEANSING
The dataset was cleaned by removing the irrelevant columns and checking for duplicate rows. Then missing values were looked at to view how much data was missing and in what way. Some of the missing values were populated using numpy's random.choice() funciton replacing the missing values with a random category variable based on their probability of occuring . Outliers were also checked and removed to prevent the results from being overly affected by them.
## EXPLORATORY DATA ANALYSIS
This was conducted to understand what the data can tell us. relationships were checked and assessed in order to further filter what was needed for the analysis. Also a few custom columns were created to complement some other variables in the dataset.
## RECOMMENDATION SYSTEM
Wiith the cleaned dataset, a content-based recommender system can now be developed. This recommendation system is the similarity of the vehicle features and not on user metadata since that is not provided. TdIdfVectorizer and cosine_similarity of scikit learn's machine learning library were used to develope the system. The recommender system prints out the top 6 most similar cars to a number of specified inputs.
## DATA MODELING
Here we check for the correlation relationship between variables to ascertain what we can use to build the price prediction model. The data was preprocessed using sklearn's LabelEncoder and fed into 3 regerssion models and evaluated for the best performing one. Randonforest regressor was chosen and it had a 87.79% accuracy score.
## INSIGHTS
 - Most of the used car listings were found in most of the top 10 most populated states in the US
 - Ford, Chevrolet, and Toyota were the most popular car manufacturers. This is because majority of the listed cars were either sedans, SUVs, trucks or pickups which these manufacturers are known for producing.
 - These top 3 car manufacturers had an average price of ~16k USD, ~1k USD higher than the total average price of all cars listed in the top 12 states with more than 5000 car listings.*
 - On average, pickups and trucks go for ~23k USD, almost 2x that of SUVs and sedans.*
 - Since there seems to be a huge market for used luxury cars (sedans and SUVs) the recommendation engine should focus more on these types of cars.
 - California has the most car listings with an average price of ~15k USD which is ~1.5x less than that of Washington state with ~4x less number of car listings.*
 - Gas fuel engines is the most occuring type of fuel in all cars except for pickups and trucks which show a considerable split between gas and diesel engine vehicles
 - The majority of the cars have below average miles driven per year. This suggests the cars have not been overworked and can be resolved for good value especially when most of then are either in excellent or good condition.
 - The average price of cars seems relatively higher for newer cars than older cars, but this is affected by other factors such as vintage cars and level of luxury attributed to the model*
 - White and black colored cars are the two most popular car colors also having the two highest average prices, ~17.6k USD and ~16.6k USD respectively. Ford and Cehvrolet car manufacturers are prevalent in this department.*
## CONCLUSION
A recommender system and a price prediction model for the used car dataset was successfully created for this project after extensive data cleaning and preprocessing.

The recommender system is able to print out the 6 most similar cars to what the user sets as a guiding parameter much like a search engine filter.

The price prediction model was achieved through Random Forest Regressor machine learning model and saved for use to predict used car prices after specifying the relevant parameters. Two models were built with similar levels of accuracy. The one with the higher accuracy (rc_uc_model, acc = 87.79%) will be used for price predictions.
## CHALLENGES AND RECOMMENDATIONS
### CHALLENGES
#### Dealing with missing data
To have a better cleaned data, some of the missing values can be figured out with the other information available. For example, for missing car types, this can be inferred from the manufacturer and model columns. Some manufacturers have a common type of car they produce (ford produces mostly pickups and trucks), and the models can comstimes infer what type of car it is. So, more coding would be needed to ascertain what type of car an entry is if that information was missing.
The missing manufacturers can also be infered from the model. Although this dataset had some models that were questionable, most of them can be used to get the manufacturer with an extensive code script.
Using a random choice method to assign items to missing cells doesn't take into account the other data in that row but helps to rationalize what it could have been based on the available item probabilities of occuring.
#### Recommendation system
The recommendation system seems to be returning cars from the same state. Further work would have to modify the code to take other cars in neighboring states into consideration
#### Price prediction model
The price prediction model is limited to the range of car specifications identified in the dataset. Any other specification not included in the dataset will run into an error
A cleaner way to prepare the data to build the maching learning model will need to be implemented to reduce the run time of the model
### RECOMMENDATIONS
#### Price prediction model
Use advanced price prediction techniques and develope an interactive user interface where users can estimate the price of a car based on various features
segregate the price prediction models for different regions - East and West coast
#### Recommender system
Use a dataset where the images of the listed cars are still accessible. That would make the recommendation system interesting by adding a visual level to it
Explore other methods of building a content based recommender system to incorporate location, seasonal weather condition, vehicle main use case
implement an input function where users input their choices to recommendation specification prompts
