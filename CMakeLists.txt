cmake_minimum_required(VERSION 2.8.3)
project(bag_to_depth_image)


set(catkin_RUN_PACKAGES
  roscpp
  sensor_msgs
  std_msgs
)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  sensor_msgs
  cv_bridge
  image_transport
  OpenCV
  rosbag
)

catkin_package(
   INCLUDE_DIRS include
   LIBRARIES
   CATKIN_DEPENDS roscpp std_msgs rosbag

)


add_executable(extract_images
  src/extract_images.cpp
)
target_link_libraries(extract_images
  ${catkin_LIBRARIES}
  ${OpenCV_LIBRARIES}
)

add_executable(depthExtraction
  src/depthExtraction.cpp
)
target_link_libraries(depthExtraction
  ${catkin_LIBRARIES}
  ${OpenCV_LIBRARIES}
)












