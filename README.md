# Structure from Motion (SfM)

Extracting 3D information from a 2D image and reconfiguring it into 3D is called "Structure from Motion". (structure = 3D structure, motion = Camera pose)  
Structure from Motion(SfM) proceeds with 3D reconstruction of the Structure, as shown in the picture from a sequential set of images.  
It is about how to reconstruct the 3D screen structure accurately, and how to find the camera pose (where the picture was taken), camera intrinsic parameter, and the extrinsic parameter.

![feature extraction](https://user-images.githubusercontent.com/65938333/192982853-80c89740-cd48-4584-aa3f-bc6575ca16a7.png)
![2 view reconstruction](https://user-images.githubusercontent.com/65938333/192982867-d575817d-b3f0-4667-860c-aed2f89861fe.png)

This project is a Python implementation of SfM with only two view. The code is based on openCV and numpy implementation.

## Installation

---

```
git clone https://github.com/sunwoochan/sfm.git
```

## How to Run?

---

Download data for example dataset and run in sfm.ipynb

## Method

---

### 1. Camera Calibration

### 2. Feature Detection & Description

### 3. Epipolar Geometry

### 4. Triangulation

## Dataset

---

38 images of nutella and intrinsic parameter

## SfM pipeline

---

1. Start from 2 views
   1. Feature extraction with SIFT
   2. Camera initialization : Find Essential matrix with RANSAC
      1. Suppose canonical camera setup, one camera matrix P = [ I | 0 ] (3x4 Matrix)
      2. From derivation, there can be 4 possible candidates for P¡¯
      3. Triangulate 2D point correspondences from first two views, and physically verified P¡¯
2. Triangulation : Lift 2D points to 3D space using camera matrices
   1. Given a set of (noisy) matched points : {xi, x¡¯i}
   2. Camera matrices : P, P¡¯
   3. Estimate the 3D point : X
3. Structure and motion adjustment (a.k.a. Bundle adjustment)
