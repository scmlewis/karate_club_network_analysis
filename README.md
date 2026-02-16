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

## Key Figures (Summary)
- **Dataset:** 34 nodes, 78 edges, average degree 4.59, density 0.139; faction split 17 / 17 (Mr. Hi vs Officer).
- **Centrality:** degree and betweenness correlation r ~= 0.915; top brokerage (lowest constraint) nodes: 0, 33.
- **Community detection:** 2 groups; modularity ~= 0.400; NMI ~= 0.677; best-label accuracy ~= 0.94.
- **Structural comparison:** faction subgraphs show distinct clustering and path-length profiles vs full network.
- **Robustness:** first-step LCC 0.97 (random) vs 0.79 (targeted); targeted removals fragment faster.
- **Figures:** centrality correlation heatmap, community-colored network layout, degree vs betweenness scatter, resilience/path-length curves.

## Analysis Flow (Notebook Phases)
1. **Data Loading and Exploration**
   - Computes core network stats (nodes, edges, density, average degree).
   - Establishes the baseline size, sparsity, and faction balance.

2. **Centrality Analysis**
   - Measures degree, betweenness, closeness, eigenvector centrality, and PageRank.
   - Produces a top-5 influencer table per metric.
   - Checks correlation between centrality measures and identifies brokerage via Burt's constraint.

3. **Community Detection**
   - Uses greedy modularity to detect communities.
   - Evaluates modularity, NMI, and accuracy against true faction labels.

4. **Network Metrics and Subgraph Comparison**
   - Compares full network to faction subgraphs on clustering, path length, and diameter.

5. **Robustness Simulation**
   - Simulates random failures and targeted removals.
   - Tracks largest component fraction, average shortest path, and number of components.

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