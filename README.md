Summary: This project focuses on 3D reconstruction using Linear Algebra approach, Gaussian Splatting approach and Neural Radiance Fields (NeRF) approach to achieve photorealistic rendering of objects and scenes from novel viewpoints. A dataset of 50 images of a bottle captured from various angles was processed to reconstruct the 3D structure and features of the object. The pipeline integrates camera parameter estimation using COLMAP, feature detection and extraction using the ORB algorithm, and depth analysis through Depth Maps, Disparity Maps, and Edge Maps. The project highlights the different realistic 3D scenes provided by differenet approaches and provides a comprehensive workflow for 3D reconstruction tasks.

## Links to download the input files(dataset)  
Input Dataset for 3D_Reconstruction.ipynb & gaussian_splatting.ipynb:  
Dataset(raw images) - https://drive.google.com/drive/folders/1TbdaAgl1JUMnI40lDh9wkbY0QbIzMqFC?usp=sharing  

Input Dataset for Camera_Calibration.ipynb:  
Checkerboard images  - https://drive.google.com/drive/folders/1yWo7p490DPzUXQvoyZLQLH4GHCnNWQYh?usp=sharing  

Input Dataset for NeRF_3DCV.ipynb: 
https://drive.google.com/drive/u/2/folders/1oGS2biV2ec0nSUgIfG6A6bvU7TlG2wa2

## Output Achieved
The output we achieved is in the follwoing directory:  
https://drive.google.com/drive/folders/1f_XtbQ4nPKVW7ScprS7jAGta3mPN8t8F?usp=sharing


# Numerical Linear Algebra
In Linear Algebra based approach for 3D reconstruction, we use the classical methods to create the dense point cloud of the object.

How to reproduce the code??
The complete code of Classical approach was implemented and tested on Google Colab. So, it is strongly suggested to use the Python CPU runtime of Colab only.

The code needs some images to be uploaded on your respsective Google Drive.
Name the parent directory as: 'DSC 210 Final Project'  
Checkerboard image folder name: 'checkerboard_imgs' https://drive.google.com/drive/folders/1yWo7p490DPzUXQvoyZLQLH4GHCnNWQYh?usp=sharing  
Dataset folder name: 'Dataset' https://drive.google.com/drive/folders/1TbdaAgl1JUMnI40lDh9wkbY0QbIzMqFC?usp=sharing  

The output directories will be made when the code will run.

Download the above mentioned data from this repository and put into respective folders. Put all these folders into parent directory.

Mount the Drive in the Colab notebook (code mentioned in the notebook) and run the code blocks one at a timee. It should work fine. The output files will be stored in newly formed folders in the parent directory.

##### The output we achieved is in the follwoing directory:
output achieved https://drive.google.com/drive/folders/1f_XtbQ4nPKVW7ScprS7jAGta3mPN8t8F?usp=sharing

# Gaussian Splatting for 3D Reconstruction
This project implements Gaussian Splatting, a technique to process 3D point clouds by mapping them to a voxel grid and applying Gaussian filters for density representation.

# Features
Feature Extraction: Detects keypoints and descriptors using SIFT. 

3D Reconstruction: Triangulates points from image pairs using essential matrices.


Gaussian Splatting: Maps 3D points to voxel grids and applies Gaussian smoothing.

Visualization: Exports splatted 3D point clouds and generates visualizations.

# Requirements
Python 3.8+
Required libraries: OpenCV, NumPy, Matplotlib, SciPy, Open3D, Scikit-learn

Run: 
pip install -r requirements.txt  

# Usage
Prepare Images: Place your images in a folder (e.g., input_images).

To open the notebook run:

jupyter notebook  

Open the file gaussian_splatting.ipynb in the Jupyter Notebook interface.

Run the Notebook:
Execute all cells in order.

Outputs:
Splatted Point Cloud: Saved as .ply file in the output directory.

Visualizations: Displayed inline and saved as .png files in the output directory.

# Implementation Details
Key Components
Feature Detection and Matching:
Extracts keypoints using SIFT and matches features with a ratio test.

# 3D Reconstruction:

Computes essential matrices and camera poses. Triangulates 3D points from matched image features.

Gaussian Splatting:

Maps 3D points into a voxel grid.
Applies Gaussian filtering for density representation.

Code snippet:

def process_point_cloud(points_3d):  
        grid_size = 1024  
        grid = np.zeros((grid_size, grid_size, grid_size))  
        voxel_coords = (points_3d * (grid_size - 1)).astype(int)  
        for point in voxel_coords:  
            grid[point[0], point[1], point[2]] += 1  
        return gaussian_filter(grid, sigma=1.0)  


# Results
Splatted Point Cloud: output/gaussian_splatted_point_cloud.ply

Feature Files: .npz files for each image.

Visualizations: Raw 3D points and Gaussian splatted outputs.

Feature matching output: [Feature matching](feature_matching.png)

Static point cloud: [Static point cloud](static_point_cloud.png)

The code also generates a 3d dynamic point cloud, stored as a .ply file. Here I have attached a screenshot of the same. To view its 3d render open the generated .ply file locally.

3D_point_cloud: [.ply Output screenshot](3d_point_cloud.jpeg)


# NeRF: Neural Radiance Fields
Refer the link: https://drive.google.com/drive/u/2/folders/1oGS2biV2ec0nSUgIfG6A6bvU7TlG2wa2
### Folder Structure:
1. images_folder: Contains the stereo images dataset. 
2. sparse: Includes pre-computed COLMAP bin files and .ini file for 3D scene geometry.
3. README.md: Instructions for running the project.
4. NeRF_3D_CV.ipynb: Google Colab notebook containing the full implementation.

### Prerequisites:
Python 3.7+.

If using Google Colab: Everything is pre-installed, you just need to import the modules to execute ther code which is handled in the code itself..

### Required Python libraries:

1. opencv-python
2. opencv-contrib-python
3. numpy
4. matplotlib
5. google-colab (for Colab execution)
6. Access to Google Drive for storing the dataset and results.


### (Optional) If not using Google Colab:
Run the following ocmmand in terminal
"pip install opencv-python opencv-contrib-python matplotlib numpy"

### COLMAP: Extracting Camera Parameters
The camera parameters are already included in the github repository. Using COLMAP requires a lot of dependencies and installation. To reduce the hassel we have included the final camera parameters of our dataset in the 'sparse' folder.
    
### Execute the NeRF_3D_CV.ipynb file block by block in Google Colab
