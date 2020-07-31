---
layout: post
title: Predicting Income Status 
subtitle: Based on Education, Gender, Age, Ethnicity, etc.
cover-img: /assets/img/Money.jpg
tags: [books, test]
---

At first glance, this challenge seems easy enough, right?  People with degrees will become the top dogs, and as education decreases, income does as well. However, this could be quite inaccurate, many many other factors play into this. The college game is long gone, traditional education has become less and less important throughout the years in **some industries**. Employers are getting caught up and realizing that skills and experience are what matters the most, but that's a whole other rabbit hole we're not going to get into today. Predicting someone's exact income with generalizations is challenging, if not next to impossible. That's is why we are going with an alternative, we'll be predicting if a person's income is above average (**using $50,000 or more**), below average (**less than $50,000**), or below the poverty line ($12,000 or less) which in this case would be **$10,000** or less because of the data available. We'll be using multiple features which as you read in the subtitle include Education, Gender, Age, Ethnicity, preferred language, their primary source of information, if the person is an active voter, amongst others.

## Data
Features that were not as important were dropped from the model. These included things like the id of the survey, district, and other features that mostly had missing values. The cleaning process also included generalizing some of the data. Some of the features had way too many variables with not many I did this by creating a simple function which would keep variables with  a **significant number** (more than 1000) and store all others in a single variable (**other**):     

![%generalizing](https://raw.githubusercontent.com/lsraei20/lsraei20.github.io/master/assets/img/Screen%20Shot%202020-07-31%20at%208.28.28%20AM.png)

Other data cleaning included the typical, things like misspellings, lower and uppercase, etc...

## Base Model vs Final Model 

Decided Baseline for this model was accuracy, false positives or negatives would not be of trouble for this specific data, even if it was used for benefit allocation there could always be an appeals system in place to suffice that. Base accuracy came out to:

![%Baseline](https://raw.githubusercontent.com/lsraei20/lsraei20.github.io/master/assets/img/baseline.png)

For the final model, I tried linear classification, Xgboost, RandomGradient. Although most of the scores seemed similar, I decided to go with RandomForestClassifier with some minimal hyperparameters which gave me a final accuracy score of about 76%:

![%accu](https://raw.githubusercontent.com/lsraei20/lsraei20.github.io/master/assets/img/accuracy.png)
