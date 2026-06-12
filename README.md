# FIFA World Cup 2026 Match Predictor

A match predictor I built for my CSE coursework, covering all 48 teams across the 12 groups of the 2026 World Cup. Pick any two teams and it predicts a scoreline and win probabilities using Poisson regression and Elo ratings.

**Live:** [garvitavarshney.github.io/FIFA-26-._.-predictor-](https://garvitavarshney.github.io/FIFA-26-._.-predictor-/)
**Repo:** [github.com/garvitavarshney/FIFA-26-._.-predictor-](https://github.com/garvitavarshney/FIFA-26-._.-predictor-)

[GitHub](https://github.com/garvitavarshney) · [LinkedIn](https://www.linkedin.com/in/garvita-varshney-b35858217/) · [Instagram](https://www.instagram.com/garvita._.varshney/) · [X](https://x.com/gvinjapiur)

---

## What it does

- Pick any two World Cup teams and get a predicted scoreline
- Win/draw/loss probabilities shown as bars
- Heatmap of every possible scoreline (0-0 through 5-5)
- Head-to-head history for teams that have met at past World Cups
- Browse all 48 teams across Groups A–L with match dates

---

## The model

I used Poisson regression, which is the standard approach for predicting football scores since goals are relatively rare, independent events.

```
expected_goals_home = team_avg_goals × (1 + elo_difference/4000 + home_advantage) × stage_factor
expected_goals_away = team_avg_goals × (1 - elo_difference/4000) × stage_factor
```

For every possible scoreline from 0-0 to 5-5, the probability is calculated using the Poisson formula, and these are summed to get win/draw/loss percentages.

Inputs to the model:
- **Elo rating** — a team strength score, similar to how chess ratings work
- **Average goals scored** — based on recent form
- **Home advantage** — small boost when not a neutral venue
- **Tournament stage** — knockout matches tend to be lower-scoring

---

## Files

```
fifa-predictor/
├── index.html   — the whole app, single file, no setup
└── README.md
```

No dependencies, no build step. Open the HTML file directly or host it.

---

## Deploying on GitHub Pages

1. Upload `index.html` to a repo
2. Go to Settings → Pages, set branch to `main`, folder to `/ (root)`, save
3. The link should be live within a minute

---

## Limitations

- Accuracy is roughly 50-55% for win/draw/loss prediction. This is actually typical for football — even professional betting models rarely go much higher because the sport is genuinely high-variance.
- Elo numbers and average goals are based on approximate current rankings, not pulled live from an API.
- A few debut teams (Curaçao, Jordan, Uzbekistan, Cape Verde) have limited World Cup history, so predictions involving them are less reliable.

---

## Possible next steps

- Pull historical match data from Kaggle instead of using fixed values
- Add the Dixon-Coles correction for low-scoring draws
- Use XGBoost to predict expected goals instead of a fixed formula
- Run a Monte Carlo simulation of the full tournament
- Build a Python/Streamlit version

---

## About

Built by Garvita Varshney, Sophomore, CSE, Manipal University Jaipur.

This is a learning project. If you spot an issue or have suggestions, feel free to open an issue or reach out.

[GitHub](https://github.com/garvitavarshney) · [LinkedIn](https://www.linkedin.com/in/garvita-varshney-b35858217/) · [Instagram](https://www.instagram.com/garvita._.varshney/) · [X](https://x.com/gvinjapiur)

---

© 2026 Garvita Varshney. Made as a college project — please don't submit this as your own work.
