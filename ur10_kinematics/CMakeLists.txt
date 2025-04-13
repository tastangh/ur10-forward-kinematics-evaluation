cmake_minimum_required(VERSION 3.0.2)
project(ur10_kinematics)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  std_msgs
  geometry_msgs
  nav_msgs
  moveit_core
  moveit_ros_planning
  moveit_ros_planning_interface
)

find_package(Eigen3 REQUIRED)

include_directories(
  ${catkin_INCLUDE_DIRS}
  ${EIGEN3_INCLUDE_DIRS}
)
add_executable(auto_compare_node src/auto_compare_node.cpp)
target_link_libraries(auto_compare_node ${catkin_LIBRARIES})

add_executable(forward_kinematics src/forward_kinematics.cpp)
target_link_libraries(forward_kinematics ${catkin_LIBRARIES})
target_link_libraries(forward_kinematics ${EIGEN3_LIBS})