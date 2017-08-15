# UNDERSTANDING DEEP LEARNING REQUIRES RETHINKING GENERALIZATION

# ON LARGE-BATCH TRAINING FOR DEEP LEARNING : GENERALIZATION GAP AND SHARP MINIMA

- Numerically experiment the difference between Large batch training and Small batch training to deep learning.
- Promising Results:
-- Large batch training will result in sharp minimizers, thus generalization worse than small batch training.
-- Plotting a  2D by f(\alpha x_l + (1-\alpha) x_s), which shows the relatively sharp and flat minimizers.
-- A heuristic methods to calculate maximal eigenvalues (or projection to another space), which also give evidence to larger eigenvalues of LB trained nets.
-- Rise steepy only along a small dimensional spaces (5%). other directions are relatively flat.
-- Warm start of SB will give better performance.
-- SB will give results farther away initial point, while LB closer.
-- Sharpness against to cross-entropy. LB and SB perform different, As the loss function reduces, the sharpness of the iterates corresponding to the LB method rapidly increases, whereas for the SB method the sharpness stays relatively constant initially and then reduces

- Training trajectory will not influence the final result very much, because of even differnet training trajectory will result in different local minima, whose generalization error does differ too much.


# AN EMPIRICAL ANALYSIS OF DEEP NETWORK LOSS SURFACES
- An emperical study to show that different optimization procedure will result in different local minima, which are seperated by high loss weight parameters, even the same initialization or switch method intermediately near convergent point. Compared different optimization methods, different methods result in different type local minima (large basin (ADAM) v.s. small basin(SGD))

- However, thia paper is a poor writing, it doesn't clarify the experiments' setting, which degrade the paper's quality.
- Some loss surface are training loss, while some are testing loss. we need to do experiments to clarify the result.

- To verify the result. we need to rerun experiments to get the training loss surface and test loss surface (I believe the result in this paper is true).
- The generalization ability may results from the small eigenvalue (large basin), so I want to compare the eigenvalues of differnent network architecture or different local minima within one same model.
- large basin: a small change to weight vector will not affect training error, will give some evidence to generation error?

# ADDING GRADIENT NOISE IMPROVES LEARNING FOR VERY DEEP NETWORKS
- A training technique which adds Annealled Gaussian Noise to the gradient while update weights, and gets bettern generalization error.

- Better test error and better validation error.
- Noise is something like exploration, thus we need annealled noise. SGD and noise injection, which one is better?
- Give us some experimental result that noise will help generalization. but not too much throty.

# ACCELERATING NEURAL NETWORK TRAINING BY LEARNING WEIGHT EVOLUTION
- The author evaluated the weight's evolution, used a NN to learn the training pattern from MNIST classification and utilize it to accelerate training of other NN used for CIFAR-10 and ImageNet classification. gets better performance.

- Weight's evolution pattern. many weights do not change too much (deviation and second moment relative to the initial point)
- The author trained a very simple NN (4*40*1) to predict future weights, this give evidence the weight's evolution pattern is kind of simple.
- from experiments curve, the validation loss and accuracy drops immediately after author apply Introspection, but arises quickly and reaches a better local minima. Author also conduct the noise injection experiment, shows that adding noise will not give better performace (I think comparative experiment is not sound enough, we need inject noise at the same time when apply Introspection).
- NN's weights exhibit some patterns (not change too much and consistently decrease or increase), will this give some insight to optimization procedure?

# DO DEEP CONVOLUTIONAL NETS REALLY NEED TO BE DEEP AND CONVOLUTIONAL?
- An empirical demonstration that deep convolutional models really need to be both deep and convolutional. the performace gap between conv and non-conv NN, deep conv and shallow conv.

- Bayesian Hyperparameter optimization approach, great~

- Only experiments that shows the importance of depth and convolution at DCNN.
- When we consider the generalization ability of NN, we also need to take account of the convolution and depth. Not all kinds of NN will have strong generalization ability.

# EIGENVALUES OF THE HESSIAN IN DEEP LEARNING : SINGULARITY AND BEYOND
- Many eigenvalues are centered at zero, only a few large eigenvalues.

- The paper is poor writting and very simple experiments (some fc NN and only 2-d data point), could not support the conclusion.

- the finding is interesting, and we could run additional experiments. I personally agree the findings

# INDUCTIVE BIAS OF DEEP CONVOLUTIONAL NETWORKS THROUGH POOLING GEOMETRY
- study the ability of CNN to model correlations among regions of their input.
- give insights of conv. and pooling operation w.r.t the regions?
- I am not fully understand the paper.

#
