# File Format Description

These files are **benchmark instances** for the **MCARPTIF-TP**. Some instances in the clustering directory (e.g., Act-IF-TP-b, Act-IF-TP-c, Cen-IF-TP-a, Cen-IF-TP-b, Cen-IF-TP-c, P2-IF-TP-a, P2-IF-TP-b, P2-IF-TP-c, and P2-IF-TP-d) are designed for multiple vehicles. Except for these, all files in this directory are for a single vehicle. 
The structure is as follows:

---

## File Structure

The file consists of two parts:

### 1. Instance Specification (Header Section)

This section contains keyword-value pairs that define the overall characteristics of the instance.  
Each line follows the format:

---

Typical keywords include:

| Keyword        | Description                                                              |
|----------------|--------------------------------------------------------------------------|
| `NAME`         | Unique identifier of the instance                                        |
| `NODES`        | Number of nodes in the network                                           |
| `REQ_EDGES`    | Number of required edges                                                 |
| `NOREQ_EDGES`  | Number of non-required edges                                              |
| `REQ_ARCS`     | Number of required arcs                                                  |
| `NOREQ_ARCS`   | Number of non-required arcs                                               |
| `CAPACITY`     | Capacity of each vehicle (first is volume, second is weight              |
| `DUMPING_COST` | Dumping cost of intermediate facilities: `IF 1, IF 2, IF 3, ...`          |
| `MAX_DURATION` | Maximum working time for each vehicle                                    |
| `DEPOT`        | Node ID of depot                                                         |
| `DUMPING_SITES`| Node ID of intermediate facilities: `IF 1, IF 2, IF 3, ...`               |
| `TURN_PENALTY` | Turn costs for each turn: 'straight, right-turn, left-turn, U-turn'|

---

### 2. Network Element Lists (Body Section)

After the `TURN_PENALTY` line, the file lists sets of edges and arcs that define the road network structure.

Each section of edges or arcs begins with a keyword row such as:

- `LIST_REQ_EDGES :`
- `LIST_NOREQ_EDGES :`
- `LIST_REQ_ARCS :`
- `LIST_NOREQ_ARCS :`

These lines act as section headers and are followed by the corresponding list of arcs or edges.

---

#### Format of Each Arc/Edge

Each arc or edge is defined in the following order:

| Field Name               | Description                                                                 |
|--------------------------|-----------------------------------------------------------------------------|
| `source node ID`         | Starting node of the arc/edge                                               |
| `target node ID`         | Ending node of the arc/edge                                                 |
| `service cost`           | Cost incurred when servicing the arc, including travel cost                 |
| `travel cost`            | Cost for traversing the arc without service                                 |
| `volume`                 | Volume of waste on this arc/edge                                            |
| `weight`                 | Weight of waste on this arc/edge                                            |
| `arc shape`              | Sequence of coordinates representing the shape of the arc, given as: <br> `x1 y1,x2 y2,x3 y3, ...` (coordinates are comma-separated)       |


---


## 📝 Notes

- All values are **tab-delimited**.
- Node IDs are integers.
- Travel costs, service costs, and demand are usually non-negative numbers.
- Non-required edges/arcs have zero service costs
- Not all sections may appear in every instance (e.g., some instances may have no required arcs).
- Since the sbi data is based on real-world measurements, the volume and weight values differ.
- In contrast, the Cen and Act instances are synthetic data generated from the MCARPTIF framework, and they assume identical values for volume and weight demand.
