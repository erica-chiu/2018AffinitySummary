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
11. Did preliminary tests with just triangles, squares and icosahedrons

**_Top statistics_**:


| Model | SeqTest Accuracy | SeqTest RMSD | SeqTest AUC |
| ----- | -------- | --- | --- |
| Feed-forward, 5 convolutions, crystal transformed, 2 poses, gradient descent | 0.8000001 | 0.70817494 | ~~ |
| Feed-forward, 2 convolutions, conformer, 2 poses, gradient descent, 2.4A grids | 0.9751578 | 2.1780472 | 0.9963048 |
| Feed-forward, 2 convolutions, conformer, 10 poses, gradient descent, 2.4A grids | 0.84553695 | 6.642 | 0.9758124 |
| Feed-forward, 2 convolutions, conformer, 2 poses, gradient descent, 0.6A grids | 0.98905164 | 0.69357973 | 0.9986486 |

More statistics can be found [here](PreliminaryTest.md).

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

**_Statistics_**:

| Model | SeqTest AUC |
| ----- | -------- |
| 1 layer cross entropy | 0.7612224 |
| 2 layer cross entropy | 0.7345741, 0.49980348 | 
| 3 layer cross entropy | 0.79310304, 0.5035895, 0.500349 |
| 1 layer nce | 0.80953294 |
| 2 layer nce | 0.80062085, 0.57625467 | 
| 3 layer nce | 0.8110932, 0.5955195, 0.5003045 | 
| 20 divisions | 0.65434194 |



## Bi-convolution
###### Can be found in high_def/bi_conv


**_Goal_**: Given relative ligand coordinates, pin coordinates, and pin features, learn features from two different spaces 

**_Benefits_**: The features are invariant to ordering of the coordinates representing each of the spaces

**_General description_**: Performs a 3D convolution over the space of the original ligand atoms with pin features and then performs a second convolution with the new features over the space of the pins coordinates

**_Variations_**
1. Random grids (2.4A, 1.2A, .6A) for pins
2. Random coordinates for pins
3. Grey map for pins
4. 2 different concatenations of ligand features
5. Cross entropy loss or swap loss

**_Top statistics_**:
| Model | SeqTest Accuracy | SeqTest RMSD | SeqTest AUC |
|---|---|---|---|
| Basic bi_conv on 2.4A grids | 0.8329366 | 7.4538136 | 0.9742352 |
| Initial ligand concatenation on 2.4A grids | 0.8538086 | 6.0495987 | 0.97240996 |
| No grids with 2nd ligand concatenation | 0.46637124 | 13.798717 | 0.8164979 |
| 0.6A grids | 0.9107372 | 5.179973 | 0.985856 |
| No grids 2 sets of bi_conv | 0.9323402 | 3.0136988 | 0.9805218 |
| Grey map swap | 0.35714287 | 3.4412975 | 3.4412975 |

## Fixing beads
###### Can be found in high_def/fix_bead

**_Goal_**: Beads and ligand vector representations should be invariant to switching beads

**_Variations_**:
1. 1-3 convolutions
2. Model35 (euclidean distance) or Model38 (cosine distance)

**_Statistics_**:
| Model | GoodBeadAcc | SeqBeadAcc | GoodBindAcc | SeqBindAcc |
|---|---|---|---|---|
| 1 Euclidean | 0.9789973 | 0.9841414 | 0.973965 | 0.9860906 |
| 2 Euclidean | 0.98313314 | 0.9812303 | 0.98346484 | 0.9756007 |
| 3 Euclidean | 0.9790819 | 0.98118925 | 0.98620284 | 0.95882887 |



For full statistics, click [here](http://saveresults.s3-website-us-east-1.amazonaws.com/model_sessions/ligand_tm) and [here](http://saveresults.s3-website-us-east-1.amazonaws.com/model_sessions/high_def).




