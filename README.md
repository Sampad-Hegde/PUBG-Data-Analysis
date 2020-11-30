# PUBG-Data-Analysis
Battle Royale-style video games have become quite popular in recent times. 
Player unknown’s battlegrounds (PUBG) is one of them where 100 players are dropped onto an island empty-handed and must explore, scavenge, and eliminate 
other players and the last one to survive wins, all while the play zone shrinks continuously. A total of 65000 games worth of anonymized player data that 
is split into training and testing sets is provided. Our goal is to predict final placement from final in-game stats and also to predict the best strategy to win PUBG. 
We have completed this job using random forest regression.


The prediction of win place percentage is an important factor in PUBG because a player can infer as to which strategy is best suited to win the game i.e. various feature 
importance’s can be taken into consideration for adopting a strategy. These types of problems are solved by doing extensive exploratory data analysis and data 
visualization before applying a regression model. We are provided with the Training Dataset so we divided it into Training and Validation Dataset in 70:30 ratio respectively. 


# Proposed Solution
Since the data was large, memory usage was an issue. We used memory reduction techniques to downcast the datatypes resulting in 75% memory reduction. 
In the process of pre processing firstly we looked for missing values and removed that value and also there was only one row with a missing value.
We started different features given to us and started removing the outliers wherever they were found. We plot a histogram for the feature and its log count and based on the graph we removed the outliers.
We used histogram over boxplot because we could draw better insights using histogram. 
As a part of feature engineering we converted the column ‘matchType’ from categorial to numeric by creating dummies so as to encode the different
values of that feature and thus using those features. Dummies are nothing but a binary variable which indicates whether the categorial
variable (generated from the values of the original variable) takes that value or no. Some features like matchId is only useful for feature extraction such as if
we need to find total players in a match. Since matchId is a hexadecimal string and it is not ordinal and has very high value count, we cant hot encode it as categorical.
We could also find it that matchId has very little predictive power.

# Models Used :
<b>Linear regression:</b> 
In our modelling process, we started off with a basic model to have a standard for more complex models.
We decide to try linear regression. .On training on the whole dataset we were ablr to get MAE=0.08985 R2=84.018%.
We were not satisfied with the results as the R squared value was not up to the mark.

<b>Decision tree :</b>
We thought of using regression tree algorithms and we fit our dataset to decision tree model. 
On predicting the output for our validation dataset and comparing it with our validation values, we found the MAE to be 0.08102 and R squared value was 85.708%. 
The results were not as we expected because our metrics are almost like our linear regression model

<b>Random Forest Regression</b>
We expected that random forest would work better as the model would not be on an assumption that the winPlacePerc is a linear combination of the inputs. 
At the cost of more time taken for fit, random forest is able to discover more complex dependencies. This model gave us an improvement, 
where MAE=0.06052 and R2=92.290. The scores were quite good, Since a man’s greed has no end,we decide to try LGBM(Light Gradient Boosting machime) 
because these boosting tree models work quite well with numerical and continuous variables which is entirely what our dataset is.

<b>LGBM :</b>
We found that this gradient boosting model worked best since it creates strong classifiers from many decision trees. 
LGBM is a whole model of decision trees which learns by fitting negative gradients which are called residual errors. 
LGBM has over 100 parameters but we have used only few which we found it necessary to prevent the model from overfit.

# Results 

<B>Linear regression</B><br/>
Mean Absolute Error is 0.08985	R2 score is 84.018%

<B>Decision tree</B><br/>
Mean Absolute Error is 0.08102	R2 score is 85.708%

<B>Random forest regression</B><br/>
Mean Absolute Error is 0.06052	R2 score is 92.290 %

<b>LGBM</b><br/>
Mean Absolute Error is 0.05448	R2 score is 93.766 %


