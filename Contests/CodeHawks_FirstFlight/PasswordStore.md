# First Flight #1: PasswordStore - Findings Report

# Table of contents
- ## [Contest Summary](#contest-summary)
- ## [Results Summary](#results-summary)
- ## High Risk Findings
    - ### [H-01. Not Owner user can able to update/set the Password in setPassword() in PasswordStore.sol contract](#H-01)




# <a id='contest-summary'></a>Contest Summary

### Sponsor: First Flight #1

### Dates: Oct 18th, 2023 - Oct 25th, 2023

[See more contest details here](https://www.codehawks.com/contests/clnuo221v0001l50aomgo4nyn)

# <a id='results-summary'></a>Results Summary

### Number of findings:
   - High: 1
   - Medium: 0
   - Low: 0


# High Risk Findings

## <a id='H-01'></a>H-01. Not Owner user can able to update/set the Password in setPassword() in PasswordStore.sol contract            

### Relevant GitHub Links
	
https://github.com/KarthickSakthi/smart-contract-testing/blob/master/test/CodeHawks/PasswordStore.js

## Summary

in PasswordStore.sol contract users who aren't Owner of the Contract can also be able to update/set Password using the setPassword() in the contract. 

## Vulnerability Details

1) in PasswordStore.sol contract users who aren't Owner of the Contract can also be able to update/set Password using the setPassword() in the contract. 

2) By 1) , if Owner try to get the Password via getPassword(), He will get the password that was updated the user who lastly updated the Password by setPassword().

3) in setPassword() There is no check and revert the transaction!

## Impact

if the contract is consumed by any Dapp, the user(not Owner) who updated the password can be able to access the assets and do actions as same as the Owner of the contract can able to do.

## Tools Used

I've used Hardhat to test the Contract

## Recommendations

in getPassword(),if the msg.sender is not the Owner, we check and revert the function call with Custom Error PasswordStore__NotOwner. The same thing need to be followed in setPassword() in contract

## How found the issue

in my Hardhat test script for this Contract , I've written 4 test cases. I found this via my third test case ("3. Should not set a password by an other than Owner") ,which was failed. remaining three were got succeed.

The Script that I written has provided in the above Relevant GitHub Links section.
		





