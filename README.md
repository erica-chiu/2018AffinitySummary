## 2018AffinitySummary

# Pinning Model 
##### *feat_flex/ligand_web*


**Goal**: Given ligand coordinates and a set of possible coordinates for each atom, select coordinates for each atom that preserves the shape of the coordinates

**General description**: Runs a 3d convolution in the ligand space and then takes those features and runs a 3d convolution in the possible coordinate space. Can repeat by taking those features and running another 3d convolution in the ligand space and do more convolutions in a similar fashion.

**Variations**: 
1. Using a feed-forward network or a RNN, 
2. using 2-6 convolutions in the pattern stated above, 
3. using Gradient Descent Optimizer or Adam Optimizer, 
4. matching a transformed version of crystal ligand or conformer, 
5. choosing from 2 poses to 10 poses

Top statistics:


# Higher Definition Model
#### *high_def/metrics_tm*
Goal: Give protein and ligand atoms and coordinates, predicts grid location that corresponds to the crystal ligand location for each atom

General description: Creates a large grid over the binding site, runs a 3d convolution over the ligand and another 3d convolution over the grid space, performs an outer product, 

Variations: 


# Bi-convolution

