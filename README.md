# Karate Club Network Analysis (Business Focus)

This project analyzes Zachary's Karate Club network to identify influential members, detect faction structure, and test network resilience. The framing targets business decision-making: who drives cohesion, how quickly the community fragments under churn, and where interventions are most effective.

## Business Question
If you are managing a club or customer community, which members most influence cohesion, and how vulnerable is the group to losing key people?

## Why This Matters
- Influence identification helps prioritize engagement and retention resources.
- Community structure reveals hidden subgroups for tailored communication.
- Resilience analysis highlights how quickly the network fragments under random churn versus targeted loss.

## What This Analysis Delivers
- Ranked influencers across multiple centrality metrics.
- A validated faction split based on graph structure.
- A resilience profile comparing random failures vs targeted removals.
- Business interpretations and recommendations tied to each phase.

## Dataset
- Built-in Karate Club network from NetworkX (`nx.karate_club_graph`).
- 34 nodes and 78 edges representing social ties within the club.
- Ground-truth faction labels are embedded in node attributes (`club`).

## Analysis Flow (Notebook Phases)
1. **Data Loading and Exploration**
   - Computes core network stats (nodes, edges, density, average degree).
   - Business interpretation: sets the baseline for operational impact.

2. **Centrality Analysis**
   - Measures degree, betweenness, closeness, eigenvector centrality, and PageRank.
   - Produces a top-5 influencer table per metric.
   - Checks correlation between centrality measures and identifies brokerage via Burt's constraint.
   - Business interpretation: identifies efficient influence levers.

3. **Community Detection**
   - Uses greedy modularity to detect communities.
   - Evaluates modularity, NMI, and accuracy against true faction labels.
   - Business interpretation: network structure can reveal group splits to guide communication.

4. **Network Metrics and Subgraph Comparison**
   - Compares full network to faction subgraphs on clustering, path length, and diameter.
   - Business interpretation: cohesion differences imply different engagement strategies.

5. **Robustness Simulation**
   - Simulates random failures and targeted removals.
   - Tracks largest component fraction, average shortest path, and number of components.
   - Business interpretation: targeted removals fragment the network faster.

6. **Visualization**
   - Centrality correlation heatmap.
   - Community-colored network layout.
   - Centrality scatter plot (degree vs betweenness).
   - Resilience curves (LCC and path length under node removal).

## Key Insights and Recommendations
- Focus engagement on top centrality members; they are the fastest levers for influence and stability.
- Use community structure to tailor messaging and reduce cross-group friction.
- Monitor shifts in betweenness or constraint for early warning of fragmentation risk.
- Prioritize retention of high-betweenness nodes to prevent sharp drops in connectivity.

## Project Structure
- `karate_analysis.ipynb` - Main analysis notebook.
- `plan.md` - Planning notes.

## How To Run
1. Open `karate_analysis.ipynb` in VS Code or Jupyter.
2. Run cells from top to bottom.
3. Review outputs and plots in each phase.

## Environment and Dependencies
This notebook uses standard data science libraries:
- `networkx`
- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `scikit-learn`
- `IPython`

Optional: create a virtual environment and install dependencies:

```bash
python -m venv .venv
.venv\\Scripts\\activate
pip install -r requirements.txt
```

## Reproducibility Notes
- Random seed is fixed (`RANDOM_SEED = 42`).
- Robustness simulations use `RANDOM_TRIALS = 100` and remove up to `MAX_REMOVE = 17` nodes.
- Results should be consistent across runs given the seed.

## Portfolio Context
This project demonstrates:
- Translating network science into business decisions.
- Exploratory analysis with clear metrics and visualization.
- Practical risk framing for churn and retention.

If you want a shorter executive summary or a one-page portfolio snapshot, the notebook already includes a business-focused summary section that can be lifted directly.