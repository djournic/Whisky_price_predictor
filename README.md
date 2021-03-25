# Phase3_Project

Welcome to my Phase 3 project: classifiers. Here I was tasked with finding my own data and solving my own problem regarding it.

I chose a whisky database from the website:
https://whiskyanalysis.com/index.php/database/

This met the requirements for an acceptable database, and I decided right away I wanted to create a model to successfully predict if a bottle was expensive or not. Luckily the data didn't need a lot of preprocessing before I got into the modeling except for one thing: many of the whisky names in the data also included ages (ex: 'Ardbeg 10yo') so it seemed like a good idea to take those names and make that another criterion for the models. That took a little work parsing the names of all the whiskies in the data, pulling out the ages and creating a column just for that. But ultimately it was done, but then not every whisky name followed that convention. I had to do more scouring of the data, and some research, eventually I was able to get an age to every whisky in the data.
Then I decided to drop the 'Super Cluster' column, it would create too many other columns when I created the dummies from it. I decided to use get_dummies as opposed to one hot encoder because it dealt with string variables better. Next, there were a significant number of null values in the 'Cluster' column, I decided simply to make them 'U' of Unknown or Undefined.
The actual modeling was probably the easiest part of it. I ran dozens of different models: decision trees, random forests, grid searches, ada boosts, gradient boosts, extreme gradient boosts, support vector machines, etc. Most of them scored pretty well, but a few models actually had an issue with predicting expensive bottles. It would get more wrong than it did right. But with the right hyperparameters and the right model, it turned out quite good. The simple decision tree, and the extreme gradient boost did the best.
Finally I wanted to get a list of recommendations from the model: a list of whiskies that are actually cheap, but that the model predicts to be expensive.
