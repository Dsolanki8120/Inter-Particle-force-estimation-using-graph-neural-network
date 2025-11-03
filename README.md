#  Inter-Particle Force Estimation using Graph Neural Networks

This project builds a **physics-informed graph representation** of granular particle assemblies to estimate **normalized particle contact forces (NPMNCF)** using a **Graph Neural Network (GNN)** based on the **Encode–Process–Decode** architecture.

Inspired by the paper:  
> **"Estimation of Contact Forces in Granular Materials Using Graph Neural Networks"**

---

##  Overview

- Each **node** represents a particle (ball) with features like **radius**, **displacement**, and **coordination number**.  
- Each **edge** represents a contact between two particles, with features computed from **relative displacement** and **contact status**.  
- The network predicts **normalized particle contact forces** across timesteps in granular assemblies.

---

##  Repository Structure

├── graph.py # Graph construction and feature computation
├── model.py # Encode–Process–Decode GNN model
├── main.py # Training and evaluation script
├── data_sets/ # Input .tab files for assemblies
├── processed_graphs_and_targets.pt # Cached data
└── README.md


## Requirements

    pip install torch numpy pandas matplotlib
## Working Steps:

      1 Data Loading:
              Each timestep and assembly is loaded from .tab files using graph.py
              Node and edge features are computed as described in the paper “Estimation of Contact Forces of Granular Materials
      2 Graph Construction:
              Node features: [radius / max_r, coordination_number]
              Edge features: [contact_status, disp_along, disp_perp]
              Edges are created between particles in contact.
      3 Model Architecture:
             Implements the Encode–Process–Decode GNN:
             Encoder: MLP-based feature projection
             Processor: 7-step message passing (EdgeUpdate + NodeUpdate)
             Decoder: Predicts per-node normalized contact force

    4 Training:
            Normalizes node and edge features
            Uses L1, L2 loss, and Pearson correlation (ρ) for evaluation
            Optimized using Adam with gradient clipping 

    5 Evauluation:
            Tracks training/testing L1, L2, and correlation (ρ) metrics
# Running:
          python main.py

