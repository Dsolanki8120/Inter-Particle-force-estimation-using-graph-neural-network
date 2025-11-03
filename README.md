Graph Neural Network for Granular Material Contact Force Estimation:

 This repository implements a Graph Neural Network (GNN) based on the Encode–Process–Decode architecture to estimate normalized particle contact forces (NPMNCF) in granular assemblies.
The implementation is inspired by the paper:

                       " Estimation of Contact Forces in Granular Materials Using Graph Neural Networks"
Overview:
      The project builds a physics-informed graph representation of granular particle assemblies where 
          Each node represents a particle (ball) with features like radius, displacement, and coordination number
          Each edge represents a contact between two particles, with features computed from relative displacement and contact status
Reopositroy Structure:

      ├── graph.py       # Graph construction and feature computation
      ├── model.py       # Encode–Process–Decode GNN model
      ├── main.py        # Training and evaluation script
      ├── data_sets/     # Input .tab files for assemblies
      ├── processed_graphs_and_targets.pt  # Cached data
      └── README.md

Requirements:

      pip install torch, numpy, pandas, matplotlib 
Working steps:

      1 Data Loading:

            Each timestep and assembly is loaded from .tab files using graph.py.
            Node and edge features are computed as described in the paper(Estimation of contact force of granular materials).

      2 Graph Construction:

            Node features: [radius / max_r, coordination_number]
            Edge features: [contact_status, disp_along, disp_perp] Edges are created between contacting particles.
      3 Model Architecture:

            The GNN follows the Encode–Process–Decode structure:

                Encoder: MLP-based feature projection
                Processor: 7-step message passing (EdgeUpdate + NodeUpdate)
                Decoder: Predicts per-node normalized force
      4 Training:
                Normalizes node/edge features
                Uses L1, L2 loss + Pearson correlation (ρ) for evaluation
                Uses Adam optimizer with gradient clipping (clip_norm=5)
      5 Evaulation:

                Tracks training and testing L1, L2, and correlation metrics.

Run training:

         python main.py


              
          

          


          
