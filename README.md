# Whisky Price Predictor

Whisky: Nectar of the Gods. Fuel for writer's.
What hasn't been said about whisky while musing quietly by a fireplace, or screaming from the back of a squadcar?

In case it hasn't become clear by now, I'm a bit of a whisky drinker myself. What appealed to me about whisky was what didn't appeal to me about beer: all beers basically tasted the same to me and it seemed so 'manufactured', whereas each whisky had its distinct flavor and had some more craftsmanship in its creation.
The problem is whisky varies pretty wildly in price from the 'celebrating your Nobel Prize' ($500+ per bottle) to the 'alcohol fueled rampage' (~$20 per bottle). The trick is to find a relatively cheap bottle of whisky that's still really good. Like with most things, computers can help us with that.

![Alt Text](https://tenor.com/view/drinking-whiskey-pour-alcohol-gif-14134639.gif)

Welcome to my project: classifiers. Here I tried to find out if you could predict if a bottle of whisky was expensive or not (expensive being $100+).
## The Data:
I found a whisky database from the website:
https://whiskyanalysis.com/index.php/database/
It's also useful to know how to read the data:
https://whiskyanalysis.com/index.php/interesting-correlations/how-to-read-the-database/

## The (Pre)Process

This met the requirements for an acceptable database. Luckily the data didn't need a lot of preprocessing before I got into the modeling except for one thing: many of the whisky names in the data also included ages (ex: 'Ardbeg 10yo') so it seemed like a good idea to take those names and make that another criterion for the models. That did take some work parsing the names of all the whiskies in the data, pulling out the ages and creating a column just for that. But ultimately it was done, but then not every whisky name followed that convention. I had to do more scouring of the data, and some research, eventually I was able to get an age to every whisky in the data.
Then came more data cleaning; I decided to drop the 'Super Cluster' column, it would create too many other columns when I created the dummies from it. I used get_dummies as opposed to one hot encoder because it dealt with string variables better. Next, there were a significant number of null values in the 'Cluster' column, I decided simply to make them 'U' of Unknown or Undefined.

## The Methods

The actual modeling was probably the easiest part of it. I ran several different models: decision trees, random forests, grid searches, ada boosts, gradient boosts, extreme gradient boosts, support vector machines, etc. Most of them scored pretty well, but a few models actually had an issue with predicting expensive bottles. It would get more wrong than it did right. But with the right hyperparameters and the right model, it turned out quite good. The simple decision tree, and the extreme gradient boost did the best.
Another aspect of this becamse clear: this could also be used to find bargains: a whisky that would typically be expensive (or predicted to be) and actually wasn't. So I compiled a short list of whiskies that meet that criteria. And I can say from experience some of these are good, and not very expensive.

![Alt Text](https://media3.giphy.com/media/mZQhT9Ey4tpgA/giphy.gif?cid=ecf05e472cqf6uiu99ucfyte9qdsfguhy4fqgjw6j9wdjdxs&rid=giphy.gif&ct=g.gif)

That said, enjoy I hope you find this useful, and cheers.
