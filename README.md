# Credit_Risk_Analysis
DU Data Bootcamp: Module 17 ML

## Overview of Project

### Purpose of Project
How can Machine Learning help us improve risk assessment, and improve decision-making, in particular when analyzing imbalanced datasets? This exploration seeks to understand the impact of various features from a major consumer lending company, and learn what predictions can be made, if any, regarding credit risk. The goal is to create a ML model that will assist stakeholders in evaluating loan requests to maximize business growth while avoiding undesirable ventures.

## Analysis and Challenges
Initial challenges, like with any ML project, are to understand the raw dataset and make decsions regarding the preprocessing of the data. I spent a bit of time sampling various methods and eventually chose to deviate slightly from the base instructions in the challenge. These changes are as follows:
* Custom encoding for date fields:

### Challenges and Difficulties Encountered
I had a few different challenges in completing the model for this project, largely due to library functionality with a few imbalanced-learn algorithms. Utilization of the Google Collab platform, and deviating away from my local ML environment helped to solve some of the issues. There have additionally been some recent changes to some of the ensemble models utilized in this project, such that I was unable to utilize EasyEnsembleClassifier either in my local ML environment or on the Google Collab platform. In review of <a href="https://imbalanced-learn.org/stable/auto_examples/ensemble/plot_comparison_ensemble_classifier.html#sphx-glr-auto-examples-ensemble-plot-comparison-ensemble-classifier-py">ensemble plot comparisons</a> from the imbalanced-learn library documentation, I was able instead implement the RUSBoostClassifier model, based on the same AdaBoostClassifier utilized in EasyEnsembleClassifier. The credit_risk_ensemble file with the _gc extension was fully functional for me on Google Collab.

## Results
