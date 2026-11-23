# Movie Profit Analysis

Does a director's star power predict profit for high-budget movies, or does budget matter more?

## Files
- `clean_high_budget.csv`: merged, cleaned dataset (1,465 films, 35 columns)
- `clean_and_merge.py`: script that rebuilds it from `final_dataset.csv` and `full_data.csv`

## Sample definition
- USD budgets only, budget >= $50M, release years 1978-2025
- Films with gross under 5% of budget dropped (streaming/limited releases)

## Key columns
- `is_profitable`: 1 if gross_usd >= 2.5 x budget_usd (target)
- `roi`, `log_roi`: (gross - budget) / budget, and log(1 + roi)
- `prior_*`: director's track record BEFORE this film (no look-ahead)
- `oscar_prior_noms`, `oscar_prior_wins`: Oscar directing nominations/wins from earlier ceremonies only

## Do NOT use as predictors
`rating` and `votes_n` are measured after release and leak the outcome.

## Modeling notes
- Split train/test by year, not randomly
- Missing prior_* values are mostly debut directors; impute inside the training pipeline
