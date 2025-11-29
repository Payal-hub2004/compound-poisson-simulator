# Sensitivity Analysis of Compound Poisson–Exponential Processes

## Project Overview
This project explores the **Compound Poisson Process** where jump sizes follow an **Exponential** distribution. This stochastic model is commonly used in Actuarial Science (Cramér–Lundberg model), Queuing Theory and reliability modelling.

The repository contains:
- A short theoretical derivation of the distribution of \(S(t)\).
- An interactive **R Shiny** app that simulates the process, demonstrates Central Limit Theorem (CLT) behaviour, and performs sensitivity analysis for the parameters \(\lambda\) and \(\theta\).
- Example visualizations and summary statistics.

---

## Mathematical Framework

The compound process is defined as:

\[
S(t) = \sum_{i=1}^{N(t)} X_i
\]

Where:
- \(N(t) \sim \text{Poisson}(\lambda t)\) is the counting process with rate \(\lambda\).
- \(X_i \sim \text{Exponential}(\theta)\) are i.i.d. jump sizes.

Conditional on \(N(t)=n\):

\[
S(t) \mid N(t)=n \sim \text{Gamma}(n, \theta).
\]

Unconditionally \(S(t)\) is a Poisson–Gamma mixture. The moment generating function (MGF) is:

\[
M_{S(t)}(s) = \exp\!\left(\lambda t \left(\frac{s}{\theta - s}\right)\right), \quad s < \theta.
\]

Mean and variance:
\[
\mathbb{E}[S(t)] = \frac{\lambda t}{\theta}, \qquad \mathrm{Var}(S(t)) = \frac{2\lambda t}{\theta^2}.
\]

---

## Visualizations & Insights

### Central Limit Theorem (CLT)
- **Small \(t\)**: distribution is skewed with mass at 0 (many simulations may have zero events).
- **Large \(t\)**: distribution tends to a Normal shape with mean \(\mu = \lambda t / \theta\).

### Sensitivity Analysis
- **\(\lambda\)** (inter-arrival rate): higher \(\lambda\) → more events → S(t) increases and converges faster to normality.
- **\(\theta\)** (jump-rate): smaller \(\theta\) → larger mean jump sizes (1/θ) → heavier tails and greater volatility.

---

## R Shiny Application

### Features
- Interactive sliders for \(\lambda\) and \(\theta\).
- Time selector: \(t = 10, 100, 1000, 10000\).
- Histogram of simulated \(S(t)\) with an optional Normal-approximation overlay.
- Real-time simulated vs theoretical mean/variance.

### Files
- `app.R` — main Shiny app (simulation + UI)
- `report.pdf` — (optional) project report and derivations
- `images/` — sample histogram images

---

## Quick Start — Run Locally

1. Clone the repository:

```bash
git clone https://github.com/<your-username>/compound-poisson-simulator.git
cd compound-poisson-simulator

