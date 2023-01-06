---
title: "STARTHack"
date: 2022-08-25T15:33:37+02:00
draft: false
toc: false
images:
tags:
  - Hackathon
  - Machine Learning
technologies:
  - Python
  - Scikit-learn
  - PyTorch
---
New year new hack. After the success of the last hackathon, we decided to attend another one. This time we decided to go for a more ambitious project. For this hackathon we, a friend group of about 15 people, travelled from Zurich to St. Gallen to attend STARTHack, hosted by the university of St. Gallen.

## The hackathon
This hackathon was designed to be a 36 hour hackathon. The hackathon started on Friday at 10pm and ended on Sunday at 10am. The hackathon was hosted by the university of St. Gallen and was sponsored by a few companies. Opposed the my prior experience with Hackathons, this one was backed by big names, such as Sunrise, Accenture and UNEP. The amenities were considerably bigger and (as always) included free refreshments such as mate and redbull. There was even an indoor trampoline and access to a nearby swimming pool. What was important, which we did not perceive as such at that time, was that this was primarily an enterpreneurial hackathon.

## The team
We were composed of 4 people, each of them ETH students in theri second year studying computer science. In our team I was the only one with prior experience in hackathons.

## The project
Out of 10 or so possible challenges we decided to take on UNEP's challenge. We were tasked to create a Machine Learning algorithm which, based on historical data collected in HongKong, could predict landslides at a reasonable accuracy. We approached this problem as a regression problem, where we tried to predict the probability of a landslide occuring at a given location. We used a dataset of 1000+ locations in HongKong, each of them containing a set of features such as the elevation, the slope, the moisture of the soil and the type of rock. 

For this project we had the opportunity to work with a team of extremely talented people from all around the globe, including a Professor from the university of Hong Kong, that worked on an implementation of such a machine learning model himself.

To harness this dataset we introduced some data preprocessing. We first conducted some correlation analysis to isolate the values which weigh in most on the prediction. Following this we standardized the data and split it into a training and a test set. We then trained a catboost model on the training set and evaluated it on the test set. With this simple pipeline we were able to achieve an f1-score of approximately 0.6.

To improve on this score we decided to use cross validation to determine the optimal hyperparameters for our model. In addition we got started to feature engineer some new features. This process was a very lengthy one, as the feature generation took a lot of time to run as well as to implement it. In the end, we managed to get it to work and it delivered us an additional 10 features. Evaluating our model brought us to an f1-score of 0.7, which was a considerable improvement.

From then on the improvements were few and far between. We evaluated different models, such as a random forest, a gradient boosting model and a neural network. We also tried to use different feature selection methods, such as PCA and Lasso. In the end we were not able to improve our score any further. We decided to stop our efforts at this point and present our results.

## The presentation
The presentation was a very interesting experience. We were given 5 minutes to present our project. We decided to split the presentation into 3 parts. The first part was a short introduction to the problem and the dataset. The second part was a short overview of our approach and the results we achieved. The third part was am outlook on what we would have done differently and what we would have done to improve our results.

Being stuck on a rather mediocre score we did not dedicate enough time to the presentation. We got very hung up on being the 4th place in the leaderboard and focused solely on improving our model, may it be by a score of 0.001.

This is where the fact, that this was an enterpreneurial hackathon comes into play. The judges were not interested in our model, but rather in our approach. They were interested in how we could take the model and develop an idea or a concept based on that model. We did not have a good answer to these questions and as a result we did not win our group.

## What I learned
This experience has tought me that it is not worth it to focus solely on the product. It is important to have a good prouct, but it is even more important to have a good direction. Perfectionism can be your downfall and being stuck on a minute detail (or rather in this case not being the top of the leaderboard) can be a very costly mistake. What we could have done, in retrospect, is take our model as-is and improve on it in a similar fashion as was done by the winners of our group. They had the idead to use the model to predict the probability of a landslide occuring at a given location using satellite data in addition to the data collected on the ground. Using these two datasets they were then able to develop a map which shows the probability of a landslide occuring.

## Conclusion
Despite the result not being as we'd hoped, I had a lot of fun. Spending two sleepless nights with some of my best friends is part of some of the best experiences in the past year. I learned a lot and I am looking forward to the next hackathon.