# Network Analysis of Artists on Last.fm

This repository contains the final project for the Social Network Analysis course (University of Pisa, M.Sc. in Data Science and Business Informatics). The project focuses on building and analyzing a network of musical artists from the Last.fm platform based on their associated tags.

## Project Overview

Last.fm is a music tracking platform that logs users' listening history and associates metadata such as genres, moods, or contexts (via tags) with each artist. In this project, we built a **similarity network** where:

- **Nodes** = Artists  
- **Edges** = Weighted connections based on shared tags  
- **Weighting rule**: An edge exists between two artists if they share at least 3 out of 5 tags. Weights range from 1 to 3 depending on how many tags are shared.

The network was analyzed using several Social Network Analysis techniques and compared with standard synthetic models (Barabási-Albert, Erdős-Rényi).

---

## Topics Covered

### Data Collection
- Data retrieved from the [Last.fm API](https://www.last.fm/api)
- Over 10,500 artists collected using `chart.getTopArtist` and `artist.getInfo`
- Final dataset: 10,512 artists, each with 5 tags
- Network generated from shared tags (see `/data_collection/`)

### Network Characterization
- **Nodes**: 10,042
- **Edges**: 725,264
- **Avg. degree**: 144
- **Clustering coefficient**: 0.514
- **Density**: 0.014
- Compared against: Barabási-Albert and Erdős-Rényi models for robustness and structure

### Task 1 – Community Detection
- Algorithms used: **Label Propagation**, **Louvain**, **Leiden**, **Infomap**
- Evaluation metrics: Modularity, Conductance, Internal Edge Density (IED), Coverage
- Best results with **Louvain**, showing distinct genre-based communities
- Wordcloud visualizations of dominant tags per community

### Task 2 – Link Prediction
- Techniques tested:
  - **Common Neighbours**
  - **Adamic-Adar**
  - **Jaccard** (Best performance)
  - **SimRank**
- Metrics: Precision, Recall, Accuracy

### Task 3 – High-Order Network Analysis
- Hypergraph and Dual Hypergraph analysis:
  - Nodes: Artists or Tags
  - Hyperedges: Shared tag sets or artist groups
- Explored density and s-components across multiple thresholds
- Found that genre overlap is highly specific and affects network fragmentation

### Open Question
> *"How are artists’ communities structured in the tag-based network, what are the dynamics of centrality and interaction between musical genres, and what strategic roles do artists play within this network?"*

Findings include:
- Genres like **rap**, **electronic**, **indie**, and **pop** are most central
- Some artists (e.g., **Juno**) act as strategic bridges between otherwise disconnected parts of the network

---

## Authors
- Niccolò Seghieri  
- Pierfrancesco Benincasa  
- Biancamaria Bombino
- Guido Trentacapilli
