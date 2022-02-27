# Predicting Average User-Ratings of Rock-Climbing Routes
### Abstract
The goal of this project was to use Linear Regression models to predict the average user-rating for rock-climbing routes in Kentucky. I collected data from the Mountain Project website about each route using web scraping. After collecting the data, I ran through multiple types of regression models before arriving at a final model. 
### Design
Kentucky has some of the best rock climbing in the world and is considered the rock climbing mecca of the East coast. Rock climbing guides are a vital part of the community there. With over 3,000 routes to choose from, a rock climbing guide company wants to better understand their what makes routes more desirable than others to provide the optimal experience for their clients. 
### Data
After some Exploratory Data Analysis and Feature Engineering, the dataset contains 1,582 routes. I collected 17 features on each route and the final model includes a total of 12 features. The data was collected from Mountain Project's website using Selenium and BeautifulSoup. 
### Algorithms
##### Feature Engineering
<ol>
    <li> The route's share-date was changed to the number of years  on the app for comparison</li>
    <li> The number of ratings, comments, photos and ticks were added together as a popularity metric because of multicollinearity issues</li>
    <li> Adding dummy variables for the categorical features</li>
    <li> Added interaction variables:
        <ul>
            <li> Difficulty Rating X Route Length</li>
            <li> Popularity / Route Age</li>
        </ul></li>
</ol>

##### Models
Simple Linear, Polynomial, Ridge & LASSO Regression were used. The final model used was a simple Linear Regression model with features removed according to the LASSO Regression results. 

##### Model Evaluation and Selection 
The entire dataset was split into a 60/20/20 - Training/Validation/Testing. I used 5-fold cross validation as I tested various models and scored them based on the validation set. I then combined the training and validation datasets for a final 80/20 (training/testing) split. The testing data was only used on the final model by using the same random state throughout. 

The metric I used to score my models was Mean Absolute Error (MAE), because it would be in the same unit as my target. Without a need to further penalize outliers, MAE keeps the model more interpretable to stakeholders. While I focused on the MAE, I also worked to reduce multicollinearity, which also increased MAE. In the future I would like to try more interaction terms to improve the model's performance even more.
### Final Simple Linear Regression Model Scores:
##### Training Data
<ul>
    <li> Accuracy: 0.566 </li>
</ul> 

##### Testing Data
<ul>
    <li> Accuracy: 0.572 </li>
    <li> MAE: 0.374 </li>
</ul> 

### Tools
<ul>
    <li> Selenium, BeautifulSoup & Requests for web scraping
    <li> Numpy and Pandas for data manipulation </li>
    <li> Scikit-learn for modeling </li>
    <li> Matplotlib and Seaborn for plotting </li>
