# Incremental SVM + Novelty Detection
Incremental fault diagnosis system for aerospace EMAs.
## How to use these file
On google colab, import these files and the data file (exp8 and exp9) and just run the code
## Voting_comparison.ipynb
For the incremental SVM (no detection of novelty),  different methods are tried :
1. Learn++.NC with basic votes
2. Learn++.NC with DW-CAV algorithm
3. Transfert of Support vectors between each expert and desactivation of old expert.
4. A mix of method 2 and 3

--> the best one being 3
   
## SVTransfer_v2.ipynb
Using the best method extracted from file Voting_comparison.ipynb in order to extract an output file (.pkl) to use on real system.

## test_plk_model.ipynb file
It allows to try the pkl file coming from the SVTransfer_v2.ipynb. But it does not contain the gatekeeper yet. 
## comparison files (static svm vs Svs transfert)
2 files (one in the scenario where we have new fault and one in the case where we just want to refine our svms) have been upload in order to compare a static svm with the one we implemented.
## GateKeeper (novelty detection)
...
## Author
Ahmad Nabil — Master's Thesis, Aeronautics Engineering, ULB (2026)

