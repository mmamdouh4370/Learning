# Intro to Neural Networks
- Edges have been a big focus so far, but more feature extraction is needed
- We need to solve recognition, detection, and segmentation
- We want to recognize the image, specific details of the image, and separate what is what
- Feature engineering is expert knowledge, so we transfer to feature learning over datasets
- Large datasets are available to do so, we use a split between train and validation data with a backup test set not interfering with the main dataflow
    - Train is our base, cleaning data is most important here
    - Validation is what we use to measure error per epoch, model adjustments should be worked from here (lr, layers, etc)
    - Test is our "secret set" that has no same data as our train/val split, use this at the end of our training loop (or per epoch) to measure real error in real world app
- Features start very raw from raw pixels, data analysis, and sift descriptors, from there we develop learned features from shape and semantics

## Supervision of learning
- The way we pass our labeled data affects our model
- We need control over how fine we go into detail (recognizing a dog vs recognizing a dogs body parts)
- The more supervised the learning, the more fine

## Goal
- Essentially, produce a prediction function to a feature representation of the image to get the desired output
- Our training aims to estimate our prediction function f by reducing the prediction error

## Neurons
- Neurons receive input from multiple other neurons summing the inputs as they are received 
- Once a threshold in the neuron is hit, it sends all the inputs summed onto the next neurons
- We aim to emulate a neuron and its travel system with neural nets
- A neuron has dendrites to receive info, the neuron itself to process info, an axon to filter data, and axon terminal branches to send info out
- In the same way, we receive data, sum it, and have a neural activation function for our axon before sending data off
    - Sum, n = sum input * weight
    - Activation function, y = 1/1+e^-n (sigmoid activation can use anything)

## Neural Networks
- Basic building block for composition is a perceptron
    - Linear classifier: a vector of weights and a bias
    - Input in, weights per input and single bias, binary output
    - weight * input + b > or <= 0, output of 1 is <= else 0
    - Each pixel of an image is a input (28 x 28 img turns to a 784 vector)
- We add more perceptrons, input goes through each perceptron
    - The more perceptrons, the more weights (784 weights -> 784*10 for 10 perceptrons), we get a final vector of the amt of perceptrons 
      with answers per vector index
- We can save ops by moving bias into our weights vector, and passing in an input of 1 for every perceptron, now we just have input * weight

### Composition
- Ways to represent complex functions as smaller compositions of simpler functions
- Think a network of stacked perceptions to stacked perceptions etc
- *Sets of layers and the connection (weights) define the architecture* (count edges to count parameters)
- We can compose our network into a bunch of matrices, which will help us understand how to code our networks
- Ex: input 50 vals, one hidden layer (perceptron stack) of 100 neurons, and 100 class classifier would be 50 + 1 (1 extra input for save op), 
  * 100 + (100 + 1) * 100 = 15200

### Nonlinearities
- Problem so far, composition of linear functions is really a single function
- We can make this non linear by using the linear classifier property (small input change can cause large change in binary output)
- We make small changes in weight/bias overtime using non linear functions (sigmoid function!!! :D)
- Main activation functions:
    - Sigmoid: 1/1+e^-x 
    - Tanh: tanh(x)
    - ReLU: max(0, x)

- Pure perceptron models are very based in reality, and can represent a NAND circuit to build any other binary function
- Thus, given enough parameters any function can be approximated
- Yet, we want to do better and be more efficient
- Composition is efficient thanks to its reuse, deep networks do better than shallower networks

### Multi layer perceptron
- Fully connected neural network with non linear activation functions "feed forward"
- To get better from here, we have to get more power and make smthn more suited to specific problems