# segregation-by-design-experiments

Street-pattern, PT, and service-accessibility experiments.

## Scheme

```mermaid
flowchart LR
    A[Inputs] --> B[Run: run_street_pattern_city.py]
    B --> C[Checked outputs]
    C --> D[Paper / thesis use]
```

## Main Result

![Main result](outputs/storyline_street_pattern_atlas.png)

## Run

Entrypoint: `run_street_pattern_city.py`

Human:

```bash
python run_street_pattern_city.py --place "Portland, Oregon, USA" --buffer-m 5000 --grid-step 500 --device cpu --output outputs/portland_summary.json
```

Agent:

Inspect summary JSON and map PNG; do not claim pattern results from logs alone.

## Publication

No standalone publication tracked; thesis integration in parent repo.

## Next Steps / Heuristics

Heuristic: morphology context is the north star; keep mechanism experiments separate from production pipeline.
