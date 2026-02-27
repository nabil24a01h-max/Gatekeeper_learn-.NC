# Incremental SVM + Novelty Detection
Incremental fault diagnosis system for aerospace EMAs.

## Voting_comparison.ipynb
For the incremental SVM (no detection of novelty), we try different types :
1. Learn++.NC with basic votes
2. Learn++.NC with DW-CAV algorithm
3. Transfert of Support vectors between each expert and desactivation of old expert.
4. A mix of method 2 and 3
--> the best one being 3
   
## SVTransfer_v2.ipynb
Using the best method extracted from file Voting_comparison.ipynb in order to extract an output file (.pkl) to use on real system.

## test_plk_model.ipynb file
It allows to try the pkl file coming from the SVTransfer_v2.ipynb. But it does not contain the gatekeeper yet. 

## Author
Ahmad Nabil — Master's Thesis, Aeronautics Engineering, ULB (2026)

