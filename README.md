### 2018AffinitySummary

## Pinning Model 
###### Can be found in feat_flex/ligand_web


**_Goal_**: Given ligand coordinates and a set of possible coordinates for each atom, select coordinates for each atom that preserves the shape of the coordinates

**_Benefits_**: Learns shape preservation for either rigid ligands or conformers (faster than trying all possible combinations)

**_General description_**: Runs a 3d convolution in the ligand space and then takes those features and runs a 3d convolution in the possible coordinate space. Can repeat by taking those features and running another 3d convolution in the ligand space and do more convolutions in a similar fashion.

**_Variations_**: 
1. Using a feed-forward network or a RNN, 
2. Using 2-6 convolutions in the pattern stated above, 
3. Using Gradient Descent Optimizer or Adam Optimizer, 
4. Matching a transformed version of crystal ligand or conformer, 
5. Choosing from 2 poses to 10 poses
6. Using weighted sums instead of concatenations (for 
7. Using batches of sizes 1, 10, 30, 100
8. Random pins or random grids
9. Use grey map pins
10. Use top 2 or 10 beads from bead model as pins

**_Top statistics_**:
| Model | SeqTest Accuracy | SeqTest AUC | SeqTest RMSD |
| ----- | -------- | --- | --- |
| Feed-forward, 5 convolutions, crystal transformed, 2 poses, gradient descent | 0.8000001 | ~~ ~~ | 0.70817494 |

## Higher Definition Model
###### Can be found in high_def/metrics_tm


**_Goal_**: Give protein and ligand atoms and coordinates, predicts grid location that corresponds to the crystal ligand location for each atom

**_Benefits_**: Reduces amount of memory because doesn't need to calculate features for all possible grid locations

**_General description_**: Creates a large grid over the binding site. Then runs a 3d convolution over the ligand and another 3d convolution over the grid space and performs an outer product. Can repeat by taking smaller grids from selected grids in the larger grids

**_Variations_**:
1. 1-3 iterations (10 divisions, 2 divisions, 2 divisions)
2. Ranging the space from -25A to +25A or -12A to +12A
3. Using cross entropy loss or noise-contrastive estimation loss
4. Compared with just 20 divisions (equivalent to 2 iterations)
5. Combine with previous pinning model

**_Top statistics_**:


## Bi-convolution
###### Can be found in high_def/bi_conv


**_Goal_**: Given relative ligand coordinates, pin coordinates, and pin features, learn features from two different spaces 

**_Benefits_**: The features are invariant to ordering of the coordinates representing each of the spaces

**_General description_**: Performs a 3D convolution over the space of the original ligand atoms with pin features and then performs a second convolution with the new features over the space of the pins coordinates

**_Variations_**
1. Random grids (2.4A, 1.2A, .6A) for pins
2. Random coordinates for pins
3. Grey map for pins

**_Top statistics_**:



## Fixing beads
###### Can be found in high_def/fix_bead

**_Goal_**: Beads and ligand vector representations should be invariant to switching beads

**_Variations_**:
1. 1-3 convolutions
2. Model35 (euclidean distance) or Model38 (cosine distance)

**_Top statistics_**:




