# File Format Description

These files contain the **solution output** for benchmark instances of the **MCARPTIF-TP**. Each file records the result of a single run using a particular algorithm (e.g., GPM), vehicle configuration, and instance.

---

## File Structure

The file consists of two parts:

### 1. Summary Section (Header)

This section provides the overall performance metrics and configuration of the solution.  
Each line corresponds to a different metric, separated by tabs.

| Field Name                   | Description                                                                 |
|-----------------------------|-----------------------------------------------------------------------------|
| `Problem Type`              | Problem name (e.g., `MCARPTIF` or `MCARPTIF-TP`)                                            |
| `Solution Method`           | Name of the algorithm or solver used (e.g., `FULL MILP`, `GPM`, or `WJ19`)                            |
| `Vehicle Capacity (Weight)` | Vehicle capacity in weight                                             |
| `Vehicle Capacity (Volume)` | Vehicle capacity in volume                                             |
| `Disposal Trips`            | Number of disposal trips made                                  |
| `Route Time`                | Total route cost including turn penalties                                  |
| `Route Time wo Turns`       | Total route cost excluding turn penalties                                         |
| `Computational Time (Sec)`  | Time taken to compute the solution                                          |
| `Clustering Time (Sec)`     | Time taken for clustering for GPM                 |
| `VA(CCI)`                   | Visual Attractiveness (Connected Component Index)                           |
| `VA(NHO)`                   | Visual Attractiveness (Normalized Hull Overlap)                             |
| `VA(ATD)`                   | Visual Attractiveness (Average Task Distance)              |
| `VA(DMT)`                   | Visual Attractiveness (Sum of Distances between Median and Tasks)                          |
| `VA(AOI)`                   | Visual Attractiveness (Arc Overlapping Index)                                 |
| `VA(ROI)`                   | Visual Attractiveness (Route Overlapping Index)                                |
| `Optimal`                   | Whether the solution is proven optimal (1) or not (0)                       |

---

### 2. Route Log Section (Body)

This section provides detailed information on the sequence of arcs visited by the vehicle(s) in the solution.

Each row corresponds to a segment in the route.

| Field Name         | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| `Load No`          | Index of the subtrip (starting from 0)                    |
| `Sequence No`      | Visiting order in the subtrip                         |
| `Starting Node`     | Source node of the segment                                                |
| `Ending Node`       | Target node of the segment                                                  |
| `Is Edge`           | 1 if this segment is an undirected edge; 0 otherwise                        |
| `Required`         | 1 if this segment requires service; 0 otherwise                             |
| `Weight`           | Weight of waste collected from this arc/edge (0 if not required)            |
| `Volume`           | Volume of waste collected from this arc/edge (0 if not required)            |
| `Travel Miles`     | Distance of this segment                          |
| `Travel Time`      | Time to traverse this segment                  |
| `Service Time`     | Time spent servicing this arc/edge                                          |
| `Served`           | 1 if the arc/edge is serviced here; 0 otherwise                             |
| `Dumped`           | Time spent dumping waste at the start of this segment, if applicable; otherwise 0       |
| `Turn Type`        | Type of turn from the previous segment to this segment (`Straight`, `Left`, `Right`, `U`) <br> This field is left blank at depots or landfills.|
| `Turn Cost`        | Time penalty associated with the turn from the previous segment to this segment                               |
| `Depart Time`      | Time the vehicle departs from the start of this segment                     |
| `Arrival Time`     | Time the vehicle arrives at the end of this segment                         |
| `Shape`            | Arc geometry (comma-delimited)                      |

---

## 📝 Notes

- All values are **tab-delimited**.
- Node IDs are integers.
- `Turn Cost` is applied before `Depart Time` as the turn occurs at the start of the segment.
- `Turn Cost` is not applied to the **MCARPTIF**.
- `Served` and `Required` differ: a segment may be marked as required but not served if it was traversed multiple times.
- `Dumped` indicates waste was disposed of at the start of the segment.
