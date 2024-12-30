# Image filtering

## Image histogram
- Histogram of numPixels of certain shade/value (usually for grayscale since b-w)
- Y axis is numPixels, X axis is "bins" of our range (b-w is 256)
- Helps show info abt image such as clustering, and basic data analysis vals 

## Digitization
- Irl objects are not exact/discrete but images will have to be discrete
- We transform continuous space to discrete space through digitization
- Sampling discretes the domain, quantization discretes the range (Defining a func at vals)
- Take a 3d landscape to 2d grayscale image. We define depth with color and have set points for our image (pixels on a grid)
- To move to RGB, range and domain remains but we layer 3 images using red green blue

### Sampling
- Defines resolution

### Quantization
- Defines quality (256 bins, we can lower this and make images look worse and have drastic pixel to pixel color changes)

### Resolution
- Diff from image res, this is a display parameter of dots per inch
- Measure of spatial pixel density (most screens 72 dpi), relates to measure of distance for image

## Intensity profile
- Take a row of pixels, chart the range as a func

## Noise
- Happens from multiple things: light, reflections, lens, electronic interference, etc
- Random with some probability, thus has distribution
- Thanks due to distribution property, easy to measure adding noise to an image through different algos (additive, multiplicative)

### Gaussian noise
- Most common noise algo used, bell curve function

### Uniform distribution
- Also common noise algo, drop low values below threshold to 0

### Salt and pepper noise
- Make each pixel b/w with uniform probability dist (0 or 1)

## Filtering
- Focuses on function of a neighborhood of the image
- Typically used for enhancing images (denoise, resize, contrast/saturation/etc adjustment)
- Info extraction (texture, edges, points, patterns)

### Correlation
- Linear relationship function for filtering img by kernel, very common 
- sum k: sum l: f(k,l) * h(k, l) (f for img h for kernel)

### Convolution
- Same formula as correlation except h(-k, -l) aka flip the kernel matrix
- Assocative operation

- Convolution is a filtering operation that shows overlap for the given functions

- Correlation compares the similarities of two sets of data (relation of the signal)

- Gaussian filter very natural and common, smooth ah bell curve, symmetric, infinite num of derivs, conv of gaussian is gaussian, separable into lower dims

### Box filter
- Replace each pixel in a neighborhood with the neighborhood avg, useful for making edges blend or sharpen

### Sobel filter
- Creates a negative of the image with edges whitened

- Any linear, shift invariant operation can be considered a Convolution

### Median filter
- Median in neighborhood, not the same as convolution as we dont use min vals
- Quite good at removing salt pepper noise esp at lower nxn neighborhoods vs mean filters

