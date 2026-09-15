# Olist Customer Experience Analysis

[Español](README_ES.md) | **English**

Statistical and probabilistic analysis of approximately **99,441 Brazilian e-commerce orders** to understand customer satisfaction, delivery performance, purchasing behavior, and seller reliability.

Built with **Python, Pandas, NumPy, SciPy, Scikit-learn, Matplotlib, and Seaborn**.

> This project was developed as an academic Data Science case study at Universidad de La Sabana using the Brazilian E-Commerce Public Dataset by Olist. It is presented as a portfolio project to demonstrate statistical reasoning, probabilistic modeling, data analysis, and machine learning skills.

## Business Problem

An e-commerce marketplace needs to understand which factors are associated with customer satisfaction and seller performance so that operational decisions can be supported by quantitative evidence rather than intuition.

This project analyzes customer experience from several perspectives, including:

- Delivery performance and negative reviews
- Product and payment behavior
- Statistical distributions of operational variables
- Seller reliability under limited information
- Product-category diversity
- Geographic differences in customer ratings
- Prediction of negative customer reviews

## Dataset

The analysis uses the **Brazilian E-Commerce Public Dataset by Olist**, containing approximately **99,441 orders from 2016 to 2018** across 9 relational CSV files covering customers, orders, order items, payments, reviews, products, sellers, and geolocation data.

The raw CSV files are not included in this repository. Download the public Olist dataset from Kaggle and place the required files in the location expected by the notebook before execution.

## Analytical Approach

The project combines exploratory analysis, probability, statistical inference, distribution fitting, information theory, Bayesian reasoning, and classification.

Main techniques include:

- Conditional probability
- Bayes' theorem
- Maximum Likelihood Estimation and AIC comparison
- Parametric distribution fitting
- Expected value and variance
- Chi-square independence testing
- Correlation analysis
- Beta-Binomial Bayesian updating
- Shannon entropy
- Logistic classification and cross-entropy/log-loss
- Kullback-Leibler divergence

## Key Results

### Delivery performance and customer dissatisfaction

Orders with delivery times slower than the defined average threshold showed a **21.0% probability of receiving a negative review**, compared with **8.2%** for orders classified as on time. This represents approximately **2.55× higher negative-review probability**.

Using Bayes' theorem, the probability that an order was late increased from a prior of **8.0%** to a posterior of **33.7%** after observing a negative review.

### Distribution modeling

Delivery time was better represented by a **Log-Normal distribution** than a Gamma distribution according to AIC:

| Distribution | AIC |
|---|---:|
| Log-Normal | 646,576 |
| Gamma | 647,288 |

Product weight also favored a Log-Normal model over Gamma based on the Kolmogorov-Smirnov statistic:

| Distribution | KS statistic |
|---|---:|
| Log-Normal | 0.066 |
| Gamma | 0.139 |

### Purchasing behavior

Payment method and product category were not independent in the analyzed sample (**χ² = 405.2, p < 0.001**).

Delivery time and customer rating showed a negative correlation of **r = -0.33**, indicating that longer deliveries tend to be associated with lower ratings.

The `fixed_telephony` category showed the highest variance in average ticket value, indicating substantial price heterogeneity within the category.

### Bayesian seller evaluation

A Beta-Binomial model was used to update the estimated reliability of a new seller.

The population prior was **75.5%** and the posterior estimate increased to **83.7% after 5 positively rated sales**.

This demonstrates how Bayesian updating can support seller evaluation when only a small amount of new information is available.

### Product-category diversity

The product catalog produced a Shannon entropy of **4.71 bits**, compared with a theoretical maximum of **6.15 bits** for the analyzed category space.

This indicates that demand is diversified but still concentrated in a subset of leading categories.

### Negative-review classification

A logistic classifier for negative reviews achieved:

- **Training log-loss:** 0.324
- **Test log-loss:** 0.325

The similarity between the two values indicates stable predictive behavior in this experiment, with delivery delay emerging as the dominant predictor.

### Geographic comparison

The rating distributions for São Paulo and Rio de Janeiro were relatively similar, with a **KL divergence of 0.035 bits**, although Rio de Janeiro showed a higher proportion of one-star reviews.

## Business Interpretation

The analysis consistently identifies **delivery performance as an important customer-experience signal**. Delays are associated with a substantially higher probability of negative reviews and appear as an important feature in the negative-review classifier.

The project also demonstrates how probabilistic and statistical tools can support marketplace decisions beyond descriptive dashboards, including seller evaluation, product-category analysis, and comparison of customer behavior across regions.

These findings are observational and should not be interpreted as causal effects without an appropriate causal design.

## Repository Structure

```text
.
├── README.md
├── README_ES.md
├── proyecto_olist_completo.ipynb
├── Informe_Gerencial_Olist.docx
├── Guia_Defensa_Oral.md
└── .gitattributes
```

The structure above reflects the repository in its current state. The notebook and supporting documents may be reorganized later as part of the portfolio standardization process.

## Reproducing the Analysis

Install the main dependencies:

```bash
pip install pandas numpy scipy scikit-learn matplotlib seaborn jupyter
```

Download the Olist dataset, configure the notebook's data paths, and run:

```bash
jupyter notebook proyecto_olist_completo.ipynb
```

## Technologies

`Python` · `Pandas` · `NumPy` · `SciPy` · `Scikit-learn` · `Matplotlib` · `Seaborn` · `Jupyter Notebook`

## Skills Demonstrated

`Data Analysis` · `Statistical Analysis` · `Probability` · `Bayesian Analysis` · `Exploratory Data Analysis` · `Hypothesis Testing` · `Distribution Fitting` · `Information Theory` · `Machine Learning` · `Business Interpretation`

## Author

**David Santiago Cifuentes Grimaldo**  
Data Science Student  
Universidad de La Sabana
