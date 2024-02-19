# Stereo Vision - SSRL
### Overview
This project focuses on stereo vision using computer vision techniques to estimate depth information from a pair of rectified stereo images. It utilizes the OpenCV library for image processing and disparity map generation. The generated disparity map is used to reconstruct a 3D point cloud of the scene.

**Link to research reflection:** https://docs.google.com/document/d/1IYjSNB6A4fzgUdNGh5LDhGe7NPew67wU5lHWY1YKXEc/edit?usp=sharing

### Choices made
- It became very helpful to run the code as a ipynb file, so the project includes both the .py and .ipynb files to use. While it was specified that the project should be in python, it might be easier for you to run it as an IPythonNoteBook project. 
- Initially, the project had the user input the file paths of the two images and the calib.txt files they wanted to use for the program. However this became very tedious for the user. Given the small scale of the source code, it seemed easier for the user to enter this information into the program. So to test the project on additional datasets, you should edit the file path and calibration information within the source code.
- The project was tested using datasets from https://vision.middlebury.edu/stereo/data/scenes2014/. The datasets were ommited from the git repository, however one that can be used for testing was left in the project's directory.
- The project assumes that the images are rectified as this was the case for the datasets given at https://vision.middlebury.edu/stereo/data/scenes2014/
- **StereoSGBM Algorithm:** The StereoSGBM algorithm was chosen for stereo matching due to its robustness and efficiency in handling various types of stereo images, including those with textureless regions or occlusions.
- **Parameter Selection:** The parameters of the StereoSGBM algorithm were chosen based on experimentation to achieve a balance between accuracy and computational efficiency.

### Cloud Map Limitation
The disparity map generated from the large input images appears noisy and lacks meaningful depth information due to an insufficient disparity range. You will find that there is additional source file called downsampling.ipynb, which is where I attempted to impliment this solution. The 3D point cloud outputted in this program indicates ongoing challenges in accurately representing the scene's depth structure. I attempted to solve this issue by:
- **Downsample Input Images:** Reduce image size using cv.resize() with a scaling factor of 0.25.
- **Adjust Parameters:** Increase disparity range and adjust parameters like block size to accommodate the reduced image size adequately.
- **Scale Disparity Values:** Multiply disparity values by 1/16 to obtain depth values in pixels.
- **Reprojection:** Reproject corrected disparity map to 3D space using cv.reprojectImageTo3D() with updated parameters
- - **Textureless Regions:** The algorithm may struggle in textureless regions or areas with repetitive patterns, addressing a known limitation of stereo matching algorithms.
.

### Features
- Computes stereo disparity map using the Semi-Global Block Matching (SGBM) algorithm.
- Reconstructs a 3D point cloud from the disparity map.
- Visualizes the disparity map and 3D point cloud.

### Tools Used
- OpenCV: OpenCV is used for image processing, stereo matching, and 3D reconstruction tasks.
- NumPy: NumPy is used for efficient array operations and manipulation.
- Matplotlib: Matplotlib is used for visualizing images, disparity maps, and 3D point clouds.

### Overall Rationale
The choices made in the project were driven by a balance between accuracy, efficiency, and usability. By leveraging established libraries and algorithms, considering potential limitations, and identifying areas for improvement, the project aims to provide a solid foundation for stereo vision tasks while also paving the way for future enhancements and optimizations.




