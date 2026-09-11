# Model Fitness — Customer Churn & Retention Analysis

A business-focused customer retention project combining exploratory data analysis, churn prediction, individual risk scoring, and customer segmentation.

## About the Project

Model Fitness is a fictional gym chain looking to reduce customer churn and improve retention.

The goal of this project was to understand **which behaviours are associated with churn**, predict which customers are at higher risk of leaving, and identify customer segments that could benefit from different retention strategies.

The analysis combines predictive modelling with customer segmentation so that the final recommendations are not only statistically useful, but also practical from a business perspective.

## Business Questions

The project focuses on four main questions:

1. Which customer behaviours are most strongly associated with churn?
2. Can churn be predicted accurately enough to support retention actions?
3. Can predicted probabilities be translated into simple, actionable risk groups?
4. Are there distinct customer segments with meaningfully different churn patterns?

## Tools & Technologies

- Python
- pandas
- NumPy
- Matplotlib
- scikit-learn
- SciPy
- Logistic Regression
- Random Forest
- K-means Clustering
- Hierarchical Clustering
- Customer Segmentation
- Predictive Analytics

## Dataset

The dataset contains **4,000 customers and 14 columns** covering:

- customer demographics;
- contract length;
- remaining contract time;
- customer lifetime;
- gym attendance;
- group-class participation;
- referral and partner programmes;
- additional-service spending;
- churn status.

There are no missing values or duplicated rows.

## Key Findings

### Overall churn

The overall churn rate is approximately:

**26.5%**

Customers who churn tend to have:

- shorter contracts;
- fewer months remaining on their contracts;
- shorter customer lifetime;
- lower current-month attendance;
- lower historical attendance;
- lower participation in group activities;
- lower additional-service spending.

A drop in recent attendance is especially interesting because it may provide an early warning signal before a customer leaves.

### Strongest relationships with churn

The strongest negative correlations with churn include:

- `Lifetime`: **-0.438**
- `Avg_class_frequency_current_month`: **-0.412**
- `Age`: **-0.405**
- `Contract_period`: **-0.390**
- `Month_to_end_contract`: **-0.381**

Higher values in these features are generally associated with lower churn.

## Predictive Models

I compared two classification models using an 80/20 stratified train-validation split.

| Model | Accuracy | Precision | Recall |
|---|---:|---:|---:|
| Logistic Regression | 93.5% | 89.6% | 85.4% |
| Random Forest | 92.3% | 87.5% | 82.6% |

**Logistic Regression performed best across all three metrics** and was selected as the primary model.

## Individual Churn Risk

Logistic Regression was also used to estimate an individual churn probability for each customer in the validation sample.

For a simple operational interpretation, probabilities were divided into illustrative risk bands:

- **Low risk:** below 30%
- **Medium risk:** 30%–60%
- **High risk:** above 60%

Within the 800-customer validation set:

- **556** customers were classified as low risk;
- **56** as medium risk;
- **188** as high risk.

These thresholds are illustrative rather than fixed business rules. In a real retention programme, they should be calibrated according to campaign capacity and intervention cost.

## Feature Importance

Random Forest feature importance supported the exploratory analysis.

The most influential features were:

1. **Customer lifetime**
2. **Current-month visit frequency**
3. **Historical visit frequency**
4. **Age**
5. **Additional-service spending**
6. **Remaining contract time**
7. **Contract duration**

This reinforces the importance of recent engagement and the strength of the customer's relationship with the gym.

## Customer Segmentation

I used standardised customer features, hierarchical clustering, and **K-means with five clusters** to identify customer segments.

The executed clustering results were:

| Cluster | Customers | Churn rate | Interpretation |
|---|---:|---:|---|
| 0 | 1,010 | 2.77% | Most loyal |
| 1 | 385 | 26.75% | Medium risk |
| 2 | 505 | 44.36% | High risk |
| 3 | 1,262 | 51.43% | Highest risk |
| 4 | 838 | 6.80% | Low risk |

### Cluster 3 — Highest risk

This is the largest segment and has the highest churn rate.

Customers have relatively short contracts, short customer lifetime, and particularly low current-month visit frequency.

### Cluster 2 — High risk

This group also has a high churn rate and is characterised by customers who do not live or work close to the gym, along with relatively short contracts and lower engagement.

### Cluster 1 — Medium risk

Churn is close to the overall average. Customers show more moderate contract length and activity.

### Cluster 4 — Low risk

Customers have high visit frequency, longer lifetime, and relatively high additional-service spending.

### Cluster 0 — Most loyal

This segment has the lowest churn rate, along with long contracts, many months remaining, strong partner participation, and stable engagement.

## Business Recommendations

Based on the analysis, I would recommend:

1. **Create early-warning alerts for declining attendance.**  
   Customers whose recent gym frequency drops meaningfully could receive proactive outreach before disengagement becomes churn.

2. **Strengthen onboarding during the first 1–3 months.**  
   Short customer lifetime is strongly associated with churn, making early relationship-building especially important.

3. **Encourage longer contracts and early renewal.**  
   Longer contracts and more remaining contract time are associated with more stable customers.

4. **Increase social and community engagement.**  
   Group classes, partner programmes, and referral initiatives appear more frequently among stable customer profiles.

5. **Prioritise retention using churn probabilities.**  
   High-risk customers can receive more targeted retention campaigns rather than applying the same intervention to everyone.

6. **Combine prediction with segmentation.**  
   Churn probability helps identify **who** is at risk, while clustering helps explain **what type of customer** they are.

## What I Learned

One of the biggest takeaways for me was understanding that a predictive model only becomes truly useful when its results can guide a real business decision.

A churn probability by itself is only a number. Turning that probability into risk groups, understanding the behaviours behind it, and combining it with customer segments makes the analysis much more actionable.

This project strengthened my understanding of how exploratory analysis, machine learning, and business judgement can work together to support customer-retention decisions.
