# Minimum Offer Price Prediction of Electronics Sold on an E-Commerce Platform

This project involves predicting the minimum offer price of electronic products (Phones, Tablets, Headphones, & Earphones) sold on an e-commerce platform. The model uses product search data extracted via RapidAPI, an API marketplace that provides access to the Product Search API, offering detailed product information*.

## Problem Statement

The goal of this project is to train a regression model that predicts the **minimum offer price** of electronic products sold on an e-commerce platform. By predicting this price, the model helps buyers estimate the lowest possible price for a product, enabling better purchasing decisions. For sellers, the model provides insights into competitive pricing, helping them optimise their pricing strategies and remain competitive in the marketplace.

## Dataset

The dataset contains the following columns:

1. **product_title**: Title of the product.
2. **product_price**: Current price of the product.
3. **product_original_price**: Original price (before any discounts).
4. **product_star_rating**: Average customer rating.
5. **product_num_ratings**: Total number of ratings.
6. **product_num_offers**: Number of offers available.
7. **product_minimum_offer_price**: The target variable—minimum price offered for the product.
8. **is_best_seller**: Whether the product is a "Best Seller" (1 = True, 0 = False).
9. **is_recommended**: Whether the product is marked as 'Recommended' based on customer ratings, purchase rate etc (1 = True, 0 = False).
10. **is_fast_shipping**: Whether the product is eligible for fast shipping (1 = True, 0 = False).
11. **product**: Product category (e.g., Phone, Tablet, Headphones & Earphones).

* Note, all brand-specific identifiers have been removed or renamed during data preprocessing.

## Model Workflow

This project has been split into 3 phases: 
- `Data Extraction`
- `Data Processing`
- `Model Building`

# Data Extraction

- Initialise an API connection using Python’s requests package to retrieve product search data using a REST API available via Rapid API (API Marketplace)
-	Save raw data as a csv file to be pre-processed in the next phase

# Data Processing

-	Drop irrelevant columns, and anonymise any brand identifiable fields 
-	Drop any records where the target variable is null
-	Preprocess pricing fields, removing any non-numeric characters
-	Create a rules-based framework to filter erroneous accessories data i.e., Keyboards / Covers

## Feature Engineering

**Pre-Model Training**
-	Combat multicollinearity between pricing columns by creating a derived feature variable which extracts the discount rate between the original and current price
-	Create three new feature variables derived from the product title using regex: ‘Storage capacity’ /  ‘has storage’  /  ‘brand’

**Pre-Model Training**

-	Remove storage capacity outliers using the Interquartile Range (IQR) method
-	Apply a log transformation to heavily right skewed numerical features
-	Create interaction features
-	Filter out any brands which have a count smaller than 10

# Model Building

- Create a custom class that imputes the ‘product star rating’ using the median, grouped by the product type
- Apply a log transformation to the target variable to stabilise variance and reduce skewness. Note the model was trained with and without the log transformation to compare performance.
- Build a pipeline that integrates column transformers for encoding and scaling, a custom imputation class, and a Random Forest regressor to train. 
- RandomizedSearchCV is used for hyperparameter tuning and the model is evaluated to identify the best parameters that optimise the R2 score
- Alternative models were trained to find the best performing model i.e Cat Boost regressor 
- The final model is saved as a pickle file


## Environment

This project uses environment variables to securely store API keys and other sensitive information. You will need to create a `.env` file in the root directory of the project to store your RapidAPI key and API host.

## Dependencies

The following libraries are required to run the project:

- `pandas`
- `numpy`
- `seaborn`
- `matplotlib`
- `requests`
- `python-dotenv`
- `scikit-learn`
- `catboost`
- `pickle-mixin`

To install dependencies, use:

```bash
pip install -r requirements.txt
