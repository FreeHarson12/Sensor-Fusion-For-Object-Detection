# Sensor-Fusion
Fuse LiDAR and Camera data using the KITTI open dataset, with the results as follows:
https://www.bilibili.com/video/BV12PcFePEFt/?spm_id_from=333.1365.list.card_archive.click&vd_source=f5c7bca2e6a1c91f48cbe5e62aae458a


#Late Fusion: First Detect, Then Fuse

This method first detects obstacles in 2D images using YOLOv4 and assumes that the 3D LiDAR obstacles' positions \((X, Y, Z)\), 3D bounding boxes \((W, H, L)\), and orientations \(R_y\) are already available. Then, the 3D obstacles are projected onto the image through the following steps:  

1. Convert 3D points to homogeneous coordinates, multiply by the projection matrix \(P\), and convert back to Cartesian coordinates to achieve 3D-to-2D projection.  
2. Compute the 3D bounding box in the camera frame \((X, Y, Z, W, H, L, R_y)\), project it onto the image, convert it to a 2D bounding box, and draw it.  
3. Fuse the 3D bounding boxes with the 2D bounding boxes and display the LiDAR and camera detections on the same image.  
4. Compute the Intersection Over Union (IOU) for each bounding box and use the Hungarian Algorithm to match them based on the IOU matrix, producing the final fused objects.  

This method combines 2D visual detection with 3D LiDAR position data, improving the accuracy and reliability of obstacle detection.



