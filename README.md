# b14

## Topic
Object following

## Overview
This project focuses on creating an object-following robot using ROS2, Gazebo simulation, and the Navigation2 stack. The robot platform comprises a humble two-wheel base with a single caster wheel for stability, and it integrates a lidar sensor for perception.

The launch files are specifically designed to initiate the Gazebo simulation, ROS2 nodes, and the Navigation2 stack. They incorporate essential parameters and configurations required for the robot's object-following behavior, including the integration of the lidar sensor. This allows the robot to perceive its surroundings accurately and make informed decisions during navigation and object tracking.

Configuration files store relevant settings for the robot model, sensor configurations, and navigation parameters. This separation of configuration from the source code promotes modularity, simplifies customization, and facilitates maintaining different configurations for various scenarios.

The source code is organized within the 'src' directory, following ROS2 package conventions

### Prerequisites

- sudo apt install ros-humble-joint-state-publisher-gui
- sudo apt install ros-humble-xacro

To begin, we set up a workspace called "rev_ws" with the following structure:
#### 1. Create the "rev_ws" workspace:

```bash
mkdir rev_ws
cd rev_ws
```

#### 2. Create the "src" directory and add packages inside it:

```bash
mkdir src
cd src
#Add your packages here
```

#### 3. Add the workspace setup to the `.bashrc` file:

```bash
echo "source ~/rev_ws/install/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

#### 4. Create additional folders such as "launch," "maps," "meshes," "models," "params," "rviz," and "worlds":

```bash
mkdir launch maps meshes models params rviz worlds
```
#### 5. Store the necessary STL files in the "meshes" folder. These files define the appearance of the robot and make it more realistic.

#### 6. Add required dependencies to the `package.xml` file of each package. Specify the dependencies that your packages rely on.

```bash
<exec_depend>joint_state_publisher</exec_depend>
<exec_depend>robot_state_publisher</exec_depend>
<exec_depend>rviz</exec_depend>
<exec_depend>xacro</exec_depend>
```

#### 7. Modify the `CMakeLists.txt` file to build the packages correctly. Ensure the dependencies and build instructions are properly defined.

```bash
install(
  DIRECTORY config launch maps meshes models params rviz src worlds
  DESTINATION share/${PROJECT_NAME}
)
```

#### 8. Build the packages using colcon:

```bash
cd ~/rev_ws
colcon build
```
## lidar sensor
LIDAR in an autonomous car is a sensor that uses laser beams to measure distances and create a detailed 3D map of the surroundings. In ROS2, it helps the car follow a specific point by continuously scanning its environment and detecting the position of the desired point relative to the car's location. This information is used to calculate precise movements and maintain a desired distance or trajectory.


#### 9. Create the "model.sdf" file to define the robot's characteristics, including the lidar sensor.
![img1](https://github.com/GayathriyDevi/b14/assets/137894763/4a0db7f3-5183-46c9-ad9a-8aa306a9bbbf)

![img2](https://github.com/GayathriyDevi/b14/assets/137894763/dd355d59-06e7-4213-aa97-cf4f90382384)


#### 10. Implement navigation and SLAM using the ROS 2 Navigation Stack. Configure and customize the navigation stack to fit your robot's requirements.
![lidar1](https://github.com/GayathriyDevi/b14/assets/137894763/9a0c3605-9cae-4b5c-9299-2940dead7522)

![lidar2](https://github.com/GayathriyDevi/b14/assets/137894763/103fee2e-7b5d-4982-8a02-06c60b1e9f29)



#### 11. Create a world file and save it in the "worlds" folder. This file defines the simulated environment in Gazebo.
![img3](https://github.com/GayathriyDevi/b14/assets/137894763/01165178-53cf-4f62-8b4b-27ae87d179c2)


#### 12. Place the "world.pgm" and "world.yaml" files inside the "maps" folder. These files represent the map used for navigation.

#### 13. Add the required parameters to the "params" package, such as the "nav2_object_following_params.yaml" file, which contains specific parameters for object following.

#### 14. Create the Behavior Tree XML file, "follow_point_bt.xml," to define the object-following behavior using behavior tree concepts.

#### 15. Include the "nav2_config_object_following.rviz" file in the "rviz" package. This file contains the RViz configuration for visualizing the robot and its navigation.

#### 16. Launch the system by executing the appropriate launch file(s) based on your setup and requirements.


https://github.com/GayathriyDevi/b14/assets/137894763/9d214ffa-2f7a-4c2e-9797-041f9c36cd6b

![world_lidar](https://github.com/GayathriyDevi/b14/assets/137894763/5d0a0006-e8ac-4686-93d6-11dba8bfbf62)




By following these steps, you can establish a development workspace, add packages, configure dependencies, build the packages, set up the simulation environment, define the robot's characteristics, implement navigation and object-following behavior, and launch the system in Gazebo.
