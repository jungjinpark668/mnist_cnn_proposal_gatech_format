# Literature Surveyor Agent

## Role
Find and organize CNN/MNIST research papers, populate `references.bib`, and write `chapters/chapter2.tex` (Literature Survey chapter).

## Context
This is a Georgia Tech ECE Ph.D. dissertation proposal using `gatechthesis.cls`. The Literature Survey chapter is **mandatory** and must be a **minimum of 5 pages**, written as a comprehensive review of the field.

The current repo contains placeholder solar-energy content that must be **completely replaced** with CNN/MNIST literature.

## Reference Material
Read `proposal_md/02_literature_survey.md` for the intended structure and topics.

## Tasks

### 1. Build `references.bib`
- **Replace** all existing solar-energy entries in `references.bib` (root of repo)
- Add **15–25 references** covering:
  - Foundational CNN architectures: LeNet-5, AlexNet, VGGNet, GoogLeNet/Inception, ResNet
  - MNIST dataset and benchmarks (original LeCun et al.)
  - Key techniques: dropout, batch normalization, data augmentation
  - Optimizers: SGD with momentum, Adam, RMSProp
  - Activation functions: ReLU, variants (Leaky ReLU, ELU)
  - Pooling strategies, regularization (L2, early stopping)
  - Recent CNN advances and MNIST state-of-the-art results
- Use consistent BibTeX format (`@article`, `@inproceedings`, `@book` as appropriate)
- Include `doi` field where available

### 2. Write `chapters/chapter2.tex`
- **Completely replace** existing chapter2.tex content
- Use `\chapter{Literature Survey}` as the top-level heading
- Organize into logical `\section{}` and `\subsection{}` groupings:
  - History of neural networks and CNNs
  - CNN architecture components (convolution, pooling, fully connected)
  - Landmark architectures (LeNet → AlexNet → VGG → ResNet)
  - The MNIST dataset and digit classification benchmarks
  - Training techniques (dropout, batch norm, optimizers)
  - Current state-of-the-art and gaps
- Must be **minimum 5 pages** when compiled

### 3. Update `abbrevs.tex`
- Add acronyms relevant to the literature (keep existing ones if still needed):
  ```latex
  \newacronym{cnn}{CNN}{Convolutional Neural Network}
  \newacronym{mnist}{MNIST}{Modified National Institute of Standards and Technology}
  \newacronym{relu}{ReLU}{Rectified Linear Unit}
  \newacronym{sgd}{SGD}{Stochastic Gradient Descent}
  \newacronym{gpu}{GPU}{Graphics Processing Unit}
  \newacronym{bn}{BN}{Batch Normalization}
  ```
- Use `\gls{cnn}` / `\gls{mnist}` etc. in chapter text on first occurrence

## LaTeX Conventions (GT Format)

| Convention | Usage |
|---|---|
| Top-level structure | `\chapter{Literature Survey}` |
| Citations | `\cite{key}` or `\textcite{key}` — **NOT** `\citep{}` or `\citet{}` |
| Cross-references | `\ref{fig:label}` (auto-becomes `\autoref{}`) |
| Acronyms | `\gls{cnn}` on first use, then abbreviation auto-used |
| Bibliography engine | `biblatex` with `biber` backend |
| Figures | Place in `figures/` (repo root), use `\includegraphics{figures/...}` |
| Tables | Use `\resizebox` pattern from GT template |
| Units | `\SI{}{}` and `\si{}` from `siunitx` |

## Quality Standards
- Every factual claim must have a `\cite{}` reference
- No first person ("I", "we") — use "this work", "the proposed method"
- Active, concise academic tone
- Logical flow from broad context → specific problem space
- End with a clear identification of research gaps that motivate this proposal

## Compilation Check
After writing, verify the document compiles:
```bash
cd /path/to/repo
pdflatex thesis.tex
biber thesis
pdflatex thesis.tex
pdflatex thesis.tex
```

## Output Files
- `references.bib` (modified — all entries replaced)
- `chapters/chapter2.tex` (modified — complete rewrite)
- `abbrevs.tex` (modified — new acronyms added)
