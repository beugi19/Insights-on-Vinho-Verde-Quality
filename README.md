# Project: Insights on Vinho Verde Quality

## File Description

project1.ipynb: inference of tangible characteristics of wine from physicochemical properties
wine_sales.ipynb: drawing conclusions from a database of wine heuristics
wine_last.ipynb: the same, for a different database with slightly different columns.

## Description

Our client, BlueBerry Winery, a start-up wine maker from Portugal, have approached CODE Analytics to help them build a Wine Quality Analytics system which can help them determine the quality of wines produced based on ingredients and composition. Moreover, they are asking for concrete suggestions for their business model since their priority is to put a proper price tag for a bottle of wine so that there is no mismatch between quality and price. Their goal is to enter the business with a good amount of analytics and research on domain knowledge. More specifically, they are asking about insights on the *Vinho Verde* variety.

In order to reach the following conclusions, three datasets have been used:

• ((D1) from now on) A dataset with 1500 red and 5000 Vinho Verde wines, coming from [CCATR09]. For every wine, physicochemical (alcohol content, chlorides, sulphates, etc\.) and sensory (wine rating by a sommelier) data are given. 

• (D2) A dataset containing wine reviews. This dataset has informations about 150.930 wines from the entire world. 310 of those are from the Vinho Verde region (39 red and 271 white). This database does not contain physicochemical data, but only basic information about the wines, including rating and price.

• (D3) A second dataset containing wine reviews, very similar to the first one. 134 Vinho Verde, 13 red, 121 white. Source: https://osvinhos.blogspot.pt

There are some issues with the data, namely:

1) Due to privacy reasons, D1 does not give any geographical or winemaking details, and more importantly, no information about price or profit. This forced me to use the other two databases as comparison.

2) The other two databases, however, are limited in size, especially when it comes to red and rosé wines.

3) There is no information about the yield (e.g. of the different wine sorts) or the winemaking costs, which makes a profit analysis basically impossible.

4) D2 and D3 do not contain any information about physicochemical characteristics of the wine (apart from alcohol content, which is present in D3). 


## Specifications 

The program used was Python 3.7.7 with the main packages used being numpy, pandas, matplotlib, seaborn and scikit-learn; occasionally, collections, statsmodels, and nltk were also used.

## Results: first part (project1.ipynb)


