# Training Convolutional Neural Networks

## Loss Function
- Way to define model performance, allows u to optimize network parameters with a metric

### Gradient Loss/Descent Function
- Start at random point, compute gradient, move along curve in direction of negative gradient (amt moved on line is learning rate)
- Continue until we cant continue in negative direction anymore
- Guaranteed to find optimum for convex funcs and local optimum for non convex (most cv problems are non convex), works for multi variate funcs

- Cross entropy and Mean squared error are popular loss functions

### Backpropagation
- Take deriv of output, and find partial deriv of previous inputs
- Allows update of weights as you take gradients
- Can set gates to manage how gradients are passed
    - Distributor/add: splits up gradient weights between all inputs given
    - Router/max: 
    - Switcher/mul:

## Stochastic Gradient Descent
- Datasets typically are too large to apply gradient descent too
- Stochastic randomly samples a data point, and creates a mini batch of data "batchsize"
- Random inital W and learning rate and when not at min shuffle training set and for each data point/batch do gradient descent "per epoch"
- Loss will not locally decrease as your data points are random, but it will converge over time

### Momentum
- Adjust the gradient by weighted sum of prev amt and current amt

### Learning rate
- Slower it is, longer to get to optimum

## Fitting
- Overfitting: too many params, too complex of an understanding
- Underfitting: not enough params, too simple of an understanding
- More data: less chance to overfit 
- Regularization, dropouts, and early stopping can help to not overfit 
    - Regularization: penalize use of parameters to prefer small weights by adding costs to having higher weights (l1, l2, elastic net)
    - Dropout: random weights, stoachastically switch neurons off, hidden units can't co-adapt and become usefully independent (dropout chance usually of 0.5)

## Training step
- Set network, loss functions, and network params up 
- Prepare training data in batches
- Feedforward one batch
    - Check loss
    - Backpropagate gradients to update parameters

## CNN Variants

### Residual Networks
- Built for deep learning, fixes vanishing gradient issue by skipping connections

### Google Network
- Goes wider then deeper, focus on features and which are useful for efficiency

### Dense Network
- Dense connected CNN
- Concat features over summing them