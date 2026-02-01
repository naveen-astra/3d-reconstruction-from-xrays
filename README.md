# 3D Reconstruction from X-rays

## Overview

This project demonstrates advanced computer vision techniques for 3D medical imaging reconstruction. The system generates synthetic X-ray projections from a 3D femur model and reconstructs the three-dimensional structure using classical image processing and computed tomography methods.

## Project Description

The project implements two primary reconstruction approaches: visual hull reconstruction from multiple silhouettes and filtered back projection (FBP) for CT-style volumetric reconstruction. The implementation processes STL models through voxelization, generates multi-angle X-ray projections, and applies sophisticated reconstruction algorithms to recover the original 3D geometry.

## Key Features

- **STL Model Processing**: High-resolution voxelization of 3D bone models
- **Synthetic X-ray Generation**: Multi-angle projection synthesis (0°, 45°, 90°, and 180-degree rotation)
- **Image Preprocessing**: Gaussian filtering and histogram equalization
- **Silhouette Extraction**: Otsu thresholding with morphological operations
- **Visual Hull Reconstruction**: Shape-from-silhouette 3D recovery
- **CT Reconstruction**: Filtered back projection implementation
- **3D Visualization**: Interactive mesh rendering using Plotly and Matplotlib

## Technical Approach

### 1. X-ray Synthesis
The system converts 3D STL models into voxel representations and generates synthetic X-ray projections through volume integration along viewing directions. Multiple angles are captured by rotating the voxel grid using scipy's rotation functions.

### 2. Preprocessing Pipeline
Generated projections undergo Gaussian blur for noise reduction followed by histogram equalization to enhance contrast and normalize intensity distributions across different views.

### 3. Silhouette Extraction
Binary masks are obtained using Otsu's automatic thresholding method. Morphological closing operations with elliptical kernels refine the extracted silhouettes by filling gaps and smoothing boundaries.

### 4. 3D Reconstruction Methods

#### Visual Hull Method
The visual hull approach back-projects silhouettes from multiple viewing angles into 3D space. The intersection of viewing cones defines the approximate 3D shape, representing the maximal volume consistent with all silhouettes.

#### Filtered Back Projection
For CT-style reconstruction, the system generates sinograms through Radon transforms and applies inverse Radon transforms with ramp filtering. This classical tomographic reconstruction method processes each axial slice independently before stacking into a complete 3D volume.

### 5. Surface Extraction
The marching cubes algorithm extracts triangulated surface meshes from reconstructed volumetric data, enabling high-quality 3D visualization and geometric analysis.

## Dependencies

```
python >= 3.7
trimesh
scikit-image
opencv-python
matplotlib
scipy
numpy
plotly
tqdm
```

## Installation

```bash
pip install trimesh scikit-image opencv-python matplotlib scipy plotly tqdm
```

## Usage

1. Place your STL file (e.g., `Femur.stl`) in the project directory
2. Open and execute `Project.ipynb` in Jupyter notebook or Google Colab
3. The notebook contains sequential cells for:
   - STL loading and voxelization
   - X-ray projection generation
   - Image preprocessing
   - Silhouette extraction
   - 3D reconstruction (both methods)
   - Interactive visualization

## Results

The implementation successfully reconstructs 3D bone geometry from synthetic X-ray projections. The visual hull method provides rapid reconstruction suitable for shape approximation, while the FBP method delivers higher accuracy volumetric reconstruction comparable to clinical CT systems.

## Technical Specifications

- **Voxel Resolution**: Configurable (200-350 subdivisions recommended)
- **Projection Angles**: 180 evenly-spaced views for CT reconstruction
- **Reconstruction Grid**: 200x200x200 default resolution
- **Visualization**: Interactive 3D mesh with aspect-corrected rendering

## Methodology Highlights

This project demonstrates fundamental principles in medical imaging without machine learning dependencies. The implementation relies on classical computer vision and tomographic reconstruction theory, making it computationally efficient and mathematically interpretable.

## Applications

- Medical imaging education and training
- Computer vision algorithm development
- Tomographic reconstruction research
- 3D modeling and visualization
- Biomedical engineering coursework

## Project Structure

```
.
├── Project.ipynb           # Main implementation notebook
├── Human_femur.stl         # Input 3D model
└── README.md              # Project documentation
```

## Future Enhancements

- Implementation of iterative reconstruction algorithms (ART, SART)
- Integration of noise models for realistic X-ray simulation
- Support for arbitrary viewing geometries
- Performance optimization through GPU acceleration
- Quantitative evaluation metrics for reconstruction accuracy

## Author

Developed as part of computer vision coursework at Amrita University.

## License

This project is available for educational and research purposes.
