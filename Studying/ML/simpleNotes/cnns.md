# Convolutional Neural Networks

- Class of neural nets that typically take an image as input, and give prediction(s) about the input
- Also used for NLP, audio research (speech through spectrograms), and converting data to a matrix format
- Dims end up being img input dim * num of convolutions
- Convolution filter/kernels of smaller dim then img go through image returning 1 num per run
- Our convolutions are known as our "weights" in the network
- This then becomes a activation/feature map (note, if we have uneven dims our final act map will be under the img dim ie 3x3x3 conv and 
  32x32x3 img, 3 fits into 32 only 10 times so activation of 30x30x1) (remember, 32x32x3 bcz rgb)
- Since we have multiple convolutions, we end up having multiple activation maps, and the sequence of these maps is a convolution network
- Total parameters is conv dims * num of conv kernels

## Convolution operation
- Given two "box functions" (spike up flat spike down) of our function f(t) and kernel g(t)
- Slide kernel func through base function, graph convolution as we go
- The graphed convolution shows our response through the similarity of our func, in our case we would have a linear pyramid 

## Stride
- Stride is the amt our kernel moves when we scan our image
- Changes dims of our activation map (3x3 kernel over 7x7 stride=1 map of 5x5, stride=2 map of 3x3)
- Formuala for map size = (imgdim1 - filterdim1)/stride + 1
- Some strides may lead to fractional map sizes which we cant have, we must solve it through other methods
  - Padding: zero, one, etc adds extra pixel to give more dim
  - Pooling: reduces dims by combining groups of pixels (multiple forms, max takes highest val, avg takes avg, etc)
  = 