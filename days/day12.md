#  Unicode Normalization

This attack is hard to explain with out proper graphics. \
Please refer to the references mentioned for a detailed explanation. \
This is a really good attack vector to try and consider while doing PT/BB.

___
#### Unicode to ASCII Transformation is a two-step process
```
1. Normalization: Where the characters are converted to a standardized form

2. Punycoding: Where the Unicode is turned into ASCII
```
#### There are two overall types of equivalence between characters
```
1. Canonical Equivalence: Characters are assumed to have the same appearance and meaning when printed or displayed. 

2. Compatibility Equivalence: This is a weaker equivalence, in that two values may represent the same abstract character but can be displayed differently.
```
####  There are 4 Normalization AlgoDefined by Unicode Standard
```
1. Normalization Form D (NFD): Canonical Decomposition
2. Normalization Form C (NFC): Canonical Decomposition, followed by Canonical Composition
3. Normalization Form KD (NFKD): Compatibility Decomposition
4. Normalization Form KC (NFKC): Compatibility Decomposition, followed by Canonical Composition
```
#### Some Vulnerabilities that can be exploited using this abuse
```
1. WAF & Filter Bypass for Attacks like XSS, SQLi, etc.
2. Account Takeovers 
3. Text Transformation Attacks
```