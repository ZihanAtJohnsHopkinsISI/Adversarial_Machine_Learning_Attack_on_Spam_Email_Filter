# Adversarial Machine Learning Attack on Spam Email Filter


## Introduction

Machine learning-based spam detection models learn from a set of labeled training data and detect spam emails using this trained model. In this assignment, we study a class of vulnerabilities of such detection models, where the attack can manipulate the numerical features used in such a model ( e.g., TF-IDF vectors representing emails to a SVM classifier) to misclassify them during the detection phase. However, very often feature extraction methods make it difficult to translate a change made to the features to that in the textual email space. This lab uses a new attack method of making guided changes to the text in emails by taking advantage of purposely generated adversarial TF-IDF vetor representing emails. We identify a set of "magic words", or malicious words, to be added to a spam email, which can cause desirable misclassifications by classifiers. This attack works in a similar way to the so-called "good word attack".

### Datesets
- messages.csv contains the email subjects, email messages, and email label (normal, abnormal)

## Model Designs

### Loading the dataset

We will be using the Ling-Spam (as used in a previous assignment). The Ling-Spam dataset is a collection of 2,893 spam and non-spam messages curated from Linguist List. The messages in the dataset revolve around linguistic interests, such as job postings, research opportunities and software discussion.

##### Acknowledgements

The dataset and its information come from the original authors of "A Memory-Based Approach to Anti-Spam Filtering for Mailing Lists". The dataset was made publicly available as a part of that paper. 

##### Additional Information of Three Datasets

In the above operation, we divided the entire dataset into three parts: training dataset, validation dataset, and testing dataset. This is done to evaluate the performance of our machine learning model on new and unseen data. The training dataset is used to train the model, the validation dataset is used to tune the model's hyperparameters(magic words in our application), and the testing dataset is used to evaluate the final performance of the model.


## Preprocessing the Emails

**To extract only useful information from the emails we used, we applied serveral data preprocessing steps.**

- (1). We removed all HTML tags, numbers, punctuation marks, and English stop words.

- (2). We converted all words to their lowercase forms and combined each paragraph into a single line instead of multiple lines.

- (3). We conducted stemming on all the remaining words to reduce them to their root forms.


## Feature Extraction

In this step, we aim to transform the text content of an email into a numerical feature vector that captures the essential information used for classification. To achieve this, we can choose from a variety of vectorization techniques that convert text data into numerical vectors.


## Training SVM Classifiers

In this section, we will train a Support Vector Machine (SVM) as an spam filter. 


## PGD Attack

Our approach is based on successful adversarial perturbations made to model input features. We employ the Projected Gradient Descent (PGD) method to modify numeric feature values in the feature domain. PGD algorithm iteratively finds the needed changes with a constraint, dmax, which is the Euclidean distance to the original features indicating the allowed level of perturbations, to achieve the maximum loss in classification. In our approach, we run PGD over a set of spam emails and generate adversarial examples. Then we test these modified feature vectors to see whether they could successfully bypass the detection (i.e., being classified as ham). 


## Magical Words

Adversarial emails are crafted by adding “magic words” to the original spam emails. The “magic words” are identified by intersecting the unique ham words with the “top words” identified during the adversarial perturbations. Specifically, the unique ham words are the words that only appear in ham emails but not in spam emails. After the PGD attack on the set of spam emails, we find which features are modified to the largest extent to bypass the detection. We then select a list of “top words” whose feature values have been changed the most. (The changes are measured by the variance of differences before and after the PGD perturbation.) In our experiments, we use the top 100 words, which is efficient. This set is relatively small and demonstrates a high success rate with the resulting magic words to fool the classifier. 


## Crafting Adversarial Emails & Attacking SVM

We can insert the identified "magic words" to original spam emails. This proccess is what we called "crafting adversarial emails". Then, we feed the new feature vectors of these crafted emails to the SVM classifier to see if they can be misclassified as ham emails.


## Check other possible email filter system and compare the result

rain KNN classifiers, Random Forest, XGBoost, with the same training dataset provided and the two feature extraction methods you have used to obtain the set of magic word you selected. Here you build two spam filters using a different algorithm. Please show the false negative rates on the testing dataset.
Pick 100 spam emails and add the magic words to them. Feed them to the two KNN classifiers. Calculate the false negative rates. Can you tell whether the attacks are successful? Ans: Both of the attack success since fn rate of KNN classifiers is higher after the attack happened


## Bibliography

- (1) Q. Cheng, A. Xu, X. Li, and L. Ding, “Adversarial Email Generation against Spam Detection Models through Feature Perturbation,” The 2022 IEEE International Conference on Assured Autonomy (ICAA’22), Virtual Event, March 22-23, 2022.

- (2) J. He, Q. Cheng, and X. Li, “Understanding the Impact of Bad Words on Email Management through Adversarial Machine Learning,” SIG-KM International Research Symposium 2021, Virtual Event, The University of North Texas, September 29, 2021. 

- (3) C. Wang, D. Zhang, S. Huang, X. Li, and L. Ding, “Crafting Adversarial Email Content against Machine Learning Based Spam Email Detection,” In Proceedings of the 2021 International Symposium on Advanced Security on Software and Systems (ASSS ’21) with AsiaCCS 2021, Virtual Event, Hong Kong, June 7, 2021.
