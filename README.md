## 2018AffinitySummary

# Pinning Model (feat_flex/ligand_web)
Goal: Given ligand coordinates and a set of possible coordinates for each atom, select coordinates for each atom that preserves the shape of the coordinates

General description: Runs a 3d convolution in the ligand space and then takes those features and runs a 3d convolution in the possible coordinate space. Can repeat by taking those features and running another 3d convolution in the ligand space and do more convolutions in a similar fashion.

Variations: Using a feed-forward network or a RNN, using 2-6 convolutions in the pattern stated above, using Gradient Descent Optimizer or Adam Optimizer, matching a transformed version of crystal ligand or conformer, choosing from 2 poses to 10 poses

Top statistics:


# Higher Definition Model



# Bi-convolution

