# First Flight #4: Boss Bridge - Findings Report

# Table of contents
- ## [Contest Summary](#contest-summary)
- ## [Results Summary](#results-summary)


- ## Low Risk Findings
    - ### [L-01. Comment Should be clear](#L-01)


# <a id='contest-summary'></a>Contest Summary

### Sponsor: First Flight #4

### Dates: Nov 9th, 2023 - Nov 15th, 2023

[See more contest details here](https://www.codehawks.com/contests/clomptuvr0001ie09bzfp4nqw)

# <a id='results-summary'></a>Results Summary

### Number of findings:
   - High: 0
   - Medium: 0
   - Low: 1



		


# Low Risk Findings

## <a id='L-01'></a>L-01. Comment Should be clear            



## Summary
Whenever writing a comment or docstring for code, it should be clear about that function for the auditor to audit

## Vulnerability Details
 **L1BossBridge.sol**
   **depositTokensToL2 Function:**
   It seems the amount check for the deposit limit is done on the vault's balance, but the comment mentions that it's for the DEPOSIT_LIMIT. It might be more clear if you directly check against DEPOSIT_LIMIT.

## Impact
The auditor or other dev will be confused , if the comment not clear

## Tools Used
 None

## Recommendations
 The Dev should should review about his comments too, whether this will understand by other Dev or Auditor or not!


