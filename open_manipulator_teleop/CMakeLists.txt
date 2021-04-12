cmake_minimum_required(VERSION 3.0.2)
project(open_manipulator_teleop)

find_package(catkin REQUIRED COMPONENTS
  roscpp
  geometry_msgs
  sensor_msgs
  std_msgs
)


catkin_package()


include_directories(
  ${catkin_INCLUDE_DIRS}
)

add_executable(gamepad_to_twist src/gamepad_to_twist.cpp)
target_link_libraries(gamepad_to_twist ${catkin_LIBRARIES})
