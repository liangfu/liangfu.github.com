================================
 Stereo Vision Project Homepage
================================

Welcome to the stereo vision project wiki!

Introduction:
=============

The *objective* of the project is to build 3d model from image pairs.

The source code is available at http://github.com/liangfu/stereo-vision .

General steps to implement 3d reconstruction from image sets :

* find correspondence between first two selected image frames
* build fundamental matrix *F* from known correspondence
* rectify images to get simple scanline stereo pair, 
  result in *H_1* and *H_2* for left and right image respectively
* compute disparity map
  using block matching algorithm -- via SAD (Sum of Absolute Diff), typically
* triangulate 3D surface from disparity map
* texture mapping and update mesh from new image frames

Feature Tracking :
==================

A list feature tracking algorithms :

* *KLT* -- the Kanade-Lukas tracker
* *Harris Corner Detector* - good for detecting corners with orthogonal edges

Self-Calibration:
=================
Build fundamental matrix *F* with feature correspondence between the views.

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
