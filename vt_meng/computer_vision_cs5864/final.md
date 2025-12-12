# YEE HAW

NN basics
 - Activation functions
  - Sigmoid (squish 0-1)
  - tanh (quish -1-1)
  - ReLu (Negative samples become 0)
  - Leaky ReLu (Negative samples become 0.1x)
  - Maxout (take max of two different linearities)
  - ELU (smoother looking relu)
 - non-linearity from activation functions allows us to map inputs to a linearly separable feature space (can learn xor)
 - Hyperparameters
  - num layers, num units per layer
  - type of nonlinearity
  - type of loss function
  - regularization constant
 - loss functions
  - goal is to minimize loss function through gradient descent
  - Hinge loss
   - penalize if the difference in output of target class to other class doesn't meet a threshold, if threshold is met then no loss is incurred
  - weight regularization
   - impose regularization on loss to reduce size of weights
  - cross entropy
   - -log([e^s_yi]/[sum(e^s_j)])
  - triplet loss - minimize distance between anchor and positive samples and maximize distance from negative samples
CNN
 - based on convolutions
 - pass a learned filter (kernel) across image
 - each kernel in a layer results in an extra channel
 - output resolution depends on stride and padding
 - stride reduces resolution by 1/S (stride step)
 - computational complexity is F^2*K*K*L*W*H
 - 1x1 conv reduces number of channels - helps computation
 - depthwise conv
  - each channel gets its own learned kernel, can be ligher
 - max pool - get max value in kernel, usually used with stride > 1 to reduce dimensions
 - receptive field - how much of the input contributes to the output of a location
History of networks
 - AlexNet
  - similar to lenet-5
  - more data
  - max pool, relu
Table View
 - Memory - conv
 - params - FC
 - flop - conv
 - VGG
  - 3x3 convs all the way down, but deeper
  - much heavier than alexnet
 - GoogLeNet
  - deeeeeper
  - stem networks
   - aggresively reduce input resolution
  - global average pooling - take average of each channel to reduce to 1x1
  - auxiliary classifier help with distributing gradients to earlier layers
   - batchnorm fixes this issue
 - Inception v2 v3
  - added batchnorm
  - added factorziation of inception block
 - ResNet
  - deeeeeeeeeeeeper
  - residual module (skip connection)
   - add input to output of function
   - easier to model identity
 - Wide ResNet
  - shallow network, increase feature maps in each block
  - increases num params
 - ResNeXt
  - Increase cardinality (add multiple diff paths instead of one linear path with a skip con)
 - DenseNet - in each block connect everything
Dense prediction
 - FCN - start by downsampling then upsampling, FC layers are actually 1x1 resolution
 - transposed conv - filter paints the output, sum where filters overlap
 - backwards-strided conv - increase resolution with output stride > 1
 - output stride = fractional input stride 1/S
 - max unpooling - remember indices from pooling layer, output is sparse so followed by transposed conv layer
 - U-Net - similar to FCN, but fuse by concat and predict at end
 - FPN - use diff size resolutions to get low and high level context, predict dfferent sizes of bb from diff levels of pyramid
Object Detection
 - metrics - IoU (NMS to filter overlapping preds), mAP - calculate AP for each category, take mean of it
 - R-CNN - Region proposals + CNN, classify with SVM
 - Fast R-CNN - run entire image through CNN, get RoI. ROI-pooling. ROIs get passed through fc layer and loss is softmax loss and regression loss for bb, predict offset and bb
  - sample only two images per mini batch and many regions per image
 - Faster R-CNN
  - RPN - tile img with anchor boxes, try to pred if box contains obj
   - look at diff scales, aspect ratios
 - Mask R-RNN
  - Faster R-CNN and FCN in RoIs
  - ROI align
  - from RoIAlign, pred class label, bb, segm mask
 - YOLO
  - coause feature maps at 7x7resolution, at each location preduct score for each class and 2 bb with conf 
 - SSD - predict boxes of diff size at diff resolutions. each res has its own predictor
 - RetinaNet - class and box subnets, extension of FPN
 - Focal loss - downweight easy examples
 - FCOS
  - No anchors
  - instead, for each class, pred if location is in GT bb. positive points in grid, regress by bb L2 and centerness
Self-supervised
 - data prediction, transformation prediction, siamese methods
 - masked auto encoders, colorization, 
 - dialated/a trous conv - large sparse filters to downsample
  - increased receptive field with same computation/resolution
 - context pred - spatial patch, jigsaw puzzle, rotation pred
Optimization
 - Minibatch SGD - compute gradient of loss for minibatch and update params
 - LR decay - Exponential, Inverse, inverse sqrtm, linear, cosine
 - in practice, step decay and manual decay are used
 - Momentum - add Bm to weight update
 - adagrad - history of gradient magnitudes scale learning rate for each param, history is not forgotten so LR decays too fast
 - RMS prop - downweight older history of adagrad
 - adam - rmsprop and momentum
NN training
 - data aug - introduce transformations not sampled in the train data
 - zero - centering subtract mean image
 - subtract per-channel means
 - must perform same processing at test time
 - preprocessing good bc helps nonlinearity
 - weight init important to be random, xavier and kaiming
 - Batch Norm - shift/rescaling are differentiable, so nn can learn how to normalize
  - stats of outputs form layer can be approx by stats from minibatch
 - other types of normalization - layer norm, instance norm, group norm, weight norm
 - Regularization
  - L1, L2
  - weight decay
  - adding noise to inputs/weights
  - label smoothing
 - transfer-learning
 - distillation
  - use teacher network outputs to train student network to match the outputs using cross-entropy loss
 - fast gradient sign - find grad of loss with correct class, take element wise sign, and go in opposite direction
 - iterative gradient sign - same as above, but take smaller steps multiple times
 - least-likely image - push classifier to least likely image
Gans
 - KL divergence = D(P||Q) = sum_samples [P(x)log(P(x)/Q(x))]
 - JSD divergence = D(P||Q) = 1/2 D(P||M) + 1/2 D(Q||M)
 - NSGAN, maximize -log(D(G(x)))
 - optimal transport - transport plan times cost (primal form)
 - 1-Lipschitz function - how steep is the slope
  - derivative must be less than L (1)
 - can bound how different the output will be basedo en the inpuit
 - compare along a plan 
 - can lower bound the primal E_x(f9x) eyiueyfhuoiafh <= w(pl_r, P_theta)
 inception score - generate many different classes distinctly to get good score
Diffusion
 - forward process - turns noise to image
 -  backwards - turns image to noise
 - reparameterization trick - change sampling from random distributiong to X = mu + sigma epsilon (allows backprop)
 - forward process - get model to predict noise at timestep t

