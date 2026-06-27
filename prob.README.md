# 🎯 Probability Bowl Model — World Cup 2026

Brier-score optimized Monte Carlo model for the Jump Trading Probability Bowl.

## What it does

- Pulls historical international results from [martj42/international_results](https://github.com/martj42/international_results) (49K+ matches, free)
- Removes bookmaker vig from market odds to get fair probabilities
- Blends market odds (65%) + historical team ratings (35%) for λ estimation
- Runs 300K Dixon-Coles corrected Poisson simulations
- Outputs every Probability Bowl prop with calibrated probabilities
- Player SOT calculator with role-based discounts (the Sangaré/Xhaka/Enciso edge)

## Setup

1. Open `probability_bowl.ipynb` in Google Colab
2. Run cells 1–6 once (setup, ~30 seconds)
3. Fill in Cell 7 with match odds + context for each match
4. Fill in Cell 8 with player props

## Data sources (all free)

| Source | What it provides |
|---|---|
| martj42/international_results | 49K historical results, updated daily |
| FanDuel / DraftKings | Moneyline + O/U odds |
| Transfermarkt | Referee card averages |
| Confirmed lineup news | Lineup-based adjustments |

## Key calibration rules

| Prop | Direction |
|---|---|
| Penalty / red card | Fade to 22–26% (crowd always overshoots) |
| Deep midfielder SOT | Fade hard (role discount 0.40) |
| Chasing team offsides | Boost ~15% above raw model |
| 2H more goals than 1H | Fade to 30–38% |
| BTTS + 3+ goals (competitive match) | Floor at 28% |

## Open in Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/poodlepal11/probability-bowl-model/blob/main/probability_bowl.ipynb)
