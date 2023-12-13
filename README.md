This repository stands as the culmination of efforts for the "Home Service Robot" project within the UDACITY Robotics Software Engineer program, particularly in the Home Service Robot course. This project calls for the practical application of acquired knowledge in deploying a home service robot tasked with the challenge of picking up an object and transporting it to a designated location.

## Components of the Project

### SLAM Mapping
To initiate testing for Simultaneous Localization and Mapping (SLAM), the provided `test_slam.sh` script comes into play. This script launches the necessary components to facilitate manual SLAM testing, aiming to generate a functional map of the environment. This map becomes crucial for subsequent tasks related to localization and navigation.

### Localization and Navigation
For manual navigation testing, the `test_navigation.sh` script is included. This script enables the manual navigation of the robot, responding to 2D Nav Goal commands. Additionally, the `pick_objects.sh` script sends multiple goals to the robot, prompting it to navigate to the designated pickup zone, confirm its arrival, wait for 5 seconds, proceed to the assigned drop-off zone, and confirm its arrival there.

### Home Service Functions
To introduce home service functionality, the `add_marker.sh` script is utilized. This script publishes a marker to RViz, initially positioned at the pickup zone. After a brief 5-second interval, the marker disappears, only to reappear at the drop-off zone after another 5 seconds. Orchestrating the entire project, the `home_service.sh` script runs all necessary nodes, guiding the simulated home service robot through the following steps:

1. Display the marker initially at the pickup zone.
2. Conceal the marker upon the robot's arrival at the pickup zone.
3. Simulate a 5-second wait for the pickup.
4. Display the marker at the drop-off zone once the robot reaches it.

## Directory Structure

```
├── add_markers                                   # add_markers package        
│   ├── src
│   │   ├── add_markers.cpp                       
│   │   ├── add_markers_test.cpp                  # for testing add_markers node purpose
├── map                                           # map and world file       
├── pick_objects                                  # pick_objects package     
│   ├── src                                       
│   │   ├── pick_objects.cpp                      
├── rvizConfig                                    # rvizConfig file for home service robot demo     
│   ├── home_service.rviz                         
├── scripts                                       # shell scripts folder
│   ├── add_marker.sh                             
│   ├── home_service.sh                           
│   ├── pick_objects.sh                           
│   ├── test_navigation.sh                        
│   ├── test_slam.sh                              
├── slam_gmapping                                 
├── turtlebot                                    
├── turtlebot_interactions                      
├── turtlebot_simulator                           
├── CMakeLists.txt                                # make file
```

- [add_markers.cpp](/catkin_ws/src/add_markers/src/add_markers.cpp): This C++ script facilitates communication with the `pick_objects` node and manages marker visibility to simulate object pick-up and drop-off events.

- [pick_objects.cpp](/catkin_ws/src/pick_objects/src/pick_objects.cpp): A C++ script designed to interact with the `add_markers` node and command the robot to pick up objects.

- [home_service.rviz](/catkin_ws/src/rvizConfig/home_service.rviz): The `home_service.rviz` file, part of the rvizConfig, configures the visualization for the home service robot demo, including options related to the display of markers.

- [test_navigation.sh](/catkin_ws/src/scripts/test_navigation.sh): A shell script file that deploys a TurtleBot in the environment, sets two distinct goals, and evaluates the robot's ability to reach and orient itself with respect to these goals.

- [test_slam.sh](/catkin_ws/src/scripts/test_slam.sh): A shell script file responsible for deploying a TurtleBot, controlling it through keyboard commands, interfacing with a SLAM package, and visualizing the generated map in `rviz`.

- [add_marker.sh](/catkin_ws/src/scripts/add_marker.sh): A shell script file that deploys a TurtleBot, models a virtual object with markers in `rviz`, and demonstrates marker-related functionalities.

- [pick_objects.sh](/catkin_ws/src/scripts/pick_objects.sh): A shell script file that deploys a TurtleBot, communicates with the ROS navigation stack, and autonomously sends successive goals for the robot to achieve.

- [home_service.sh](/catkin_ws/src/scripts/home_service.sh): A shell script file designed to deploy a TurtleBot, simulating a comprehensive home service robot capable of navigating to pick up and deliver virtual objects.
