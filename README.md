# Adversarial_Machine_Learning_Attack_on_Spam_Email_Filter


## Introduction

Machine learning-based spam detection models learn from a set of labeled training data and detect spam emails using this trained model. In this assignment, we study a class of vulnerabilities of such detection models, where the attack can manipulate the numerical features used in such a model ( e.g., TF-IDF vectors representing emails to a SVM classifier) to misclassify them during the detection phase. However, very often feature extraction methods make it difficult to translate a change made to the features to that in the textual email space. This lab uses a new attack method of making guided changes to the text in emails by taking advantage of purposely generated adversarial TF-IDF vetor representing emails. We identify a set of "magic words", or malicious words, to be added to a spam email, which can cause desirable misclassifications by classifiers. This attack works in a similar way to the so-called "good word attack".

### Datesets
- messages.csv contains the email subjects, email messages, and email label (normal, abnormal)

## Model Designs

### Loading the dataset

We will be using the Ling-Spam (as used in a previous assignment). The Ling-Spam dataset is a collection of 2,893 spam and non-spam messages curated from Linguist List. The messages in the dataset revolve around linguistic interests, such as job postings, research opportunities and software discussion.

#### Acknowledgements

The dataset and its information come from the original authors of "A Memory-Based Approach to Anti-Spam Filtering for Mailing Lists". The dataset was made publicly available as a part of that paper. 




## Bibliography

- (1) Q. Cheng, A. Xu, X. Li, and L. Ding, “Adversarial Email Generation against Spam Detection Models through Feature Perturbation,” The 2022 IEEE International Conference on Assured Autonomy (ICAA’22), Virtual Event, March 22-23, 2022.

- (2) J. He, Q. Cheng, and X. Li, “Understanding the Impact of Bad Words on Email Management through Adversarial Machine Learning,” SIG-KM International Research Symposium 2021, Virtual Event, The University of North Texas, September 29, 2021. 

- (3) C. Wang, D. Zhang, S. Huang, X. Li, and L. Ding, “Crafting Adversarial Email Content against Machine Learning Based Spam Email Detection,” In Proceedings of the 2021 International Symposium on Advanced Security on Software and Systems (ASSS ’21) with AsiaCCS 2021, Virtual Event, Hong Kong, June 7, 2021.
