# Topics to Review for Midterm Exam:

1. Any topics mentioned on course topical outline

2. Review homework assignments!

3. Basic history of vision (Hough, Roberts, Rosenfeld, Duda & Hart, Minsky, Rosenblatt, Fukushima) - don't need to know dates
 - Hough - early line detection
 - Roberts - extract geometric 3d shapes from visual data
 - Rosenfeld - first vision textbook
 - Duda and Hart - pattern and scene analysis
 - Minsky - connect a camera to computer and describe what it sees (caused first AI winter (can't model nonlinear))
 - Rosenblatt - Perceptron
 - Fukushima - neocognitron - similar architecture to modern dat cnn's without training using backprop

4. Image formation
 - light hits object, bounces off into imaging system, projects onto image plane. brightness is determined from intensity, surface, and angle of light. 
- Digital cameras samples light into cells to convert into digital signals. 3 color channels, RGB. quantize world images into digital image plane. Bayer grid records RGB in different grids. more green since human eyes are sensitive to green. 

5. Sampling and aliasing
Terminology
 - sample -  record function at discrete values
 - reconstruction - build signal from sample
 - aliasing - sampled signal is same as lower freq signal
 - lower resolution reduces high frequencies
Nyquist-Shannon sampling theorem - you should know what this is and how to prove it
 - sampling must be at least twice the maximum frequency of input signal to reconstruct the signal
Anti-aliasing - how?
 - sample more
 - get rid of all freq that are greater than half of new sampling freq
   - lose info, but better than alias
   - use smoothing filter
 - anti-aliasing improves NN performance

6. Image transformations
Point processing types (don't need to know formulas)
Image filtering
- replace value at pixel by a function of neighboring pixels
 - Image warping - what's it change?
- Translation
- Scaling
- Rotation
- Affine - combine trans, scale, rot, and shear (preserves parallel lines)
- Projective transformations - affine trans and projective warps (lines may not stay parallel)
   - Types of warps
   - Don't need to memorize rotation formula, but should be familiar with it and inverse transformations
 - Affine transformations vs projective
Forward vs inverse warping 
 - Forward warp - send (x,y) -> (x,y)'
   - if pixel is warped to not an integer location splat the values to neighboring pixels
 - Inverse warping - usually better, more efficient, no problem with holes (not all warps have inverse functions)

7. Filtering
Correlation vs convolution (if I give you one formula, can you derive the other? - should be familiar with manipulating these from homework)
 - correlation adding, convolution subtracting idx
 - in deep learning, we use cross-correlation since the kernel isn't flipped since it doesn't matter to NN that the resulting image is flipped
Smoothing / low-pass filters (Gaussian / box) - don't need to memorize formula of Gaussian
 - sum to 1, removes high frequency, smoothing proportional to size
 - convolving gaussian with gaussian is gaussian, use a bigger sigma
 - gaussian filters are good for additive, zero-mean noise
Properties of linear filters
 - convolution with an impulse response is itself, cross-correlation will be flippsed
 - can add filters independently if filters are added or images are added
 - filter(shift) = shift(filter)
 - commutative
 - associative (convolve filters first)
 - distributes over addition
 - identity gives filter
 - most of these only true for convolutions
Sharpening with filters
 - accentuate pixels in relation to local average
 - 2 * image - smooth
 - image - smoothed = detail, image + detail = sharp
Separability
 - filters can be separated into x-filters and y-filters
 - pass x and y separately over image, reduces computational complexity by M
bilateral filter - give more weight to pixel like the interest pixel
8. Fourier transform
 - represent any univariate function as a weighted sum of sines and cosines at different frequencies
Don't need to memorize formulas per se, but should be familiar with manipulating them from homework (you will be given equation of Fourier transform)
Complex conjugate
Foward / backward transform
Properties of Fourier transform (linearity, duality)
Fourier transform pairs (need to know these, including comb)
Complexity of FFT
You should understand what the Fourier transform of images look like (i.e. if I give you an image, can you tell me what the Fourier would be?)
Transformations with FT
Convolution theorem - this was on homework!
Proof of the sampling theorem - you should understand this

9. Edge detection
Derivative filters (you should know what these are - e.g. Sobel) and how orientation and magnitude are computed
 - sobel is just derivative filter with smoothing
 - orientation is calculated as adding sin(theta)y + cos(theta)x derive
 - magnitude is calculated as changing the sigma for each derivative
Canny edge detector terminology

10. Corner detection
You should be very familiar with this from your homework 
You need to know the second moment matrix and how we can use it to detect corners

SIFT
You should know the idea behind how SIFT is computed (e.g. slide 24 of 8_slides.pdf)
Matching
How we can do matching and suppress mismatches
Optical flow
What is it?
What are the assumptions we had for estimating optical flow?
Brightness constancy constraint
Lucas-Kanade and the second moment matrix
When doesn't optical flow estimation work under this formulation?
Fitting
Hough transform and RANSAC (be careful to review and understand all the RANSAC slides)
Connection of outlier ratio, sample size, and iterations
Need to know how these work (don't need to memorize formulas for Hough transform)
Alignment
You don't need to memorize the formula for cross-product
Understand homographies and homogeneous coordinates
Cameras
Pinhole projection model - you should know the terminology (e.g. camera center, optical center, aperture, image plane, etc.)
Understand coordinate system - this is the foundation for understanding everything we talked about in epipolar geometry
Projection equations (you should easily be able to derive these)
Thin lens formula - you should know this
Depth of field, field of view
Perspective projection
Finding a vanishing point
Measuring height without a ruler (this was on your homework!)
You should know how to find a line passing through two points, intersection of two lines (point) etc. (I will give you cross-ratio formula)
Orthographic projection
Camera calibration
You need to understand how I can go from a world coordinate to a image coordinate (x =~ PX)
Understand principal point (slide 43-45) of 12_slides.
What are extrinsics and intrinsics?
Epipolar geometry
You need to really understand the epipolar constraint and epipolar geometry formulas (e.g. epilines, epipoles, etc.). This was directly on your homework. You need a good conceptual understanding of this.
You definitely need to review slides 27-39 of 13_slides and have an understanding enough that if I gave you the picture you would be able to derive the epipolar constraint and essential matrix. using triple product.
Fundamental matrix - you should understand the relationship of it to essential matrix. You can derive these yourself, but you should be very familiar with these equations.
Two-view stereo
Review slides 11-15 closely -- you shoud be able to describe how we can calculate depth from disparity (disparity is just how much the patch moved), and the other thing it depends on is the baseline and focal length...
Lambertian surface
Multi-view stereo
Have a general idea of the plane sweep stereo algorithm
Structure from motion
You know know how we can solve for structure from motion using the incremental algorithm
Plenoptic function
What is it? 
Two plane light field (concept)
NeRFs
Understand the concept of what a neural radiance field models (inputs / outputs)
Some part of the exam may require you to compute a matrix inverse. I will give you instructions on how to use the Gauss-Jordan method on the exam, but if you want to save yourself the time, you can refresh your memory on this ahead of time.

