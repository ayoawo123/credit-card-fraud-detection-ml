# Can Machine Learning Detect Credit Card Fraud? What 284,807 Transactions Reveal

Credit card fraud is difficult to detect because fraudulent transactions are rare. I analyzed a public dataset of **284,807 transactions** to examine whether machine learning can distinguish fraud from legitimate purchases—and what mistakes these models make.

![Original fraud distribution](../images/fraud_distribution.svg)

## How rare is credit card fraud?

Only **492 transactions (0.173%)** were labeled fraudulent. A system that called every transaction legitimate would appear almost 99.83% accurate while catching **zero fraud**. That is why I measured *recall* (the share of fraud caught) and *precision* (the share of alerts that were genuine), not just accuracy.

## What did the data reveal?

The median transaction amount was **9.25 for fraud versus 22.00 for legitimate transactions**, in the dataset's unspecified currency units. Amount alone cannot reliably identify fraud. I also found **1,081 exact duplicate records**, which were removed before training. There were no missing values.

## Which model performed better?

I compared two models using **56,746 transactions they had not seen during training**.

| Model | Fraud caught (recall) | Alert precision | False alerts |
|---|---:|---:|---:|
| Logistic Regression | 87.4% | 5.6% | 1,389 |
| Random Forest | 72.6% | 97.2% | 2 |

Logistic Regression detected **83 of 95** fraudulent transactions, but it generated many more false alarms. Random Forest detected **69 of 95**, missing more fraud yet producing far fewer false alerts. Random Forest also achieved higher average precision across thresholds (**0.808 versus 0.672**).

![Measured model performance](../images/model_comparison.svg)

## What happens with a new transaction?

For a transaction held out from training, the Random Forest returned a **0.000 model score** and classified it as legitimate; the known label was legitimate. This illustrates a single prediction, **not** proof that future predictions will be correct.

## The takeaway

Fraud detection involves a tradeoff: catching more fraud can inconvenience more genuine customers. Banks would need to weigh missed losses against investigation costs before selecting a model and decision threshold. These findings come from one historical dataset and one test split; real deployment requires additional validation and human oversight.

*Source: ULB/Worldline credit card fraud dataset, distributed through Kaggle. [View the analysis on GitHub](https://github.com/ayoawo123/credit-card-fraud-detection-ml).*
