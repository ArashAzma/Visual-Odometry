# Visual-Odometry

![Vo_3](https://github.com/user-attachments/assets/29d92e4a-8b78-4711-996a-6160cc07fca1)


Visual Odometry pipeline using stereo image sequences to estimate camera trajectory and reconstruct 3D scene features. The implementation leverages OpenCV and various computer vision techniques to track camera motion and estimate its path through space.

## Project Structure

The visual odometry pipeline consists of several key stages:

### 1. Dataset Preparation
- Used **KITTI dataset** stereo image sequences
- Processed grayscale stereo image pairs
- Loaded camera calibration parameters

### 2. Depth Estimation
- Implemented stereo depth estimation using two methods:
  - Block Matching (BM)
  - Semi-Global Block Matching (SGBM)
- Computed disparity maps to calculate depth information
- Depth calculation uses camera intrinsic parameters and baseline distance

![Untitled design (2)](https://github.com/user-attachments/assets/b05a1d16-e75f-4afc-bd34-f5a42c4de22b)

### 3. Feature Extraction and Matching
  - SIFT (Scale-Invariant Feature Transform)
  - ORB (Oriented FAST and Rotated BRIEF)
  - SURF (Speeded Up Robust Features)
- Used feature matching techniques:
  - Brute Force Matching
  - FLANN-based Matching
- Applied feature matching with distance ratio test for robust matching

### 4. Motion Estimation with PnP
- Utilized PnP (Perspective-n-Point) with RANSAC for robust motion estimation
- Converted rotation vectors to rotation matrices
- Estimated camera translation between consecutive frames

### 5. Trajectory Reconstruction
- Accumulated transformations to build global camera trajectory
- Tracked feature points in global coordinate system
- Compared estimated trajectory with ground truth poses

## Performance Metrics

- Computed Root Mean Square Error (RMSE) to quantify trajectory estimation accuracy

## Dependencies
- OpenCV
- NumPy
- Pandas
- Matplotlib
- Plotly

## Results and Observations

- Trajectory estimated with feature-based motion estimation
- Visual comparison between estimated and ground truth trajectories
- Disparity and depth maps generated for each frame

https://github.com/user-attachments/assets/10ccf87b-792f-4e4c-bf61-4a2179e50a81

## Future Improvements
- Implement loop closure detection
- Explore deep learning-based feature matching
- Add more robust outlier rejection techniques