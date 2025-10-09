# Single Vehicle Residential Waste Collection Problem

## Introduction
Single vehicle residential waste colleciton problem can be defined as the mixed capacitated arc routing problems under time restrictions with intermediate facilities and turn penalties (**MCARPTIF-TP**).
This repository contains the **benchmark instances** and **experiment results** for the **MCARPTIF-TP** proposed in the paper "**Graph Partitioning-based Matheuristic for Residential Waste Collection Problem with Visual Attractiveness and Turn Penalty**". 
The file formats are described in the README file of each directory.


## Repository Structure and Guide

This repository is organized to clearly separate **benchmark instances** from **experiment results**, with each part containing its own documentation for clarity.

### 📁 benchmark_instances/

This folder contains all the benchmark instance files used for experiments.  
There are two subfolders:

- **[clustering/](benchmark_instances/clustering/)**: Contains 26 clustering instance files.
- **[routing/](benchmark_instances/routing/)**: Contains 75 routing instance files.

> All instance files in these subfolders follow the **same format**.  
> Please refer to **[Benchmark Instances Format](benchmark_instances/README.md)** for a detailed description of the instance file format.

---

### 📁 experiment_results/

This folder contains all result files generated from experiments, grouped into three main categories.

#### 📁 experiment_results/MCARPTIF-TP

This directory includes the main experimental results for the 'MCARPTIF-TP'. It consists of two subfolders:

- **[clustering/](experiment_results/MCARPTIF-TP/clustering/)**: Contains results from clustering algorithms.
- **[routing/](experiment_results/MCARPTIF-TP/routing/)**: Contains results from routing algorithms.

> **Note:**  
> The format of result files is **different** for clustering and routing.  
> For details about the result file format in each case, please refer to:
>
> - **[Clustering Results Format](experiment_results/MCARPTIF-TP/clustering/README.md)**
> - **[Routing Results Format](experiment_results/MCARPTIF-TP/routing/README.md)**

#### 📁 experiment_results/MCARPTIF

This directory contains the experimental results for the 'MCARPTIF' instances, where the turn penalty is assumed to be zero.
The experiments were conducted using the GPM algorithm, and the “Route Cost wo Turns” value in the result files represents the objective value of this solution.
These results can be directly compared with those in the 'MCARPTIF-TP' directory.

#### 📁 experiment_results/Sensitivity_Analysis

This directory includes the results of sensitivity analyses conducted on the 'P1-IF-TP-4' instance,
examining the effects of varying turn penalties and AOI (Arc Overlapping Index) tolerance parameters.

---

### 📄 Quick Navigation

- [Benchmark Instances Format](benchmark_instances/README.md)
- [Clustering Results Format](experiment_results/clustering/README.md)
- [Routing Results Format](experiment_results/routing/README.md)

---

If you have any questions about the file formats or folder organization,  
please see the relevant README linked above, or open an issue in this repository.
