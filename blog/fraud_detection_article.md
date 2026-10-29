# Can Machine Learning Detect Credit Card Fraud? Insights from 284,807 Transactions

*Publication draft — complete bracketed fields using the executed notebook before publishing.*

Credit card fraud creates losses for financial institutions and anxiety for customers. But finding suspicious activity among millions of legitimate purchases is difficult. I explored a public dataset of 284,807 credit card transactions to understand what machine learning can—and cannot—tell us.

![Fraud vs legitimate transactions](../images/fraud_distribution.png)

## How common was fraud?

The dataset contains 492 fraudulent transactions, approximately **0.173%** of all records. That means a system labeling everything legitimate could appear over 99% accurate while missing every fraudulent transaction. Accuracy alone is therefore a poor measure of success.

## Can transaction patterns help identify fraud?

The dataset includes transaction amounts, elapsed time, and anonymized numerical features. After exploring the distributions and checking data quality, I compared two classifiers: Logistic Regression and Random Forest. The anonymized features limit how confidently we can explain *why* individual transactions look suspicious.

## Which model detected fraud more effectively?

[Insert the measured precision, recall, F1-score, and average precision for both models after executing the notebook. Explain the tradeoff between catching fraud and incorrectly flagging customers.]

![Model comparison](../images/model_comparison.png)

## What happens with a new transaction?

I tested the selected model on a transaction held out from training. [Insert its measured risk score, prediction, and whether the original label agreed.] The output is a screening signal—not proof of fraud—and would require appropriate human review.

## Final takeaway

Fraud detection requires more than a high accuracy percentage. The most useful model is one that identifies meaningful risks while controlling unnecessary alerts. Before real-world deployment, a financial institution would also need threshold tuning, temporal validation, monitoring, and governance.

*Dataset: ULB/Worldline credit card fraud dataset, available on Kaggle. Code and reproducible analysis: [GitHub repository](https://github.com/ayoawo123/credit-card-fraud-detection-ml).*