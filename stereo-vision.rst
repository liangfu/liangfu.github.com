Welcome to the stereo vision project wiki!

Introduction:
-------------

General steps to implement 3d reconstruction from image sets :

* rectify images to get simple scanline stereo pair
* compute disparity map (correspondence matching)
* compute 3d surface geometry from disparity map

Feature Tracking :
----------------------------------------

A list feature tracking algorithms :

* KLT -- the Kanade-Lukas tracker

Self-Calibration:
-----------------
Build fundamental matrix *F* with feature correspondence between the views.

Spare 3D Reconstruction:
------------------------
Calculate disparity map and build texture mapped model.

Reference:
----------
1. Peter Kovesi's MATLAB functions for computer vision : 
   http://www.csse.uwa.edu.au/~pk/research/matlabfns/
2. Probabilistic Feature-based On-line Rapid Model Acquisition :
   http://mi.eng.cam.ac.uk/~qp202/my_papers/BMVC09/
3. high-quality stereo sequences recorded from a moving vehicle :
   http://cvlibs.net/datasets.html
4. MATLAB Functions for Multiple View Geometry : 
   http://www.robots.ox.ac.uk/~vgg/hzbook/code/
