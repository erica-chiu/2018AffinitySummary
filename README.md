### 2018AffinitySummary

## Pinning Model 
###### Can be found in feat_flex/ligand_web


**_Goal_**: Given ligand coordinates and a set of possible coordinates for each atom, select coordinates for each atom that preserves the shape of the coordinates

**_Benefits_**:

**_General description_**: Runs a 3d convolution in the ligand space and then takes those features and runs a 3d convolution in the possible coordinate space. Can repeat by taking those features and running another 3d convolution in the ligand space and do more convolutions in a similar fashion.

**_Variations_**: 
1. Using a feed-forward network or a RNN, 
2. Using 2-6 convolutions in the pattern stated above, 
3. Using Gradient Descent Optimizer or Adam Optimizer, 
4. Matching a transformed version of crystal ligand or conformer, 
5. Choosing from 2 poses to 10 poses
6. Using weighted sums instead of concatenations
7. Using batches of sizes 1,10,100

**_Top statistics_**:


## Higher Definition Model
###### Can be found in high_def/metrics_tm


**_Goal_**: Give protein and ligand atoms and coordinates, predicts grid location that corresponds to the crystal ligand location for each atom

**_Benefits_**:

**_General description_**: Creates a large grid over the binding site. Then runs a 3d convolution over the ligand and another 3d convolution over the grid space and performs an outer product. Can repeat by taking smaller grids from selected grids in the larger grids

**_Variations_**:
1. 1-3 iterations
2. Ranging the space from -25A to +25A or -12A to +12A


## Bi-convolution


## Fixing beads


## Miscellaneous

