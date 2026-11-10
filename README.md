# CaseComp2026
BHDAC Case Comp
Acct1: Longest consecutive months in which a person’s credit account remained in good standing or active
Could potentially make binary- 0 for less than 25%, 1 for between 25 and 50%, etc.

Acct2: How many credit cards had some balance or activity within the last 3 months, excluding cards with serious unresolved credit problems

Acct3: Total number of credit accounts currently open (credit cards, student loans, auto loans, mortgages, etc.)

Acct4: Number of new credit accounts has opened within the past 3 months, not counting collection accounts

Acct5: How many months ago the person’s oldest credit account was opened

Acct6: Number of credit accounts that currently owe money (balance greater than $0)

Bad_flg_90plus_24m: binary variable that = 0 if the person defaulted 

Consumer_bad_flg_90plus_24m: binary variable that = 0 if the person defaulted (company-specific)

Potential variables to look at:
Acct1, Acct3, Acct5, Col1, Del4, Del6, Bad_flg

We took Del4, look at the total number of trades 30 or more days delinquent in the last 12 months and compare that to total number of open trades. Look at the proportion of total number of open trades that are delinquent?

Limit Acct5 to be < 12 months so that this variable matches up more appropriately with del4

Limit Del6 to be < 12 months too to compare with Del4: if a person has low months, we want to see if they are more likely to default because it shows they're currently doing poorly with their credit account

Possible methodology: use decision tree and recursive binary splitting 

First steps: create a subset of the dataset. We are investigating independent variables acct1, acct3, acct5, col1, del4, and del6. We will use one particular variable Del4-- the total number of trades 30 or more days delinquent in the last 12 months-- as somewhat of a driving factor to investigate the other variables. We hypothesize Del4 has predictive power in modeling the probability of those that will default (more delinquent trades = more risky credit behavior). Because we are using this as our basis, we want to restrict our other variables to be within the same time frame (12 months) and then use that time frame in our future regression/classification methods. 

Acct1 refers to the longest consecutive months in which a person's credit account remained in good standing/active. The minimum value is 0, while the maximum value is 99. Although this is a relatively reasonable value in this context, it appears that 99 is used as a placeholder when there is missing data (as in the same row, there are other 999... values for other columns that wouldn't make sense). THEREFORE, 99 will be replaced with the median. Also, because we want to restrict these numbers between 0 and 12, we can use min max scaling, with non-99 max value to correspond to a max value of 12. This variable is likely to possesss a magnitude of importance as del4, but as an inverse relationship instead (more months = less risky credit behavior).

Acct3 refers to total number of open trades. It is not entirely intuitive if a higher number of trades will equal more risky credit behavior-- likely to have less predictive power than the aforementioned variables. Once again, 99 will be replaced by the median.

Acct5 refers to how many months ago the person's credit account was opened. The min is 0 and the max is 9999-- need to replace 9999 values with median value instead. Will also need to use scaling to map values between 0 and 12, with the non-9999 max value corresponding to 12.

Col1 refers to total number of unsatsified collections (accounts that became very past due and were turned over to a collection agency/debt collector). It is intuitive reasoning that more collections = higher likelihood of defaulting. There does not seem to be an overwhelmingly strange values for this column.

Del6 refers to the number of months since the most recent 30 day delinquency on trades. The min is 0 and the max is 9996-- will use similar methodology as acct5 to compensate. This variable seems as if it would operate in tandem with Del4, in terms of its relationship with creditee with risky behavior (more months since delinquency = more risky creditee).


