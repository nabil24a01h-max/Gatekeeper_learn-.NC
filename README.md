# Incremental SVM
Incremental fault diagnosis system for aerospace EMAs using Learn++.NC (SVM ensemble)/ SVs transfert and novelty detection (SVDD + confidence gatekeeper). Detects unknown faults while learning new classes without catastrophic forgetting.
# Incremental Fault Diagnosis for Aerospace EMAs

Intelligent fault diagnosis framework combining **incremental learning** and **novelty detection** for Electromechanical Actuators.

## Problem

Traditional ML classifiers:
- ❌ Can't detect unknown fault types
- ❌ Forget old classes when learning new ones
- ❌ Require full retraining with historical data

## Solution

Two-stage architecture:
```
Sample → [GATEKEEPER] → Known? → [LEARN++.NC] → Fault Class
              ↓
           Unknown → Flag for investigation
```

### 1. Gatekeeper (Novelty Detection)
- **SVDD** (One-Class SVM): geometric boundary in feature space
- **Confidence check**: max probability + margin between top-2 classes
- Decision: KNOWN only if both criteria pass

### 2. Learn++.NC/ SVs transfert (Incremental Classification)
- Ensemble of SVM classifiers
- Each data batch → new expert with a transfert of SVs
- No catastrophic forgetting

## Author

Ahmad Nabil — Master's Thesis, Aeronautics Engineering, ULB (2025)

