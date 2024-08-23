
# Grasping Project

This project involves processing and combining point clouds from noisy real depth cameras to create a full view of an object. The resulting processed data is used to generate grasps using two different pipelines: GraspIt! and GPD.

## Table of Contents

- [Introduction](#introduction)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
  - [Point Cloud Processing](#point-cloud-processing)
  - [Preparing for GPD](#preparing-for-gpd)
  - [Preparing for GraspIt!](#preparing-for-graspit)
  - [Running GraspIt!](#running-graspit)
  - [Running GPD](#running-gpd)
- [Points System](#points-system)
- [References](#references)

## Introduction

The objective of this project is to combine multiple point clouds from different views to obtain a complete view of an object. The processed point clouds are then used for grasping simulations using GraspIt! and GPD.

## Requirements

- Python 3.x
- Open3D Library
- GraspIt! Simulator
- GPD (Grasp Pose Detection)
- GitPod account (for running the Jupyter Notebook in a cloud environment)

## Installation

1. Clone the repository and navigate to the project directory:

   ```bash
   git clone https://github.com/yourusername/grasping-project.git
   cd grasping-project
   ```

2. Install the required Python packages:

   ```bash
   pip install -r requirements.txt
   ```

3. Follow the instructions for installing [GraspIt!](http://graspit-simulator.github.io) and [GPD](https://github.com/atenpas/gpd).

## Usage

### Point Cloud Processing

1. Download the point clouds provided in the assignment.
2. Use the provided Python script to read, manipulate, and process the point clouds.
3. Combine the point clouds into one using techniques like downsampling, outlier removal, and bounding box cropping.
   - Set limits for the z-axis in the bounding box.
   - Decide whether to apply processing to the final combined point cloud or to individual samples.

### Preparing for GPD

1. Ensure that the processed point cloud includes a table under the object.
2. Translate the point cloud to the position (0, 0, 0).
3. Save the point cloud as a `.pcd` file.

### Preparing for GraspIt!

1. Ensure that the processed point cloud only contains the object without the table.
2. Create a mesh from the point cloud, translate it to the position (0, 0, 0), and save it as a `.ply` file.

### Running GraspIt!

1. Open the GraspIt! interface.
2. Import the Barrett robot and the mesh of the object as a graspable body.
3. Run the Eigengrasp planner and sort the grasps by ϵ-quality.
4. Take a screenshot of the best grasp.

### Running GPD

1. Run GPD using the prepared point cloud.
2. Adjust parameters in `eigen_params.cfg` if necessary to optimize the run time.
3. Take a screenshot of the grasp output.

## Points System

- **Correct Point Cloud Processing** (2 points)
  - GraspIt! mesh should be solid without a table.
  - GPD point cloud should include a table.

- **Correct GraspIt! Output** (2 points)
  - Screenshot of the grasp.
  - List of top 10 grasps.

- **Correct GPD Output** (1 point)
  - Screenshot of the grasp.

## References

- [Open3D Point Cloud Class](http://www.open3d.org/docs/release/python_api/open3d.geometry.PointCloud.html)
- [Open3D Point Cloud Tutorial](http://www.open3d.org/docs/latest/tutorial/Basic/pointcloud.html)
- [Surface Reconstruction Tutorial](http://www.open3d.org/docs/latest/tutorial/Advanced/surface_reconstruction.html)
- [Open3D Triangle Mesh Class](http://www.open3d.org/docs/release/python_api/open3d.geometry.TriangleMesh.html)
- [GraspIt! Commander API](https://github.com/graspit-simulator/graspit_commander/blob/master/src/graspit_commander/graspit_commander.py)
