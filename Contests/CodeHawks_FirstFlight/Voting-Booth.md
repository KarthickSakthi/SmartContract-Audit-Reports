# First Flight #6: Voting Booth - Findings Report

# Table of contents
- ## [Contest Summary](#contest-summary)
- ## [Results Summary](#results-summary)
- ## High Risk Findings
    - ### [H-01.  rewardPerVoter in _distributeRewards() is wrong](#H-01)




# <a id='contest-summary'></a>Contest Summary

### Sponsor: First Flight #6

### Dates: Dec 15th, 2023 - Dec 22nd, 2023

[See more contest details here](https://www.codehawks.com/contests/clq5cx9x60001kd8vrc01dirq)

# <a id='results-summary'></a>Results Summary

### Number of findings:
   - High: 1
   - Medium: 0
   - Low: 0


# High Risk Findings

## <a id='H-01'></a>H-01.  rewardPerVoter in _distributeRewards() is wrong            

### Relevant GitHub Links
	
https://github.com/Cyfrin/2023-12-Voting-Booth/blob/main/src/VotingBooth.sol

## Summary

 Calculation of rewardPerVoter in _distributeRewards() is wrong

## Vulnerability Details

in this logic ``` uint256 rewardPerVoter = totalRewards / totalVotes; ``` we're considering the **totalRewards** with **totalVotes**, **totalVotes** were the total number of voters who participated in this VotingBooth, So, once rewards distributed there is still remaining eth exist in the contract.

## Impact

The voters in **s_votersFor** will get only a small share due to considering the whole voters in this VotingBooth.

## Tools Used

Remix IDE
## Recommendations

Need to re-write the logic, by considering only the voters in s_votersFor. So the voters in s_votersFor will get a correct share of reward.

The else block in

```diff
+ uint256 rewardPerVoter = totalRewards / totalVotesFor;
- uint256 rewardPerVoter = totalRewards / totalVotes;
```
Green highlighted one is recommended
		





