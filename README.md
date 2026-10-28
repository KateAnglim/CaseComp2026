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
Acct1, Acct3, Acct5, Col1, Del4, Bad_flg

We took Del4, turn the total number of trades 30 or more days in the last 12 months into a proportion given the total number of trades ever and see if this proportion matches

