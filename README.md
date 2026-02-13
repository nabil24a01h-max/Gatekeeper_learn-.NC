# Gatekeeper_learn-.NC
Incremental fault diagnosis system for aerospace EMAs using Learn++.NC (SVM ensemble) and novelty detection (SVDD + confidence gatekeeper). Detects unknown faults while learning new classes without catastrophic forgetting.
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

### 2. Learn++.NC (Incremental Classification)
- Ensemble of SVM classifiers
- Each data batch → new expert (old experts unchanged)
- Weighted voting by expert accuracy
- No catastrophic forgetting

## Installation
```bash
pip install numpy pandas scikit-learn optuna matplotlib
```

## Usage
```python
from learnpp_nc import LearnPPNC
from gatekeeper import Gatekeeper

# Train classifier incrementally
clf = LearnPPNC()
clf.add_data(X_batch1, y_batch1, "Batch_1")
clf.add_data(X_batch2, y_batch2, "Batch_2")

# Setup gatekeeper
gk = Gatekeeper(nu=0.05)
gk.fit(X_train)
gk.set_classifier(clf)
gk.calibrate_thresholds(X_val, y_val, known_classes)

# Diagnose new sample
decision = gk.decide(x_new)
if decision.is_known:
    print(f"Fault class: {decision.predicted_class}")
else:
    print("Unknown fault detected!")
```

## Author

Ahmad Nabil — Master's Thesis, Aeronautics Engineering, ULB (2025)

