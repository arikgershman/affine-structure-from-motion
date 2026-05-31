# 3D Reconstruction: Affine Structure from Motion 🎥
* **Course:** CMSC426
* **Author:** Arik Gershman

## Viewing This Project
The Jupyter notebook contains embedded output and visualizations, which makes it too large to render directly on GitHub. For the best experience:
* 📄 **[View the PDF](CMSC426_Assignment4_sp26.pdf)** — recommended for a quick look at the code and results
* 📓 **[View the notebook on nbviewer](https://nbviewer.org/github/arikgershman/affine-structure-from-motion/blob/main/CMSC426_Assignment4_sp26.ipynb)** — for interactive notebook rendering
* 💾 Download the `.ipynb` file to run it locally

## Project Overview
This project implements an Affine Structure from Motion (SfM) algorithm from scratch to recover a 3D point cloud from a 2D image sequence (the "hotel" dataset). Building upon foundational interest point tracking, the algorithm utilizes Singular Value Decomposition (SVD) and orthographic projection constraints to simultaneously estimate camera motion and reconstruct the 3D structure of the scene.

## Methodology
The pipeline is broken down into several main components:

**1. Measurement Matrix Construction & Factorization**
* Normalizes the tracked 2D feature coordinates (x and y) across multiple frames to have a zero mean and constructs the measurement matrix.
* Performs Singular Value Decomposition (SVD) on the matrix and enforces a strict rank-3 constraint to approximate the initial motion and shape matrices.

**2. Orthographic Constraints & Metric Upgrade**
* Constructs a system of linear equations based on the orthographic projection constraints of an affine camera model ($||a_i||^2 = 1$, $||a_j||^2 = 1$, $a_i^T a_j = 0$).
* Solves the least-squares system and applies Cholesky decomposition to correct and refine the initial affine motion and structure matrices.

**3. 3D Point Cloud Visualization**
* Extracts the finalized 3D structure matrix, representing the positions of the tracked feature points in 3D space.
* Maps the scattered spatial data using a 3D projection plot from multiple elevation and azimuthal viewing angles to clearly verify the physical structure of the reconstructed scene.

## Technologies Used
* **Language:** Python
* **Environment:** Jupyter Notebook
* **Libraries:** NumPy (for linear algebra, SVD, and Cholesky decomposition), SciPy (for handling `.mat` tracking data files), Matplotlib (for 3D spatial visualizations), OpenCV
