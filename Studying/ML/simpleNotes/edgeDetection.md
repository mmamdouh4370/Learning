# Edge Detection 
- Edges give more info on the shape and semantics of an image over raw pixels, and give a compact border
- Edges come from a variety of discontinuities: depth, light, color, and surface.
 
## Edge Models
- Step edge: abrupt change
- Ramp edge: gradual change
- Roof edge: peak change "up and down"

- More specifically, edges are a rapid change in an images intensity function (extrema of derivavitve)
- Noise makes it harder to distinguish edges in intensity functions
- Smoothing can help, take a smoothing func and the intensity func, mult them and take the deriv and check for extrema 
  (2nd deriv we can use zero crossings for same info)
- We can save ops by using a convolution smoothing func since dx(f * g) = f * dxg, so we just have dxg and f and just mult 
- Smoothing can have an inverse effect and smooth edges too much whilst removing noise
- Use localization, keep it close to marked true edges and keep it to one point per true edge point 

## Prewitt and Sobel Edge Detector
- Compute derivatives for both xy, then find gradient magnitude and its threshold
- Use discrete derivs
    - Backward diff: f(x) - f(x-1) = f'(x)
    - Forward diff: f(x) - f(x+1) = f'(x)
    - Central diff: f(x+1) - f(x-1) = f'(x)

## Marr Hildreth Edge Detector
- Smooth image with gaussian filter
- Apply laplacian to image
- Check for zero crossings, find their slope, and apply threshold to the slope to mark further edges

## Canny Edge Detector
- Smooth image with gaussian filter
- Find derivative of image 
- Find magnitude and orientation of the gradient 
- Apply non max suppression 
- Apply hysteresis thresholding (high low threshold for edge or non edge pixel, any vals between high low use neighbors to see if 
  connected to edge)
