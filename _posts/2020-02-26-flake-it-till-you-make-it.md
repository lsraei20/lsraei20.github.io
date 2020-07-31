---
layout: post
title: Predicting Income Status (Failure)
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

At this point is where the learning curve starts, I had finished all of this work, I was ecstatic with the results when it hit me! I had messed up big time...

![%matrix](https://raw.githubusercontent.com/lsraei20/lsraei20.github.io/master/assets/img/matrix.png)

As you can see in this confusion matrix I did not get a high score, that was at best a little better than a base accuracy score...  
At this point in the project, my only option was to keep going with it and explore what went wrong. 

## What Broke My Project 

This post has been written as I worked through the project, I believe you can identify my excitement at the beginning and how disappointment hit strong! 

The main issue I identified was the fact that I was measuring my accuracy score at the beginning of the project. This was key to me not realizing something was wrong until the very end. 

![%incomeacc](https://raw.githubusercontent.com/lsraei20/lsraei20.github.io/master/assets/img/income%20acc.png)

As you can see in this picture, the target at the beginning had way more classifiers, so the accuracy score was a low 22%. However, when I cleaned it afterward to 'above average', 'below average' and 'poverty' that reduce the classifiers by a lot causing my base score to increase. This mistake sounds so silly that it is embarrassing, to say the least.

My model nothing else but predicting the majority classifier which in this case happened to be 'Above Average'. 

![%incomeacc](https://raw.githubusercontent.com/lsraei20/lsraei20.github.io/master/assets/img/targetcount.png)

There are multiple reasons as to why I believe my model was not successful at increasing the score, these are theories and doubts I had even before starting the project.
-First is that there was just not enough variety of data for my model to learn from. I know! This contradicts what I said before! The fact that I had to create a function to generalize because there was too much variety, but let me explain... The variety in the features was really dirty, it was was mostly in one or two variables but then 341 other variables had only 1 or 2 instances. This is why I cleaned and classified them as **others** so in hindsight, there was almost no variety, or better put not enough data for the other classifiers.

![%vari](https://raw.githubusercontent.com/lsraei20/lsraei20.github.io/master/assets/img/variety.png)

-Another Problem that is correlated to the first is that this needs a lot more data since the begging I knew predicting income would be hard as there are a lot of factors that go into it. However, that false hope score made me blind to that fact, I thought I had it all figured out, and the results were going to be incredible. I started sensing that something was wrong when my visualizations started becoming a priority at the end of the project, I had problems creating Shapley Value Plots and others. I spend a lot of time stuck in that phase until I did the confusion matrix, that is what gave it away and made my world crumble.

## Conclusion

Apart from disappointment, there are many things that I was able to take from this frustrating experience. It should come as no surprise that I'd be sure not to touch the target **ever again**  after getting my base score. (I still cannot believe how small, yet impactful this mistake was). The most important thing, however, is a data exploration and my failure of it. Now I have that famous machine learning phrase stuck in my head forever 'Garbage in garbage out!' there is no doubt that my data was just too messy even though I spent hours refining and cleaning it, but maybe this dataset just was not meant to be. I could have of course realized this a lot sooner with minor but critical tweaks to my process. 





