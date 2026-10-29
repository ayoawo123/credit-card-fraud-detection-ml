# The 99.83% Trap: When AI Accuracy Hides Credit Card Fraud

*What 284,807 transactions reveal about the danger of trusting accuracy alone.*

Imagine a fraud detector boasting **99.83% accuracy**. Impressive? Not necessarily. In the dataset I studied, a system could achieve that score simply by labeling **every transaction legitimate**—and catching **zero fraud**.

That is the 99.83% trap: a strong-looking number can hide a serious failure.

![Fraud versus legitimate transactions](../images/fraud_distribution.svg)

## How much fraud was hiding in the data?

Of **284,807 credit card transactions**, only **492 (0.173%)** were fraudulent—roughly one in every 579 purchases.

My first step was to explore the data. I found **1,081 exact duplicate records**, which I removed, and no missing values. The median transaction amount was **9.25 for fraud versus 22.00 for legitimate purchases** (the dataset does not specify a currency). Transaction amount alone cannot reliably distinguish fraud.

## Could machine learning do better?

I compared two models on **56,746 transactions excluded from their training**, including 95 fraud cases.

| Model | Fraud cases found | Genuine alerts | False alerts |
|---|---:|---:|---:|
| Logistic Regression | 83 of 95 (87.4%) | 5.6% | 1,389 |
| Random Forest | 69 of 95 (72.6%) | 97.2% | 2 |

The contrast was striking. Logistic Regression caught **14 more fraudulent transactions**, but also raised **1,387 more false alarms**. Random Forest produced far fewer mistaken alerts, yet missed **26 fraud cases**.

![Model performance comparison](../images/model_comparison.svg)

## What about one new transaction?

I used Random Forest to classify a transaction held out of training. It marked the transaction **legitimate**, matching its known label. One successful prediction is useful as a demonstration, not proof that future decisions will always be correct.

## The takeaway

Fraud detection is not about achieving the highest accuracy score. It is about balancing **missed fraud** against **unnecessary alerts**. Before banks could use either model, they would need further testing, appropriate alert thresholds, and human oversight.

**The lesson: always ask what an accuracy score is hiding.**

*Source: [ULB/Worldline Credit Card Fraud Detection dataset](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud). [Explore the analysis and code on GitHub](https://github.com/ayoawo123/credit-card-fraud-detection-ml).*
