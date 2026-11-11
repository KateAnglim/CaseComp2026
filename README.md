# CaseComp2026
BHDAC Case Comp

Methodology: use decision tree classifier 

First steps: create a subset of the dataset. We are investigating independent variables acct1, acct3, acct5, col1, del4, and del6. We will use one particular variable Del4-- the total number of trades 30 or more days delinquent in the last 12 months-- as somewhat of a driving factor to investigate the other variables. We hypothesize Del4 has strong predictive power in modeling the probability of those that will default (more delinquent trades = more risky credit behavior). 

Acct1 refers to the longest consecutive months in which a person's credit account remained in good standing/active. The minimum value is 0, while the maximum value is 99. Although this is a relatively reasonable value in this context, it appears that 99 is used as a placeholder when there is missing data (as in the same row, there are other 999... values for other columns that wouldn't make sense). THEREFORE, 99 will be replaced with the median. This variable is likely to possesss a magnitude of importance as del4, but as an inverse relationship instead (more months = less risky credit behavior).

Acct3 refers to total number of open trades. It is not entirely intuitive if a higher number of trades will equal more risky credit behavior-- likely to have less predictive power than the aforementioned variables. Once again, 99 will be replaced by the median.

Acct5 refers to how many months ago the person's credit account was opened. The min is 0 and the max is 9999-- need to replace 9999 values with median value instead.

Col1 refers to total number of unsatsified collections (accounts that became very past due and were turned over to a collection agency/debt collector). It is intuitive reasoning that more collections = higher likelihood of defaulting. There does not seem to be any overwhelmingly strange values for this column.

Del6 refers to the number of months since the most recent 30 day delinquency on trades. The min is 0 and the max is 9996-- will use similar methodology as acct5 to compensate. This variable seems as if it would operate in tandem with Del4, in terms of its relationship with creditee with risky behavior (more months since delinquency = more risky creditee).

For the machine learning portion, we want to use decision trees as a classification method to determine which variables be most influential in determining what makes a person more risky, and compare that with if they do actually default on their loans. We are trying to maximize node purity-- a node is completely pure if all the observations in a particular node belong to the same category. So, we want to repeatedly split the data into smaller subnodes until the terminal leaf nodes are as pure as possible. That is, given a random creditee's information, we would be able to accurately classify if they default on their loan or not. The first portion of the machine learning section uses this basic decision tree classifier, and calculates what our maximum information gain will be. So for our first split, the variable that we split on will be pretty predictive on if a person is likely to default. For the second split, it will be slightly less predictive but still the 2nd most predictive variable, the 3rd split it will be 3rd most predictive, and so on. We will contain gaining monotonically less information from each split until we reach a stop limit.  

From the decision tree, we generate a classification report that tells us the precision, recall, and f1_score. Precision tells us: out of all the times we predicted a positive result, how many were actually correct?
Recall tells us: out of the actual positive items, how many did the model manage to find?
F1 score: This is the harmonic mean of precision and recall.

One important thing to note is to include class_weight = {0:1, 1:10} in the DecisionTreeClassifier. Note that a value of 0 for bad_flg consists of about 93.69% of observations, while a value of 1 for bad_flg consists of a mere 6.31%. There is way more observations for when the person did not default compared to when they did default. We add this term to tell the classifier to pay more attention to the underrepresented class, the people who did default. We will penalize errors when looking at the class of people who did default 10 times more heavily than when looking at the class of people who did not default. This statement also slightly increases f1 score.

The feature importances section gives us the importance of each predictor variable, and uses Gini importance, another method of determining how pure a node is. This basically measures how much each feature reduces node impurity across all the splits in the tree.

The random prediction section provides metrics for if we were to simply classify every observation as default or not default based on the proportion of default/not default cases we see in the dataset. For this mdoel, the f1 score for default is 0.07, which is significantly less than the f1 score for default for our model (0.30). This indicates our mdoel does a way better job at predicting probability of default than a random one would.

Next steps: how to improve f1 score further?




