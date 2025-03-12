# Minimum Offer Price Prediction for Electronics on Amazon

This project focuses on predicting the minimum offer price of electronic products (Phones, Tablets, Headphones, & Earphones) on Amazon. The model uses product search data extracted via RapidAPI, a platform that provides access to the Amazon Product Search API, offering detailed product information.

## Problem Statement

The goal of this project is to develop a regression model that predicts the **minimum offer price** of electronic products on Amazon. By predicting this price, the model helps buyers estimate the lowest possible price for a product, enabling better purchasing decisions. For sellers, the model provides insights into competitive pricing, helping them optimise their pricing strategies and remain competitive in the marketplace.

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
9. **is_amazon_choice**: Whether the product is marked as "Amazon's Choice" (1 = True, 0 = False).
10. **is_prime**: Whether the product is eligible for Amazon Prime (1 = True, 0 = False).
11. **product**: Product category (e.g., Phone, Tablet, Headphones & Earphones).

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
