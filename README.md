# Height vs Return Performance on Grass Courts (ATP 1991-2024)

<p align="center">
  <img src="figures/returner_height.png" width="550">
</p>

## 📍 Project Goal
Does being *very tall* actually hurt a player when returning serve on grass courts, where the ball skids and stays low?

## 📦 Data Source
* **Jeff Sackmann’s Tennis Abstract CSVs**  
  <https://github.com/JeffSackmann/tennis_atp>  
  • Tour-level singles only, 1991-2024, surfaces = Grass, Hard, Clay.

## 🛠 Pipeline
| step | notebook | output |
|------|----------|--------|
| 1. Load & clean | `notebooks/01_prepare_data.ipynb` | `matches_clean.parquet` |
| 2. Model & plot | `notebooks/02_returner_grass.ipynb` | `figures/returner_height.png` |

### Key engineered fields
* `ret_pct_diff`   = *(winner’s return %  − loser’s return %)*  
* `rank_diff`      = winner_rank – loser_rank (ability control)

## 📊 Main Findings
* On **grass**, there is a shallow **“comfort zone” around 1.78 m** (≈ 5′10″):  
  returners in that band concede ~1 % fewer points than both shorter (< 1.70 m) and taller (> 1.90 m) peers, after holding year & ranking constant.
* Above **1.90 m** the edge disappears; below **1.70 m** the disadvantage grows.
* On **hard** and **clay**, height helps: the curves rise steadily beyond 1.85 m.

Effect size: ≈ **1 return point per 100**—small but statistically significant  
(*mixed-effects model, p < 0.05*). Uncertainty widens for heights > 2.05 m because very few 2-meter giants play many grass matches.

## 🔁 Reproduce

```bash
git clone https://github.com/<your-user>/tennis-height-grass.git
cd tennis-height-grass
conda env create -f env.yml      # or  pip install -r requirements.txt
jupyter lab notebooks/02_returner_grass.ipynb
