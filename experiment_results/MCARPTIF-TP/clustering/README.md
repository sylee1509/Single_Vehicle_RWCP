# File Format Description

These files contain the **clustering solution output** for benchmark instances of the **MCARPTIF-TP**. Each file records the result of a single run using a particular algorithm (e.g., PUNCH). Each number in the filename corresponds to the following algorithms.

| Number | Method Name                   | Description                                                                 |
|---------|-----------------------------|-----------------------------------------------------------------------------|
| 1 | `MIP_CCP`              | Mixed integer programming model for capacitated p-median problem                                             |
| 2 | `METIS`              | Graph partitioning algorithm METIS (`Karypis & Kumar, 1998`)                                            |
| 3 | `METIS_MODIFIED`           | METIS + Iterative search                             |
| 5 | `INERTIAL_FLOW` | Graph partitioning algorithm Inertial Flow (`Schild & Sommer, 2015`)                                            |
| 6 | `INERTIAL_FLOW_MODIFIED`                   | Inertial Flow + Iterative search                           |
| 7 | `PUNCH`                   | Graph partitioning algorithm PUNCH (`Delling et al., 2011`)                             |
| 8 | `PUNCH_MODIFIED`                   | PUNCH + Iterative search              |
| 9 | `K_MEANS++`                   | Capacitated version of k-means algorithm (`Geetha et al., 2009`)                          |
| 10 | `SOTA_CCP`                   | State-of-the-art algorithm for the large-scale capacitated clustering problem (`Gnägi & Baumann, 2021`)                          |
| 11 | `PUNCH_CHAIN_IMP`                   | PUNCH + Iterative search + Chain Improvement                          |


---

## File Structure

The file consists of two parts:

### 1. Summary Section (Header)

This section provides the overall performance metrics and configuration of the solution.  
Each line corresponds to a different metric, separated by tabs.

| Field Name                   | Description                                                                 |
|-----------------------------|-----------------------------------------------------------------------------|
| `ClusteringMethod`              | Clustering Method                                             |
| `ComputationTime`           | Time taken to compute the clustering solution in seconds                            |
| `K` | The number of clusters obtained from the algorithm                                             |
| `K_LB` | The minimum number of clusters for this instance (calculated by $\lceil \frac{\text{total demand}}{\text{vehicle capacity}} \rceil$)                                             |
| `CCI`                   | Visual Attractiveness (Connected Component Index)                           |
| `NHO`                   | Visual Attractiveness (Normalized Hull Overlap)                             |
| `ATD`                   | Visual Attractiveness (Average Task Distance)              |
| `DMT`                   | Visual Attractiveness (Sum of Distances between Median and Tasks)                          |

---

### 2. Clustering Information Section (Body)

This section provides detailed information on the sequence of arcs visited by the vehicle(s) in the solution.

Each row corresponds to a segment in the route.

| Field Name         | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| `Starting Node`     | Source node of the segment                                                |
| `Ending Node`       | Target node of the segment                                                  |
| `Cluster`           | Index of assigned cluster (0, 1, 2, ... ); -1 for non-required arc/edge                        |
| `Required`         | 1 if this segment requires service; 0 otherwise                             |
| `Is Edge`           | 1 if this segment is an undirected edge; 0 otherwise                        |
| `Weight`           | Weight of waste collected from this arc/edge (0 if not required)            |
| `Volume`           | Volume of waste collected from this arc/edge (0 if not required)            |
| `Shape`            | Arc geometry (comma-delimited)                      |

---

## 📝 Notes

- All values are **tab-delimited**.
- Node IDs are integers.