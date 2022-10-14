# Credit_Risk_Analysis
DU Data Bootcamp: Module 17 ML

## Overview of Project

### Purpose of Project
How can Machine Learning help us improve risk assessment, and improve decision-making, in particular when analyzing imbalanced datasets? This exploration seeks to understand the impact of various features from a major consumer lending company, and learn what predictions can be made, if any, regarding credit risk. The goal is to create a ML model that will assist stakeholders in evaluating loan requests to maximize business growth while avoiding undesirable ventures.

## Analysis and Challenges
Initial challenges, like with any ML project, are to understand the raw dataset and make decsions regarding the preprocessing of the data. I spent a bit of time sampling various methods and eventually chose to deviate slightly from the base instructions in the challenge. These changes are as follows:
* Custom encoding for date fields: months were initially converted to numerical values based on standard calendar conventions
* StandardScaler was used to transform the columnar data to reduce the impact of numerical variance between columns, inparticular in recognition of the potential impact that interest rates and debt-to-income metrics may have in comparison to loan amounts.

Central to this challenge and resulting analysis are the innate hurdles around building ML models using imbalanced datasets. As was covered throughout the module documentation, in assessing something like fraudulent credit card charges, or in this case, risk assessment for consumer lending in an attempt to make predictions regarding future delinquency, models can have a high degree of accuracy by reconizing <i>most</i> loan applications as acceptable. The default rates in the dataset are relatively low, such that predicting the vast majority of applications as "safe" would be relatively accurate. They would not, however, offer much in the way of precision. That is to say, and was demonstrated in multiple model scoring, that models may do an excellent job of predicting safer loans. But they may not help much at all in predicting future delinquency.

<div><p>
<img src="https://github.com/cb19weber/Credit_Risk_Analysis/blob/main/images/resampling_models.png" align="center">
</p></div>

As documented above, the resampling models all performed relatively similarly. Balanced accuracy scores ranged from 0.79 to 0.83, with Combination (Over and Under) Sampling coming out on top. The high risk predictability across all models was extremely low, consistently around 0.03, while low risk assessment was captured almost perfectly.

The challenge offered further guidance in model construction with the suggestion of ensemble models: BalancedRandomForestClassifier and EasyEnsembleClassifier. Challenges encountered with using these models are discussed in detail below, but from a results perspective 
<div><p>
<img src="https://github.com/cb19weber/Credit_Risk_Analysis/blob/main/images/ensemble_models.png" align="center">
</p></div>
the models performed again somewhat similarly to the resampling model work. The BalancedRandomForestClassifier was nearly identical in both quality and flaw, mainly highlighted by the precision faults regarding high risk precision. Ironically the RUSBoostClassifier was the highest precision model, with 0.11 for high risk assessment, <i>until</i> the RandomForestClassifier (non-Balanced) was utilized. Wow! What a difference! 0.76 precision! There was definitely a sacrifice to accuracy. But such imablances have to be considered in varying economic conditions. Is it better to be more risk averse? It's certainly better to utilized multiple models to get a clearer picture on how the data stacks up to communicate a story and varying probabilities.

After some adjustments to my local ML environment, I was able to run the BalancedRandomForestClassifier and EasyEnsembleClassifier locally. The BalancedRandomForestClassifier results were unchanged and consistent with the model built in Google Collab. The EEC results came in remarkabely similar to the RUSBoostClassifier results initially modeled. <img src="https://github.com/cb19weber/Credit_Risk_Analysis/blob/main/images/eec_model.png" align="center">The precision was slightly worse than RUSBoostClassifier, but certainly higher than any of the other models. Noteworthy, the EEC model had a slightly lower recall than RUSBoostClassifier, and a slightly lower F1 score, but was otherwise markedly similar. This does seem to confirm the models similar performance assessment as documented within imbalanced-learn.

### Challenges and Difficulties Encountered
I had a few different challenges in completing the model for this project, largely due to library functionality with a few imbalanced-learn algorithms. Utilization of the Google Collab platform, and deviating away from my local ML environment helped to solve some of the issues. There have additionally been some recent changes to some of the ensemble models utilized in this project, such that I was unable to utilize EasyEnsembleClassifier either in my local ML environment or on the Google Collab platform. In review of <a href="https://imbalanced-learn.org/stable/auto_examples/ensemble/plot_comparison_ensemble_classifier.html#sphx-glr-auto-examples-ensemble-plot-comparison-ensemble-classifier-py">ensemble plot comparisons</a> from the imbalanced-learn library documentation, I was able instead implement the RUSBoostClassifier model, based on the same AdaBoostClassifier utilized in EasyEnsembleClassifier. The credit_risk_ensemble file with the _gc extension was fully functional for me on Google Collab. The EasyEnsembleClassifier method is coded into credit_risk_ensemble that was designed to run on my local ML environment. In order to run the EEC model in my local ML environment, along with the BalancedRandomForestClassifier, I had to step back my scikit-learn library package to version 1.0. Some of the attributes within EEC have been deprecated since version 1.0 and are noted in the documentation as being removed completely in version 1.2.

## Results
Overall, I <i>love</i> Machine Learning. I've been interested in statistics since I was young, and the ability to produce models from which to learn from the underlying data and form predictive theorums is really exciting. I also enjoy that there is significant judgment required in the development of Machine Learning models and dataset preprocessing. You have to ask questions of the data and really explore the nuances of the greater context before building any of the models. And even then, it's really interesting to run several different models in parallel and compare the algorithms for the problem set being researched. I look forward to hopefully a future ability to get deeper with ML and continued self learning and development.