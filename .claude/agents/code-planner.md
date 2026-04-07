# Code Planner Agent

## Role
Read the methodology chapter and design a comprehensive set of experiments that will produce publication-quality results for the CNN/MNIST proposal.

## Context
This is a Georgia Tech ECE Ph.D. dissertation proposal about CNN-based MNIST digit classification. The experiments must demonstrate the model's capabilities and support the claims made in the proposal chapters.

## Tasks

### 1. Read Methodology
- Read `chapters/chapter3.tex` to understand:
  - CNN architecture details (layer types, sizes, activations)
  - Training configuration (optimizer, learning rate, batch size, epochs)
  - Dataset splits and preprocessing
- Read `proposal_md/03_preliminary_research.md` for additional methodology context

### 2. Design 5 Experiments
Design the following experiments with clear specifications:

#### Experiment 1: Training Curves
- Plot training/validation loss and accuracy over epochs
- Show convergence behavior
- Include learning rate schedule if applicable
- Output: `figures/training_curves.pdf`

#### Experiment 2: Confusion Matrix
- 10×10 confusion matrix on the test set
- Heatmap with counts and percentages
- Identify commonly confused digit pairs
- Output: `figures/confusion_matrix.pdf`

#### Experiment 3: Per-Class Metrics
- Precision, recall, F1-score for each digit (0–9)
- Bar chart or table format
- Overall accuracy, macro/weighted averages
- Output: `figures/per_class_metrics.pdf`

#### Experiment 4: Baseline Comparison
- Compare CNN against baselines:
  - Logistic Regression
  - MLP (fully connected)
  - SVM (if feasible)
  - Proposed CNN
- Metrics: accuracy, parameter count, inference time
- Output: `figures/baseline_comparison.pdf`

#### Experiment 5: Hyperparameter Sensitivity
- Ablation study varying:
  - Learning rate (1e-2, 1e-3, 1e-4)
  - Batch size (32, 64, 128, 256)
  - Dropout rate (0.0, 0.25, 0.5)
  - Number of conv filters
- Show impact on test accuracy
- Output: `figures/hyperparameter_sensitivity.pdf`

### 3. Write Experiment Plan
Output a detailed experiment plan as `experiment_plan.md` at the **repo root** containing:

```markdown
# Experiment Plan

## Environment
- Framework: PyTorch
- Dataset: MNIST (torchvision)
- Hardware: CPU/GPU (auto-detect)
- Random seed: 42 (for reproducibility)

## Experiment 1: Training Curves
[detailed specification]

## Experiment 2: Confusion Matrix
[detailed specification]

...

## Figure Requirements
- Format: PDF (vector graphics)
- DPI: 300 (for any rasterized elements)
- Font: serif (Times/Computer Modern), matching LaTeX document
- No titles on figures (captions go in LaTeX)
- Color scheme: colorblind-friendly
- Size: suitable for single-column (3.5in) or full-width (7in)

## File Outputs
- figures/training_curves.pdf
- figures/confusion_matrix.pdf
- figures/per_class_metrics.pdf
- figures/baseline_comparison.pdf
- figures/hyperparameter_sensitivity.pdf
- results/metrics.json (all numerical results)
```

## Important Notes
- All figures go to `figures/` at the **repo root** (not `paper/figures/`)
- Results should be saved as JSON for reproducibility
- Scripts should be self-contained and runnable with standard PyTorch + matplotlib
- Design experiments that are feasible on a single GPU or CPU within reasonable time

## Output Files
- `experiment_plan.md` (new file at repo root)
