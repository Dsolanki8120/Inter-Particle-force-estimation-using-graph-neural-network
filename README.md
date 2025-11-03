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

