# Project: Insights on Vinho Verde Quality

## File Description

project1.ipynb: inference of tangible characteristics of wine from physicochemical properties
wine_sales.ipynb: drawing conclusions from a database of wine heuristics
wine_last.ipynb: the same, for a different database with slightly different columns.

## Description

Our client, BlueBerry Winery, a start-up wine maker from Portugal, have approached CODE Analytics to help them build a Wine Quality Analytics system which can help them determine the quality of wines produced based on ingredients and composition. Moreover, they are asking for concrete suggestions for their business model since their priority is to put a proper price tag for a bottle of wine so that there is no mismatch between quality and price. Their goal is to enter the business with a good amount of analytics and research on domain knowledge. More specifically, they are asking about insights on the *Vinho Verde* variety.

In order to reach the following conclusions, three datasets have been used:

• ((D1) from now on) A dataset with 1500 red and 5000 Vinho Verde wines, coming from [CCATR09]. For every wine, physicochemical (alcohol content, chlorides, sulphates, etc\.) and sensory (wine rating by a sommelier) data are given. 

• (D2) A dataset containing wine reviews. This dataset has informations about 150.930 wines from the entire world. 310 of those are from the Vinho Verde region (39 red and 271 white). This database does not contain physicochemical data, but only basic information about the wines, including rating and price. Source: Winemag.

• (D3) A second dataset containing wine reviews, very similar to the first one. 134 Vinho Verde, 13 red, 121 white. Source: https://osvinhos.blogspot.pt

There are some issues with the data, namely:

1) Due to privacy reasons, D1 does not give any geographical or winemaking details, and more importantly, no information about price or profit. This forced me to use the other two databases as comparison.

2) The other two databases, however, are limited in size, especially when it comes to red and rosé wines.

3) There is no information about the yield (e.g. of the different wine sorts) or the winemaking costs, which makes a profit analysis basically impossible.

4) D2 and D3 do not contain any information about physicochemical characteristics of the wine (apart from alcohol content, which is present in D3). 


## Specifications 

The program used was Python 3.7.7 with the main packages used being numpy, pandas, matplotlib, seaborn and scikit-learn; occasionally, collections, statsmodels, and nltk were also used.

## Results: first part (project1.ipynb)

First of all, I tried to use D1 in order to find out which physicochemical characteristics make a good Vinho Verde. First of all, I tried a simpler task, namely finding out whether the red and white wines in the database have significantly different characteristics. This simple classification exercise had the additional benefits of getting me at ease with the data and also in order to check whether the data are accurate (since the characteristics of red and white wines should be quite different from each other). The following approaches were tried:
a) Gaussian Naive Bayes,
b) K-nearest neighbors,
c) Logistic Regression,
d) Support Vector Machine Regression,
e) Random Tree Classification,
f) Random Forest Classification.

The methods gave an accuracy, respectively, of 97, 93, 99.1, 99.7, 98.3, and 99.6 percent. All methods were tested on cross-validation stability with all resulting in only minor fluctuations. Moreover, in all cases, the precision and recall values were quite similar.

To round up the red/white data, I calculated the main descriptive statistics of the two samples (red and white). The following conclusions were reached:

1) Volatile acidity is much larger in red wines than in white wines.
2) Citric acid is more present in red wines than in white wines.
3) The spread in residual sugar values is larger in white wines.
4) Red wines have significantly more chlorides.
5) White wines have significantly more SO2 (both free and total).
6) Red wines have more sulphates.
7) White wine quality is slightly higher. In particular, no red wine got the best grade (9).

Then, the main problem was tackled, namely the identification of characteristics that can help predict a wine's quality. First, D1 was split into three samples: low (grade <= 5), medium (grade 6 or 7) and high quality (grade 8 or 9). Descriptive statistics of these three subsamples made it clear that this classification problem would be much harder than the previous one, but that some characteristics did differ among the different wine classes, first of all alcohol content. This was made clear via a series of boxplots (shown in presentation 1), which in particular show that high-quality Vinho Verde has low density, high alcohol content, and low sulphates content. This was confirmed via a simple linear regression, which additionally showed that every indicator bar citric acid and chlorides is statistically significantly different between low and high-quality Vinho Verde (p<0.001).

Moreover, a polynomial regression of second degree was done as well, for all wines and separately for white and red ones. Two of the main results were that a red Vinho Verde with a high product of free SO2 and total SO2 tends to be of lower quality, while for white wines, the same is true for the product of chlorides and sulphates. However, when trying to predict a wine's rating, linear and polynomial regression get an accuracy rate of just 55 percent.

Therefore, it was necessary to try the machine learning techniques previously used again. The best turned out to be the random forest regression, which gave a 67,5 percent (when the wines were split in seven quality categories) or 82 percent (three categories).

Summing up, these were the main take-home messages from the first part:
a) Alcohol content is the most important single characteristic. A good Vinho Verde has a relatively high alcohol content.
b) Low SO2 is an excellent quality predictor for red Vinho Verde, while low chlorides and sulphates predicts a good white Vinho Verde.
c) Basically all of the physicochemical indicators are statistically significant, and therefore, throwing them away would be a mistake.

Other approaches I have tried that did not yield significant results:
1) Look at for which characteristics the mean value inside low-quality wines (or medium-quality, or high-quality, or white) diverges more (relatively) from the overall mean.
2) Pairplots possibly indicating which characteristics are the most correlated.
3) Full statistics panel with minimum, maximum, Q1-3, mean and SD of all characteristics.
4) Swarmplot of wines, divided in low-, medium-, and high-quality, by alcohol content.
5) Univariate boxplots of red and white wines.
6) Correlation matrix of all characteristics.
7) Scatterplots of three characteristics (x-axis, y-axis, hue), e.g. wine content-sulphates-quality.
