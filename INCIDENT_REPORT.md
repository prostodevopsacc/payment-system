# Incident Report: Payment Commission Bug

## Bug Discovery
- Found using: ```sh git bisect run node test-payment.js```
- Problematic commit: 8a06214f33d5de734ed5993940eb7ad49c0b60d9
- Author: Portfolio Developer

## Root Cause
The bug was introduced in the "Optimize commission calculation" commit where:
1. Commission calculation was changed to return rate instead of amount
2. The comission was calculated wrong inside the function

## Fix Applied
- Reverted commit: 8a06214f33d5de734ed5993940eb7ad49c0b60d9
- Fix commit: 93389d19c333fe98137d2317b113a3ea95f6ccdb
- Verification: ```sh git bisect run node test-payment.js```

## Stash Usage
- Stashed work: ```commision.js analytics.js```
- Stash command used: ```sh git stash push -m "WIP: Progressive commission feature"```
- Recovery successful: Yes

## Reflog Recovery
- Lost commit: 28654bc
- Recovery command: git reset HEAD@{3}
- Restored SHA: 0343d48

## Lessons Learned
Научился черрипкать комииты вместо мерджить, когда это не надо. И пользоваться reflog. Также git blame очень полезный инструмент
