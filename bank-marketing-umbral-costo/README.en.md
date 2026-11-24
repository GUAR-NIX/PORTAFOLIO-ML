🇪🇸 [Español (full version)](README.md) · 🇬🇧 **English (summary)**

# 📞 Who to call? Term-deposit campaign with ML

A model that decides **which customers a bank should call** to offer a term deposit, with a **calibrated** probability that they
accept and a **threshold chosen by the cost/benefit** of each call. Real telemarketing data from a Portuguese bank (UCI Bank
Marketing, **41 thousand customers**, 2008–2010, only 11% accept).

> ⚠️ **Before reading the figures:** the results below use a **stratified** 80/20 split, which is **optimistic** for this
> problem. In the test that does mimic real use (train on the past, predict the future), the AUC drops from **0.815** to
> **0.704**. The full README contains that temporal stress test.

## Results (test: 8,236 never-seen customers, stratified split)

| | Rule by segment | Logistic regression | **Calibrated LightGBM** |
|---|---:|---:|---:|
| AUC [95% CI] | 0.675 [0.658; 0.693] | 0.801 [0.784; 0.818] | **0.815** [0.798; 0.832] |
| Average precision (base rate 0.113) | 0.246 | 0.444 | **0.490** |
| Brier (lower is better) | 0.0898 | 0.0785 | **0.0751** |
| Subscriptions captured calling the top 10% | 27.7% | 44.4% | **47.4%** (lift 4.7×) |

LightGBM beats logistic regression on every metric, but the advantage is **small** (+0.014 AUC [+0.008; +0.020]): a well-built
logistic regression would be a defensible alternative if simplicity were a priority.

**In money** (assumptions: 8 USD per customer handled, 80 USD margin per deposit → 11% threshold):

| Policy on the test set | Called | Deposits captured | Net profit |
|---|---:|---:|---:|
| Call everyone | 100% | 100% | 8,352 USD |
| Rule: segments with rate > 10% | 64.1% | 84.5% | 20,488 USD |
| Calibrated logistic, p ≥ 11% | 20.7% | 64.8% | 34,440 USD |
| **Calibrated LightGBM, p ≥ 11%** | **18.8%** | **65.5%** | **36,256 USD (×4.3)** |

**What makes it different from a tutorial:** the most predictive variable (`duration`, the length of the call) is excluded
because it is **only known after calling**; probabilities are calibrated; and the threshold is economic, not 0.5.

**Temporal stress test, figures, API, limitations and reproduction commands:** [full README (Spanish)](README.md). Commands are
language-independent.
