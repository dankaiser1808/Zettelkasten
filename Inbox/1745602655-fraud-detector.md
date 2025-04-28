---
id: 1745602655-fraud-detector
aliases:
  - Fraud Detector
tags: []
---

# Fraud Detector

Fraud Detector allows us to build, deploy and manage fraud detection algorithms/models.
It predicts suspicious transactions and behaviour before any valuable process are going to be executed, for example payment.
It doesn't require any machine learning knowledge since it's fully managed by amazon and works in Real-Time to detect frauds.
As other AWS services, Fraud Detector stronglt integrates other AWS services like IAM.

The workflow of the Fraud Detector is defined as follows:

We define a business use case that should be monitored for fraud. We Input historical data of the use case and select the model type and train the model based on the input data. After the training we receive a model score and an performance evaluation for the fraud detection. After that, we have the opportunity to retrain the model to enhance the evaluation outcome. Next, we can define rules how to deal with the confidence of a detected fraud. If the confidence is 70%, we can queue it for human review for example.

All those rules we define will be aggregated and deployed as a so called detector. The detector can evaluate frauds in real-time and also evaluate batches of events.

It automatically improves based on the feedback we give, making it better with usage.
