# Protein Structure Classification Using Graph Neural Networks (GNNs) - Work in progress

## Overview

This project implements a pipeline for classifying protein structures using Graph Neural Networks (GNNs). The system fetches protein structure data from biological databases, converts 3D protein structures into graph representations, and trains GNN models (GIN or GAT architectures) for classification tasks.

## Architecture

### 1. Data Acquisition
1. **Uniprot to PDB Mapping**:
   - Input dataset contains Uniprot IDs with corresponding classification labels
   - Maps Uniprot IDs to Protein Data Bank (PDB) identifiers using Uniprot API
   - Handles cases of multiple structures or missing structures

2. **Structure Download**:
   - Retrieves PDB files in mmCIF format from RCSB database
   - Processes structures by selecting relevant chains and filtering components

### 2. Graph Representation

1. **Graph Construction**:
   - Converts protein structures to graphs using Graphein package
   - Nodes represent amino acids with various biochemical features
   - Edges represent spatial relationships or covalent bonds

2. **Graph Storage**:
   - Stores graphs in efficient formats compatible with GNN libraries
   - Maintains node features, edge connections, and graph labels
   - Supports batch loading for model training

### 3. Model Development

1. **GNN Architectures**:
   - Implements Graph Isomorphism Networks (GIN) for topology-aware learning
   - Includes Graph Attention Networks (GAT) for interaction weighting
   - Configures appropriate graph pooling operations

2. **Training Framework**:
   - Sets up data loaders for batch processing of protein graphs
   - Implements standard training loops with evaluation metrics
   - Supports common regularization techniques

## Structural representation - Graphein
Graphein provides utilities for a number of edge-construction schemes, which are organized into distance-based, intramolecular interaction-based, and atomic structure-based submodules. 
These edge construction methods are composable to allow for the creation of novel edge construction schemes. 

`Distance-based edge construction methods` include distance cutoffs, which create edges between nodes that are within a certain distance of each other, and k-nearest neighbors, which create edges between a node and its k nearest neighbors based on Euclidean distance.  
`Intramolecular interaction-based edge construction methods` include hydrogen bonds, which create edges between nodes that are involved in hydrogen bonding, and covalent bonds, which create edges between nodes that are covalently bonded.  
`Atomic structure-based edge construction methods` include van der Waals interactions, which create edges between nodes that are in close proximity to each other based on van der Waals radii, and electrostatic interactions, which create edges between nodes that have opposite charges.