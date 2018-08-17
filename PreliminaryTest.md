# Models

## integer square:
| Model | Explanation | Accuracy |
|:-----:|:-----------:|:--------:|
conv_rand_inp | Used random shape matching | 0.0122875
conv_basic | Used convolutions to create features | 0.52933125
conv_no_loc | Used no coordinate information | 0.533325
conv_less_mem | Used independent convolutions to reduce memory usage | 0.43043125
rnn_conv | Used RNN instead of feed-forward net | 0.56195625
rnn_no_loc | Used RNN and no coordinate information | 0.53053125
birnn | Used bidirectional rnn instead of feed-forward net | 0.542495


## float square:
| Model | Explanation | Accuracy |
|:-----:|:-----------:|:--------:|
conv_basic2 | Used convolutions to create features | 0.358625
conv_no_loc2 | Used no coordinate information | 0.360305
conv_basic_k15 | Used kernel size of 15 instead of 21 | 0.362722
conv_basic_k25 | Used kernel size of 25 instead of 21 | 0.37927225
conv_basic_pix5 | Used pixel size of .5 instead of .7 | 0.361384
conv_basic_pix9 | Used pixel size of .9 instead of .7 | 0.41228775
adam_conv_basic | Used adam optimizer as opposed to gradient descent | 0.3422775
add_conv_basic | Instead of concatenation, used weighted sum of pin combination | 0.3561075
add2_conv_basic | Instead of concatenation, used weighted sum of lig feats and pin coords | 0.35749
add3_conv_basic | Instead of concatenation, used weighted sum of pin feats and relative lig distances | 0.356545
add12_conv_basic | Combination of 1 and 2 | 0.3499175
add13_conv_basic | Combination of 1 and 3 | 0.3566525
batch_conv_basic | Batches in groups of 10 | 0.5996925
batch100_conv_basic | Batches in groups of 100 | 0.7342025
single_batch_conv_basic | Combined batches of 10 with min | 0.5141025
single_max_batch_conv_basic | Combined batches of 10 with max | 0.19069
batch_adam_conv_basic | Batches in 10 with adam optimizer | 0.5742675
more_conv_basic | Added another cross convolution to a total of 3 convolutions | 0.40216
rnn_conv2 | Used RNN instead of feed-forward net | 0.40108
rnn_no_loc2 | Used RNN and no coordinate information | 0.3743025
birnn2 | Used bidirectional rnn instead of feed-forward net | 0.22496
lstm_basic | Used LSTM for feature creation instead of convolutions | 0.142



## icosahedron:
| Model | Explanation | Accuracy |
|:-----:|:-----------:|:--------:|
conv_basic_iso | Used convolutions to create features | 0.4063
conv_no_loc_iso | Used no coordinate information | 0.4024625
rnn_conv_iso | Used RNN instead of feed-forward net | 0.444475
rnn_no_loc_iso | Used RNN and no coordinate information | 0.42755
birnn_iso | Used bidirectional rnn instead of feed-forward net | 0.14515975



### original_square:
- rnn_conv: 0.56195625
- conv_rand_inp: 0.0122875
- conv_basic: 0.52933125
- conv_less_mem: 0.43043125
- conv_no_loc: 0.533325
- rnn_no_loc: 0.53053125
- birnn: 0.542495 (50 hidden)



### adv_square:
- conv_basic: 0.358625
- birnn: 0.22496
- rnn_conv: 0.40108
- rnn_no_loc: 0.3743025
- conv_no_loc: 0.360305

### icos:
- conv_basic: 0.4063
- rnn_no_loc: 0.42755
- birnn: 0.14515975
- conv_no_loc: 0.4024625
- rnn_conv: 0.444475
 
### add_weights:
- 1: 0.3561075
- 2: 0.35749
- 3: 0.356545
- 1&2: 0.3499175
- 1&3: 0.3566525
 
### more models:
- more_conv: 0.40216
- adam_conv: 0.3422775
- lstm: 0.142
- rnn_batch_pix9: 0.83133

### batches:
- batch10_rnn: 0.8852425
- batch10: 0.5996925
- adam_batch10: 0.5742675
- single_batch10: 0.5141025
- single_max_batch: 0.19069
- batch100: 0.7342025

### pixels and kernels:
- k15: 0.362722
- k25: 0.37927225
- pix5: 0.361384
- pix9: 0.41228775
 

## Model explanations

Note: all models are used with float squares unless explicitly stated

|    Model      | Explanation | Accuracy |
|:-------------:|:-----------:|:--------:| 
10_5_conv_basic | Starts with 10 poses, goes to 5 poses, and then finally chooses a pose | 
adam_conv_basic | Used adam optimizer as opposed to gradient descent | 0.3422775
add_conv_basic | Instead of concatenation, used weighted sum of pin combination | 0.3561075
add2_conv_basic | Instead of concatenation, used weighted sum of lig feats and pin coords | 0.35749
add3_conv_basic | Instead of concatenation, used weighted sum of pin feats and relative lig distances | 0.356545
add12_conv_basic | Combination of 1 and 2 | 0.3499175
add13_conv_basic | Combination of 1 and 3 | 0.3566525
add23_conv_basic | Combination of 2 and 3 | too big
add123_conv_basic | Combination of 1, 2, and 3 | too big
batch_conv_basic | Batches in groups of 10 | 0.5996925
batch100_conv_basic | Batches in groups of 100 | 0.7342025
batch1000_conv_basic | Batches in groups of 1000 | too big
batch_adam_conv_basic | Batches in 10 with adam optimizer | 0.5742675
birnn | Used bidirectional rnn instead of feed-forward net (integer squares) | 0.542495
birnn2 | Used bidirectional rnn instead of feed-forward net (float squares) | 0.22496
birnn_iso | Used bidirectional rnn instead of feed-forward net (icosahedrons) | 0.14515975
conv_basic | Used convolutions to create features (integer squares) | 0.52933125
conv_basic2 | Used convolutions to create features (float squares) | 0.358625
conv_basic_iso | Used convolutions to create features (icosahedrons) | 0.4063
conv_basic_k15 | Used kernel size of 15 instead of 21 | 0.362722
conv_basic_k25 | Used kernel size of 25 instead of 21 | 0.37927225
conv_basic_pix5 | Used pixel size of .5 instead of .7 | 0.361384
conv_basic_pix9 | Used pixel size of .9 instead of .7 | 0.41228775
conv_less_mem | Used independent convolutions to reduce memory usage (integer squares) | 0.43043125
conv_no_loc | Used no coordinate information (integer squares) | 0.533325
conv_no_loc2 | Used no coordinate information (float squares) | 0.360305
conv_no_loc_iso | Used no coordinate information (icosahedrons) | 0.4024625
conv_rand_inp | Used random shape matching (integer squares) | 0.0122875
lstm_basic | Used LSTM for feature creation instead of convolutions | 0.142
more_conv_basic | Added another cross convolution to a total of 3 convolutions | 0.40216
rnn_conv | Used RNN instead of feed-forward net (integer squares) | 0.56195625
rnn_conv2 | Used RNN instead of feed-forward net (float squares) | 0.40108
rnn_conv_iso | Used RNN instead of feed-forward net (icosahedrons) | 0.444475
rnn_no_loc | Used RNN and no coordinate information (integer squares) | 0.53053125
rnn_no_loc2 | Used RNN and no coordinate information (float squares) | 0.3743025
rnn_no_loc_iso | Used RNN and no coordinate information (icosahedrons) | 0.42755
single_batch_conv_basic | Combined batches of 10 with min | 0.5141025
single_max_batch_conv_basic | Combined batches of 10 with max | 0.19069


### ligand:
- conv: train-0.211336666667, test-0.292093762416 (could run for longer)
- adam: train-0.24562, test-0.306924516532 (also could run for longer)

#### Preliminary Runs
|    Model      | Explanation | Train Accuracy | Test Accuracy | Average RMSD |
|:-------------:|:-----------:|:--------------:|:-------------:|:------------:|
ligand_adam | adam optimizer instead of gradient descent | 0.24562 | 0.306924516532 | |
ligand_adam3 | adam and 3 convolutions | 0.576979742173 | |
ligand_adam6 | adam and 6 convolutions | 0.167024174328 | |
ligand_conv | 2 convolutions | 0.211336666667 | 0.292093762416 | 13.436826244990032 |
ligand_conv3 | 3 convolutions | 0.376234096692 | |
ligand_conv4 | 4 convolutions | too big | |
ligand_conv5 | 5 convolutions | 0.396642808453 | |
ligand_conv6 | 6 convolutions | 0.0 | |
ligand_rnn | rnn instead of feed forward |  | |
ligand_rnn3_adam_pix9 | rnn, adam, 3 convoluations, pixel .9 | | |


#### Full Runs on xstream
Learning to find correct pose given original ligand coordinates and multiple random poses for each atom

|    Model      | Explanation | Train Accuracy | Test Accuracy | Train Average RMSD | Test Average RMSD | Last Batch Ran |
|:-------------:|:-----------:|:--------------:|:-------------:|:------------------:|:-----------------:|:--------------:|
0, fwd2 | feed-forward net with 2 convolutions and 2 poses, gradient descent optimizer | 0.303333333333 | .54 | 2.2899334 | 3.044272 | 83583
1, fwd3 | feed-forward net with 3 convolutions and 2 poses, gradient descent optimizer | 0.238888888889 | 0.493333333333 | 3.4184973 | 2.4580858 | 71899
2, fwd4 | feed-forward net with 4 convolutions and 2 poses, gradient descent optimizer | 0.261111111111 | 0.518888888889 | 3.2393553 | 2.30844 | 80299
3, fwd5 | feed-forward net with 5 convolutions and 2 poses, gradient descent optimizer | 0.434444444444 | 0.637777777778 | 1.9871486 | 1.4491253 | 69603
4, fwd6 | feed-forward net with 6 convolutions and 2 poses, gradient descent optimizer | 0.373333333333 | 0.577777777778 | 2.380698 | 1.8441339 | 69730
5, fwd_adam2 | feed-forward net with 2 convolutions and 2 poses, adam optimizer | 0.29 | 0.487777777778 | 3.1777396 | 2.4393547 | 66699
6, fwd_adam3 | feed-forward net with 3 convolutions and 2 poses, adam optimizer | 0.318888888889 | 0.511111111111 | 2.9273443 | 2.4509358 | 66785
7, fwd_adam4 | feed-forward net with 4 convolutions and 2 poses, adam optimizer | 0.498888888889 | 0.693333333333 | 1.7167966 | 1.2009867 | 65166
8, fwd_adam5 | feed-forward net with 5 convolutions and 2 poses, adam optimizer | 0.231111111111 | 0.537777777778 | 3.395176 | 2.3522975 | 62458
9, fwd_adam6 | feed-forward net with 6 convolutions and 2 poses, adam optimizer | 0.337777777778 | 0.501111111111 | 2.8802297 | 2.4606843 | 71999
10, rnn2 | rnn with 2 convolutions and 2 poses, gradient descent optimizer | 0.306666666667 | 0.517777777778 | 2.955842 | 2.2691903 | 34099
11, rnn3 | rnn with 3 convolutions and 2 poses, gradient descent optimizer | 0.463333333333 | 0.618888888889 | 1.839397 | 1.5545195 | 35341
12, rnn4 | rnn with 4 convolutions and 2 poses, gradient descent optimizer | 0.453333333333 | 0.602222222222 | 1.9027276 | 1.630737 | 34980
13, rnn5 | rnn with 5 convolutions and 2 poses, gradient descent optimizer | 0.351111111111 | 0.558888888889 | 2.7551725 | 2.0155606 | 32377
14, rnn6 | rnn with 6 convolutions and 2 poses, gradient descent optimizer | 0.363333333333 | 0.563333333333 | 2.4736986 | 2.0263968 | 33516
15, rnn_adam2 | rnn with 2 convolutions and 2 poses, adam optimizer | 0.332222222222 | 0.585555555556 | 2.7406085 | 1.950406 | 80611
16, rnn_adam3 | rnn with 3 convolutions and 2 poses, adam optimizer | 0.433333333333 | 0.614444444444 | 2.1726098 | 1.6305083 | 33255