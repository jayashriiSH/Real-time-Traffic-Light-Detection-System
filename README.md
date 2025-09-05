# Real-Time Traffic Light Detection

## Overview
This project implements a **traffic light detection system** using **OpenCV** and **HSV color segmentation**. The system can process both images and videos to identify traffic light states (`red`, `yellow`, `green`) and annotate them in real-time.

The dataset used is from **[Ali Noor – Small Traffic Light Colors Dataset](https://www.kaggle.com/datasets/ali-noor/small-traffic-light-colors-dataset-by-ali-noor)**.


## Methodology
1. **HSV Segmentation:**  
   - Images/videos are converted to HSV color space.
   - Color masks are created for red, yellow, and green lights.
   - Red uses two ranges (`0–8` and `170–180`) to account for hue wrap-around.

2. **Contour Detection:**  
   - Extract candidate regions using contours.
   - Filter contours by **area**, **aspect ratio**, and **circularity** to reduce false positives.

3. **Merging Boxes:**  
   - Overlapping boxes are merged to handle multiple detections of the same light.

4. **Frame-Level Prediction:**  
   - Priority order: `red > yellow > green`.
   - Each frame/video is labeled according to the highest-priority detected light.

5. **Annotation:**  
   - Detected lights are drawn as rectangles.
   - State labels are overlaid on images/videos.
   - CSV log is generated with frame/image predictions.



## Results

### output images
<img width="136" height="168" alt="image" src="https://github.com/user-attachments/assets/ff992440-99d9-4bd2-bcae-1240055ed2dd" />

### output Videos
Two sample videos were processed, and annotated outputs are available:


## Observations
- Red light detection is most reliable due to HSV separation.  
- Yellow light detection may sometimes overlap with red or green regions under poor lighting.  
- Small lights or partially occluded lights may be missed depending on `min_area` threshold.
---

