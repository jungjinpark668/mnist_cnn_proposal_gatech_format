# Code Executor Agent

## Role
Implement and run the experiments defined in `experiment_plan.md`, generating publication-quality figures and results for the CNN/MNIST dissertation proposal.

## Context
This is a Georgia Tech ECE Ph.D. dissertation proposal. All generated figures must meet academic publication standards and integrate seamlessly with the `gatechthesis.cls` LaTeX template.

## Tasks

### 1. Read the Plan
- Read `experiment_plan.md` at the repo root for experiment specifications
- Read `chapters/chapter3.tex` for model architecture details

### 2. Implement Experiments
Create Python scripts using **PyTorch** and **matplotlib**:

- `scripts/train_model.py` — Train the CNN, save training history
- `scripts/run_experiments.py` — Run all 5 experiments, generate figures
- Or combine into a single comprehensive script

Requirements:
- Use `torchvision.datasets.MNIST` for data loading
- Set random seed (`torch.manual_seed(42)`) for reproducibility
- Auto-detect CUDA/MPS/CPU
- Save trained model checkpoint to `results/model.pth`
- Save all metrics to `results/metrics.json`

### 3. Generate Publication-Quality Figures

All figures must follow these specifications:

| Property | Requirement |
|---|---|
| Format | **PDF** (vector graphics) |
| DPI | 300 (for rasterized elements) |
| Font | Serif (Times/Computer Modern) — use `matplotlib.rcParams['font.family'] = 'serif'` |
| Title | **No titles** on figures (captions are in LaTeX) |
| Labels | Clear axis labels with units |
| Colors | Colorblind-friendly palette (e.g., `tab10` or custom) |
| Size | `figsize=(7, 5)` for full-width, `(3.5, 3)` for half-width |
| Legend | Inside plot or outside, no overlap with data |
| Grid | Light gray grid for readability |
| Line width | Minimum 1.5pt for visibility |

### 4. Output Files

All figures go to `figures/` at the **repo root**:

```
figures/training_curves.pdf
figures/confusion_matrix.pdf
figures/per_class_metrics.pdf
figures/baseline_comparison.pdf
figures/hyperparameter_sensitivity.pdf
```

Results saved to `results/` at the repo root:
```
results/metrics.json
results/model.pth
```

### 5. Integrate with LaTeX
After generating figures, update the relevant chapter files to include them:
- Add `\begin{figure}[ht]` blocks in `chapters/chapter3.tex` or `chapters/chapter4.tex`
- Use the GT figure pattern:
  ```latex
  \begin{figure}[ht]
      \centering
      \includegraphics[width=0.85\textwidth]{figures/training_curves.pdf}
      \caption[Training convergence]{Training and validation loss/accuracy curves over 20 epochs showing model convergence.}
      \label{fig:trainingCurves}
  \end{figure}
  ```
- Add corresponding tables using the GT `\resizebox` pattern:
  ```latex
  \begin{table}[ht]
  \centering
  \caption[Baseline comparison]{Classification accuracy comparison across model architectures on MNIST test set}
  \label{tbl:baselineComparison}
  \resizebox{0.8\textwidth}{!}{%
  \begin{tabular}{llll}
  \hline
  Model & Accuracy (\%) & Parameters & Inference Time (ms) \\ \hline
  Logistic Regression & 92.1 & 7,850 & 0.3 \\
  MLP & 97.8 & 669,706 & 0.5 \\
  Proposed CNN & 99.2 & 431,080 & 1.2 \\ \hline
  \end{tabular}%
  }
  \end{table}
  ```

## Important Notes
- **Never** use `natbib` commands (`\citep`, `\citet`) — this repo uses `biblatex` (`\cite{}`, `\textcite{}`)
- Figures directory is `figures/` at repo root, not `paper/figures/`
- If training takes too long, reduce epochs or use a smaller model variant
- All scripts should be runnable from the repo root: `python scripts/run_experiments.py`

## Compilation Check
After adding figures to chapters, verify compilation:
```bash
pdflatex thesis.tex && biber thesis && pdflatex thesis.tex && pdflatex thesis.tex
```
