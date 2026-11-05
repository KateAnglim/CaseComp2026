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

Variables to look at:
Acct1, Acct3, Acct5, Col1, Del4, Del6, Bad_flg

We took Del4, look at the total number of trades 30 or more days delinquent in the last 12 months and compare that to total number of open trades. Look at the proportion of total number of open trades that are delinquent?

Limit Acct5 to be < 12 months so that this variable matches up more appropriately with del4

Limit Del6 to be < 12 months too to compare with Del4: if a person has low months, we want to see if they are more likely to default because it shows they're currently doing poorly with their credit account

Possible decision tree: use random forest classifier and recursive binary splitting 