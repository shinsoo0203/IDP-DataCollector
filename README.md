# IDP-DataCollector

## Overview
Collecting autonomous car sensor data

## Sensor Specification


## ZED2 topic list
● RGB : 왼쪽, 오른쪽 카메라 합쳐서 송출
  color 
    -rgb : /zed2/zed_node/rgb/image_rect_color
    
    -gray : /zed2/zed_node/rgb/image_rect_gray
    
  refine
    -raw : /zed2/zed_node/rgb_raw/image_raw_color  
    
    -rectified :/zed2/zed_node/rgb/image_rect_color

● Left : 왼쪽 카메라 이미지

  // RGB 동일

● Right : 오른쪽 카메라 이미지

  // RGB 동일
  
● Stereo : 왼쪽, 오른쪽 각각 송출
  
  // RGB 동일
  
● Point Cloud : 이미지 포인터 형태로 반환

  /zed2/zed_node/point_cloud/cloud_registered

● IMU : 각속도, 선속도

  /zed2/zed_node/imu/data

● Pose : position 및 roll, pitch, yaw

  /zed2/zed_node/pose

  
