# Computational Geometry — Algorithm Visualizations

This project contains interactive Jupyter Notebook visualizations of key algorithms in **computational geometry**, including convex hull construction, hierarchical data structures, and range searching.

All notebooks use **Matplotlib animations** (`FuncAnimation` → embedded HTML player) so you can step through each algorithm frame by frame.

---

## Contents

### 1. Dobkin–Kirkpatrick Hierarchy — `DK-hierarchy.ipynb`

Visualizes the **Dobkin–Kirkpatrick (DK) hierarchy** for 3D convex hulls.

- Iteratively removes an independent set of low-degree (≤ 8) vertices to build an $O(\log n)$-level hierarchy of progressively simpler convex hulls.
- Each level is rendered as a 3D subplot showing the hull polyhedron, retained vertices (blue), and removed vertices (red).
- **Parameters**: 20 random 3D points, seed 42.

### 2. Grouped Convex Hull Algorithm (3D) — `grouped-convex-hull-algorithm.ipynb`

Demonstrates a **hierarchical grouped convex hull** algorithm in 3D that combines:

- **Hierarchical grouping** at multiple levels based on $\lceil \log_2 \log_2 (3n-6) \rceil$.
- **Preparata–Hong** algorithm for computing local hulls within each group.
- **Dual DK hierarchy** for efficient tangent queries between groups.
- **Incremental gift wrapping** to merge local hulls face by face.

Includes:
- Static 3D plots of groups and their local hulls.
- **Gift wrapping animation**: for each edge, shows candidate tangent points from all groups, evaluates them, and selects the best to form the next face.
- Summary overview: original points → groups → final hull.
- **Parameters**: 100 random 3D points, seed 27.

### 3. 2D Grouped Convex Hull — `twoD-convexhull.ipynb`

2D version of the grouped convex hull algorithm using **Jarvis March (gift wrapping)** with per-group tangent queries.

- **Animation 1 — Grouping**: Groups of size $m = 2^{2^i}$ appear one by one with their local convex hulls.
- **Animation 2 — Gift Wrapping**: Each step shows the current vertex, dashed arrows to each group's tangent candidate, and the selected next hull vertex highlighted in green.
- Static summary comparing groups + local hulls vs. final global hull.
- **Parameters**: 30 random 2D points in $[0, 10]^2$, seed 42.

### 4. Orthogonal Range Search (KD-Tree) — `orthogonal_range_search.ipynb`

Implements a **KD-Tree** and uses it for axis-aligned rectangular range queries.

- **KD-Tree construction**: recursive median splits alternating x/y axes.
- **Range search**: visits each node and classifies it as *reported* (fully inside), *pruned* (fully outside), or *partially overlapping* (recurse deeper).

Includes:
- **Construction animation**: step-by-step display of each split line and the median point chosen.
- **Search animation**: colour-coded traversal — green (reported), red (pruned), yellow (visited / partial overlap), with the query rectangle in blue.
- Static summary: KD partition structure + query result.
- **Parameters**: 20 random 2D points in $[0, 10]^2$, seed 42; query rectangle $[2, 7] \times [3, 8]$.

---

## Requirements

- Python 3.8+
- NumPy
- Matplotlib
- SciPy
- IPython / Jupyter Notebook

```bash
pip install numpy matplotlib scipy jupyter
```

## Usage

Open any notebook in Jupyter or VS Code and **run all cells**. Animations are embedded as interactive HTML players — use the play/pause/step controls to explore each algorithm.
