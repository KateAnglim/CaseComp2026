# CaseComp2026
BHDAC Case Comp

Methodology: uses decision tree classifier to classify whether someone will default 

Uses variables Acct1, Acct3, Acct5, Col1, Del3, and Del6 as independent variables.
Consumer_bad_flg_90plus_24m as dependent variable.

Cleans relevant variables before building tree by replacing exceptional values with the median.

Generates decision tree, classification report, and confusion matrix.

Identifies most important variables (highest predictive power) in the classification algorithm;
top variables are Col1, Acct1, and Del6.

Attempts random forest classifier-- but results are worse. Use baseline model.

We may need more observations where a person does default to further improve model accuracy.





