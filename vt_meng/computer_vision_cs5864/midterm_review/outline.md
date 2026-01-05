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
 - Transform is F, backward is F^-1
Properties of Fourier transform (linearity, duality)
 - Plancherel theorem (energy is perserved)
 - Linearity = F{af1 + bf2} = aF{f1} + aF{f2}
Fourier transform pairs (need to know these, including comb)
 - Box - sinc
 - gauss(var = sigma) - gauss(var = 1/sigma)
 - f(t) = 1 (constant signal) - impulse
Complexity of FFT
 - discrete fourier transform FFT is NlogN complexity of an NxN image
You should understand what the Fourier transform of images look like (i.e. if I give you an image, can you tell me what the Fourier would be?)
Transformations with FT
 - scaled images are scaled inversely in FT
 - rotated images have the same rotation in FT
 - translated images have same magnitute, different phase
Convolution theorem - this was on homework!
 - fourier transform of a convolution is the product of their fouriers
 - inverse ft of prod of two fourier is the conv of their inv ft
Proof of the sampling theorem - you should understand this
 - sample function at discrete intervals by multiplying with the comb function
 - take the ft
 - becomes F(u) * 1/T comb(t;1/T)
  - basically replicated copies of F(u)
 - succeeds when sampling freq 1/T exceeds twices greated freq in F(u), or else the freq will overlap
 

9. Edge detection
Derivative filters (you should know what these are - e.g. Sobel) and how orientation and magnitude are computed
 - sobel is just derivative filter with smoothing
 - orientation is calculated as adding sin(theta)dy + cos(theta)dx derive
 - magnitude is calculated as changing the sigma for each derivative
Canny edge detector terminology
 - compute x and y derivative images
 - find magnitude and oriention of gradient
 - threshold gradient magnitude
 - non-max sup - for each loc above threshold, check if its higher than its neighbors in both directions of the gradient. use interpolation if subpixel
 - hysterisis - use high threshold to start edge curves, use low threshold for curves touch the high curves

10. Corner detection
You should be very familiar with this from your homework 
You need to know the second moment matrix and how we can use it to detect corners
 - Harris
  - compute partial derivatives
  - 2nd moment matrix is Ix2, Ixy, Ixy, Iy2
  - use eigenvalues of M to get cornerness
  - use R to get orientation
  - corner response det(M) - alphatrace(M)^2
  - threshold r
  - non-max sup
  * not scale-invariant
  2D multi-scale blob detection
- find scale-space locations where LoG reachs local max
- multiply by sigma^2 to make responses comparable
- look for sigma with max response
- convolve img with scale-norm log at diff sigma
- find max across space and scales

11. SIFT
You should know the idea behind how SIFT is computed (e.g. slide 24 of 8_slides.pdf)
 - scale-invariant
 - rotation-invariant
 - approximate LoG with DoG
 - compute DoG with image pyramid, reducing the scale each octave
 - take 16x16 square window around detected feature
 - compute gradient orientation for each pixel
 - histogram of orientations weighted by magnitude is the descriptor
 - split 16x16 window into 4x4 grid
 - quantize gradient orientation by snaping to one of 8 directions
 - gradient contributes magnitude to histogram
 - 16 cells * 8 orientations = 128 dim descriptor per feature
 - normalize and clip to threshold
 - make it rotation invariant by rotating the patch to its maximum response
 - can handle changes in viewpoint, illumination, fast, efficient


12. Matching
How we can do matching and suppress mismatches
 - generate candidate matches through euclidean distance between feature descriptors. take closest/k-closest/threshold distance as candidates
 - ratio test, find distance between 1st candidate and 2nd candidate and take ratio
 - if low, good match
 - if high, ambiguous match

Visual words
 - cluster feature descriptors, groups correspond to visual words
 - summarize images based on distribution of word occurrences

13. Optical flow
What is it?
 - apparent motion of brightness patterns in the image; not equal motion field
What are the assumptions we had for estimating optical flow?
 - brightness consistency
 - small motion
 - spatial coherence
Brightness constancy constraint
 - I(x,y,t-1) = I(x+u(x,y), y+v(x,y), t)
 - using taylor expansion of this yields
    Ixu(x,y)+Iyv(x,y)+It=0
 - suppose (u,v) satisfies gradient I dot (u,v) + It = 0
Lucas-Kanade and the second moment matrix
 - spatial coherence - neighbor pixels have the same u,v
 - for a neighborhood of n pixels, set up linear least squares
 - use second moment matrix for cornerness to solve Ad=b
 = ATAd = ATb
 = d = (ATA)-1ATb
 - find u,v minimizing sum_i(I(x+u,y+v,t)-I(x,y,t-1))
When doesn't optical flow estimation work under this formulation?
 - large movement
  - can fix with multiple resolutions
 - point doesn't move like neighbors
  - fix with motion segmentation
 - brightness consistency doesn't hold
  - feature matching/tracking
state of the art is learned

14. Fitting
Hough transform and RANSAC (be careful to review and understand all the RANSAC slides)
Hough transform
 - discretize param space into bins
 - for each feature point, vote in a bin that couldve produce the point
 - line corresponds to a point
 - point corresponds to line
 - two points on a line correspond to two intersecting lines
 - plot all lines on param space and find where the most intersect (vote)
 - issue is unbounded param domains and vertical lines
 - solve using polar represenation
  - each point x,y adds a sinusoid in (theta, rho) param space
 - for circles:
  - for each edge pixel, r, gradient direction, calculate center a= x-rcos(theta) b = y-rsin(theta)
 - pros
  - can deal with nonlocality and occlusion (since lines are estimated)
  - can detect muliple instances
  robust to noise
  - general strat for shape local
 - cons
  - complexity increases exponentially with number of params
   - not a big deal in practice
  - nontarget shapes can create spurious peaks
  - hard to pick good grid size
 - generalized
  - offline, at each boundary point compute displacement
  - detection, find gradient at point, use retrieved vectors to find a vote for referrence point
Ransac
 - random sampling consensus
  - randomly choose subset of points
  - fit model to subset
  - count number of inliers, reject rest
  - choose model with most inliers
 - parameters
  - s - min number of points to fit model
  - distance threshold t - can be empirical (t=1.96sigma)
  - d - expected inlier ratio
  - N - iterations (log(1-p)/log(1-(1-e)^s))
Connection of outlier ratio, sample size, and iterations
Need to know how these work (don't need to memorize formulas for Hough transform)
15. Alignment
You don't need to memorize the formula for cross-product
Understand homographies and homogeneous coordinates
16. Cameras
Pinhole projection model - you should know the terminology (e.g. camera center, optical center, aperture, image plane, etc.)
 - camera center - pinhole
 - aperture - size of pinhole
 - image plane - where the light projection is captured
 - focal point - where all parallel rays to the optical axis pass through
 - focal plane - where all parallel ray converge
 - depth of field - controled by aperature size
 - filed of view - controlled by focal length and length of sensor
Understand coordinate system - this is the foundation for understanding everything we talked about in epipolar geometry
 - O is origin (pinhole), XY in image, Z sticks out from image (optical axis)
Projection equations (you should easily be able to derive these)
 - (x,y,z) = (fx/z, fy/z)
Thin lens formula - you should know this
 - y'/y = D'/D
 - y'/y = (D'-f)/f
 - 1/D' + 1/D = 1/f
Depth of field, field of view
17. Perspective projection
Finding a vanishing point
 - find vector in direction of lines
 - center at optical axis
 - vp is given by (flx/lz, fly/lz)
front-parallel planes are fixed depth z
 - scaled by a factor of f/z
 - angles and ratios are preserved
Measuring height without a ruler (this was on your homework!)
 - given two vp on horizon
 - find horizon line
 - find line though bottom of ref and obj
 - find intersection of horizon line and bottom line, call that v
 - cross v and top of obj to get line
 - cross that line with vert ref line to get projection of obj onto ref
 - use cross ratio to solve for heigh
You should know how to find a line passing through two points, intersection of two lines (point) etc. (I will give you cross-ratio formula)
Orthographic projection
18. Camera calibration
You need to understand how I can go from a world coordinate to a image coordinate (x =~ PX)
 - normalized coordinate system: camera center is at the origin, principle axis is z, x,y of image plan are parallel to x,y of world
 - P is made up of K[R|t]
Understand principal point (slide 43-45) of 12_slides.
 - point where principle axis intersects image plane
 - in normalized, origin is at the pp,
 - in image coordinates, origin in the corner
What are extrinsics and intrinsics?
 - extrinsics = R and t
 - intrinsics = f and pp
19. Epipolar geometry
You need to really understand the epipolar constraint and epipolar geometry formulas (e.g. epilines, epipoles, etc.). This was directly on your homework. You need a good conceptual understanding of this.
You definitely need to review slides 27-39 of 13_slides and have an understanding enough that if I gave you the picture you would be able to derive the epipolar constraint and essential matrix. using triple product.
 - calibrated case
 - Projection matrices are K[I|0] and K'[R|t]
 - can premultiply the projection matrices by inverse calibration to get normalized image coordinates
 - triple product = x' dot [t X Rx] = 0
 - Ex is the epipolar line associated with x
 - ETx' is ass x'
 - Ee=0
 - E is singular (rank 2) 5 degrees of freedom
Fundamental matrix - you should understand the relationship of it to essential matrix. You can derive these yourself, but you should be very familiar with these equations.
20. Two-view stereo
Review slides 11-15 closely -- you shoud be able to describe how we can calculate depth from disparity (disparity is just how much the patch moved), and the other thing it depends on is the baseline and focal length...
 - parallel image planes, epipolar lines are horizonal scan lines
 - can use homographies to project on a common plane
 - for each pixel, find corresponding epipolar scanline
 - examine all pixels on scanline and find best match,
 - triangulate matches
 - x-x' = fB/z
 - z = fB/x-x'
 - compute disparity x-x' and depth(x) = Bf(x-x')
Lambertian surface
 - matte, non-reflective surface
21. Multi-view stereo
Have a general idea of the plane sweep stereo algorithm
22. Structure from motion
You know know how we can solve for structure from motion using the incremental algorithm
init motion from two images using fundamental matrix
init structure from triangulation
for each new image,
 calibarate point by projecting already known points
 compute 3d points from prohections, reoptimize existing points through triangulation
23. Plenoptic function
What is it? 
given several images of the same scene, how to generate new scenes from images
plenoptic function, set of all things we can ever see
L(theta, phi, lambda, t, x, y, z)
can model any thing, anywhere, anytime 
Two plane light field (concept)
24. NeRFs
Understand the concept of what a neural radiance field models (inputs / outputs)
Some part of the exam may require you to compute a matrix inverse. I will give you instructions on how to use the Gauss-Jordan method on the exam, but if you want to save yourself the time, you can refresh your memory on this ahead of time.

