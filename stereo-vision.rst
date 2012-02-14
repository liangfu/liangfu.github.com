================================
 Stereo Vision Project Homepage
================================
	:Author: Liangfu Chen
	:Version: 0.0.1
	:Date: Sun Feb 12 16:19:44 KST 2012
	:Link: http://github.com/liangfu/stereo-vision

Introduction:
=============

The **objective** of the project is to build 3d model from image pairs. Instead
of pursuing the accuracy of the final result, speed is considered more 
important in this project.

The source code is available at 
`github <http://github.com/liangfu/stereo-vision>`_ .

General steps to implement 3d reconstruction from image sets :

1. find correspondence between first two selected image frames
   
2. build fundamental matrix *F* from known correspondence
   
3. rectify images to get simple scanline stereo pair, 
   result in *H_1* and *H_2* for left and right image respectively
   
4. compute disparity map
   using block matching algorithm -- via SAD (Sum of Absolute Diff), typically
   
5. triangulate 3D surface from disparity map
   
6. texture mapping and update mesh from new image frames

Feature Tracking :
==================

A list feature tracking algorithms :

* *KLT* -- the Kanade-Lukas tracker
* *Harris Corner Detector* - good for detecting corners with orthogonal edges

OpenCV introduce the KLT algorithm in *cvCalcOpticalFlowPyrLK*. It takes in two
gray images as input and outcome a list of matched feature points with
evaluation values.
By removing point matches with large error, the correspondence problem can be
solved.

Useful functions in OpenCV:

**cvCalcOpticalFlowPyrLK**
	:input:		image_left, image_right
	:ouput:		corners_left, corners_right, feature_errors
	:optional:	window_size, max_pyramids

Self-Calibration:
=================
Build fundamental matrix *F* with feature correspondence between the views.

With a number of matched feature points (more than 8), *cvFindFundamentalMat* 
function is applied. Then *cvStereoRectifyUncalibrated* is used to compute 
homography.

Useful functions in OpenCV:

**cvFindFundamentalMat**
	:input:		imagePoints1, imagePoints2
	:output: 	fundamental matrix *F*
	:optional:	RANSAC parameters	

**cvFindHomography**
	:input:		imagePoints1, imagePoints2
	:output:	homography *H*, mask (optional, to get inliers)
	:optional:	*RANSAC* or *LMED* parameters

**cvStereoRectifyUncalibrated**
	:input:		imagePoints1, imagePoints2
	:output:	homography H1, H2 (for left and right images respectively)

3D Reconstruction:
==================
Calculate disparity map and build texture mapped model.

Related Links:
==============
1. Peter Kovesi's MATLAB functions for computer vision : 
   http://www.csse.uwa.edu.au/~pk/research/matlabfns/
2. Probabilistic Feature-based On-line Rapid Model Acquisition :
   http://mi.eng.cam.ac.uk/~qp202/my_papers/BMVC09/
3. high-quality stereo sequences recorded from a moving vehicle :
   http://cvlibs.net/datasets.html
4. MATLAB Functions for Multiple View Geometry : 
   http://www.robots.ox.ac.uk/~vgg/hzbook/code/
5. Robust, Non-linear Homography Estimation
   http://www.ics.forth.gr/~lourakis/homest/index.html
