Graph Classification(Proteins)
----------------------------------------------

Proteins is a molecular dataset for graph classification tasks. In this dataset, each graph represents a molecule such that nodes are atoms and edges are bonds. The labels are determined by the chemical functionalities of molecules. The protein dataset from TUDataset is a collection of graphs that represent the 3D structure of proteins. The dataset contains 1,113 proteins, of which 663 enzymes and 450 non-enzymes. The task is to classify a protein as an enzyme or a non-enzyme based on its graph representation.

In order to train this dataset, firstly, we implemented some models such as 
- Two-layer SAGEConv from DGL
- Three-layers GraphConv from DGL
- Three-layers  SuperGATConv

ihe above models are inefficient to train this completed dataset and the accuracy of all of them were insignificant. To now, the best model is Hierarchical Graph Pooling with Structure Learning (HGP-SL) model [Link](https://github.com/cszhangzhen/HGP-SL). The measurments of this model are  as below





## Evaluation
|Dataset   |Model       |Epoch| Time-inference    | Test Accuracy      |
|--        |--          |--   |---                |       --           |
|Proteins  |HGP-SL      |100  |0.550 $\pm$ 0.134  |  0.780 $\pm$ 0.029 |





The architecture of HGP-SL is designed to generate hierarchical representations of graphs, focusing on graph classification tasks. The core of HGP-SL is its graph pooling operation, which adaptively selects a subset of nodes to form an induced subgraph for the subsequent layers. This operation is crucial for learning hierarchical representations of graphs, as it allows the model to progressively reduce the complexity of the graph while preserving its topological information. To ensure the integrity of the graph's topological information, the HGP-SL introduces a structure learning mechanism. This mechanism learns a refined graph structure for the pooled graph at each layer. It is essential for maintaining the hierarchical representation of the graph, as it allows the model to adaptively adjust the graph structure to better capture the underlying patterns and relationships within the data.


### Requirements

    python==3.10.6
    dgl==1.1.2
    pytorch==2.0.1+cpu
    torch-scatter==2.1.1+pt20cpu
    torch-sparse==0.6.17
    torch-geometric==2.4.0