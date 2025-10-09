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

This folder contains all result files generated from experiments, separated into two categories:

- **[clustering/](experiment_results/clustering/)**: Contains results from clustering algorithms.
- **[routing/](experiment_results/routing/)**: Contains results from routing algorithms.

> **Note:**  
> The format of result files is **different** for clustering and routing.  
> For details about the result file format in each case, please refer to:
>
> - **[Clustering Results Format](experiment_results/clustering/README.md)**
> - **[Routing Results Format](experiment_results/routing/README.md)**

---

### 📄 Quick Navigation

- [Benchmark Instances Format](benchmark_instances/README.md)
- [Clustering Results Format](experiment_results/clustering/README.md)
- [Routing Results Format](experiment_results/routing/README.md)

---

If you have any questions about the file formats or folder organization,  
please see the relevant README linked above, or open an issue in this repository.
