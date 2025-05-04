# Protein Structure Classification Using Graph Neural Networks (GNNs)

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

## Usage Instructions

1. Prepare input file with Uniprot IDs and corresponding labels
2. Run data acquisition pipeline to fetch and process PDB structures
3. Convert protein structures to graph representations
4. Configure and train GNN model with appropriate parameters
5. Evaluate model performance on test set

## Dependencies

- Python 3.7+
- Biopython (for PDB processing)
- Graphein (for graph construction)
- PyTorch Geometric or DGL (for GNN implementation)
- Standard scientific stack (NumPy, Pandas)

## Expected Outputs

- Processed graph representations of protein structures
- Trained GNN models with evaluation metrics
- Visualization of important structural features (when using GAT)

## Applications

This pipeline can be adapted for various bioinformatics tasks including:
- Protein function prediction
- Enzyme classification
- Protein-protein interaction prediction
- Structural motif detection