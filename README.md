# IPPE
Infinitesimal Plane-based Pose Estimation (IPPE): A very fast and accurate way to compute a camera's pose from a single image of a planar object using point correspondences. This has uses in several applications, including augmented reality, 3D tracking and pose estimation with planar markers, and 3D scene understanding.

This is the author's Matlab implementation from the peer reviewed paper "Infinitesimal Plane-based Pose Estimation" by Toby Collins and Adrien Bartoli, published in the International Journal of Computer Vision, September 2014. A copy of the author's pre-print version can be found here: http://isit.u-clermont1.fr/~ab/Publications/Collins_Bartoli_IJCV14.pdf

 Feel free to contact Toby (toby.collins@gmail.com) if you have any
 questions about the paper and IPPE.

 This package is free and covered by the BSD licence without any warranty. We hope you find this code useful and if so please cite our paper in your work:

@article{
year={2014},
issn={0920-5691},
journal={International Journal of Computer Vision},
volume={109},
number={3},
doi={10.1007/s11263-014-0725-5},
title={Infinitesimal Plane-Based Pose Estimation},
url={http://dx.doi.org/10.1007/s11263-014-0725-5},
publisher={Springer US},
keywords={Plane; Pose; SfM; PnP; Homography},
author={Collins, Toby and Bartoli, Adrien},
pages={252-286},
language={English}
}

## Demos
We give two demo functions for running IPPE.

The first demo: IPPE_demo1, shows how to use IPPE to solve a perspective camera's pose with a plane and a single image using ransac-based feature matching. Two feature methods are supported, which are affine-sift (ASIFT) and SURF. Other can be easily added. This demo loops through a set of 5 images and computes the camera's pose relative to the plane for each image.

The second demo: IPPE_demo2, shows and example of using IPPE to solve a camera's pose with a plane and simulated point correspondences.

 In the demos we show results with IPPE, and the results you get by nonlinear refinement using the gold standard method of Levenberg Marquardt (LM). LM optimises the reprojection error, which produces statistically optimal results for I.I.D Gaussian measurement noise, but is about two orders of magnitude slower than IPPE, and in practice it often gives poses that are virtually indistinguishable to IPPE. On a modern desktop machine IPPE typically computes poses in under 0.2ms with Matlab code, with comparable accuracy to LM (which can take up to 10ms). C++ code is coming, which will be significantly faster. IPPE is the fastest method available for solving the problem with comparable accuracy to LM. Note that if speed is not an issue, one should refine the results from IPPE with LM to have statistically optimal poses. 
 
## Dependencies
This package requires the Affine SIFT (ASIFT) library for affine-invariant SIFT matching: http://www.ipol.im/pub/art/2011/my-asift/ This is easy to compile with cmake, and you should put the executable demo_ASIFT in the demo_ASIFT_src folder.

Optionally, you may need Bouguet's calibration toolbox:  http://www.vision.caltech.edu/bouguetj/calib_doc/ This is used for performing lens undistortion on an image.
