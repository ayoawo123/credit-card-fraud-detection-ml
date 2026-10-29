# 99.83% Accurate. Zero Fraud Caught. Here's the Catch.

*How 284,807 credit card transactions exposed the hidden danger of trusting machine learning accuracy alone.*

Imagine a fraud detector that boasts **99.83% accuracy**. Impressive, right?

Not necessarily. In the dataset I studied, a system could reach that number simply by declaring **every transaction legitimate**. It would miss every single fraud case.

That's the accuracy trap: being right almost all the time can still mean failing at the one job that matters.

## How much fraud was hiding in the data?

I examined **284,807 credit card transactions**. Just **492—0.173%—were fraudulent**. That's roughly one fraudulent transaction in every 579.

There were no missing values, although I removed **1,081 exact duplicate records** before training. Interestingly, fraudulent transactions had a lower median amount (**9.25**) than legitimate transactions (**22.00**), in unspecified currency units. Amount alone, however, is not enough to identify fraud.

![Fraud distribution](../images/fraud_distribution.svg)

*Figure 1. Only 0.173% of transactions were fraudulent. Source: ULB/Worldline dataset.*

## Could machine learning identify the fraud?

I tested **Logistic Regression** and **Random Forest** using **56,746 transactions kept out of model training**, including 95 confirmed fraud cases.

Logistic Regression identified **83 of the 95 frauds (87.4%)**, but generated **1,389 false alerts**. Random Forest caught **69 frauds (72.6%)**, with just **2 false alerts**.

So which performed better? It depends on what matters most: catching more fraud or avoiding unnecessary investigations. There is no single winner without considering the cost of both mistakes.

![Model comparison](../images/model_comparison.svg)

*Figure 2. More fraud caught came with substantially more false alerts in this test.*

## What would happen with one new transaction?

I asked Random Forest to score a transaction it had not seen during training. It classified the transaction as **legitimate**, matching the known label. That is one correct example, not a guarantee of future accuracy.

## The real lesson

**A high accuracy score does not automatically mean a good fraud detector.** Financial institutions must measure missed fraud, unnecessary alerts, and the costs of each, then validate their models before operational use.

The next time you see a model boasting 99% accuracy, ask a better question: **What did it miss?**

*Data: [ULB/Worldline Credit Card Fraud Detection dataset](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud). [Explore my code and full CRISP-DM analysis on GitHub](https://github.com/ayoawo123/credit-card-fraud-detection-ml).*
