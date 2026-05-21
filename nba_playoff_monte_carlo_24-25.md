# NBA Playoff Monte Carlo Simulator

Simulates the NBA playoff bracket 10,000 times to estimate each team's championship probability.

## Method

Each series is modeled as a sequence of independent Bernoulli trials. The probability that team A beats team B in a single game is derived from their Elo ratings:

```
P(A wins game) = 1 / (1 + 10^((elo_B - elo_A) / 400))
```

Home-court advantage adds +70 Elo points to the higher seed for games 1, 2, 5, and 7. After each round the bracket reseeds (lowest vs highest remaining seed), matching the real NBA format.

## What's inside

The notebook has 9 sections:

1. Team data - 2024-25 playoff field with estimated Elo ratings
2. Simulation engine - `win_prob()` and `simulate_series()` functions
3. Full bracket simulator - `simulate_bracket()` with conference reseeding
4. 10,000 simulations
5. Championship probability chart by team
6. Series length distribution (OKC vs Cleveland)
7. Sensitivity analysis - how OKC's title odds shift as their Elo changes
8. Summary statistics


## Results (2024-25 field)

OKC enters as the heavy favorite (~26% title probability) given their #1 West seed and top Elo rating. The West sends stronger teams overall, so Eastern Conference teams win the title roughly 38% of the time combined.

## Requirements

```
numpy
pandas
matplotlib
seaborn
scipy
jupyter
```

Install with:
```bash
pip install numpy pandas matplotlib seaborn scipy jupyter
```

## Run it

```bash
jupyter notebook nba_playoff_monte_carlo.ipynb
```

## Extensions

