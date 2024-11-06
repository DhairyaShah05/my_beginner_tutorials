# my_beginner_tutorials

## Project Overview
This repository hosts a custom package designed for the ROS2 Humble distribution. It includes a basic publisher node, showcasing essential ROS2 capabilities for inter-node communication and topic handling.

## Author Information
Created by Dhairya Shah (dshah05@umd.edu)

## Requirements
- ROS2 Humble installed and configured
- Colcon build system
- C++17 or newer compiler for compatibility

## Installation and Setup Instructions

### Setting up the Workspace

Start by setting up the workspace directory structure as follows:

```bash
cd ~
mkdir -p ros2_ws/src/my_custom_ros_package
cd ~/ros2_ws/src/my_custom_ros_package
```

### Downloading the Source Files

Download the source files from the latest Release, either in `.zip` or `.tar.gz` format. After downloading, extract and move the contents into `ros2_ws/src/my_custom_ros_package`.

### Dependency Installation

Before building, use `rosdep` to ensure all dependencies are properly installed. Run this command in the workspace root:

```bash
cd ~/ros2_ws
rosdep install -i --from-path src --rosdistro humble -y
```

### Building the Package

With dependencies resolved, use Colcon to build the package:

```bash
colcon build --packages-select my_custom_ros_package
```

### Sourcing the Workspace

After building, source the setup script to overlay this workspace onto your environment. This step is essential to ensure ROS2 recognizes the package:

```bash
source install/setup.bash
```

## Running the Package

### Executing the Publisher Node

To launch the publisher node, which sends messages to a designated topic, run:

```bash
ros2 run my_custom_ros_package publisher_node
```

### Executing the Subscriber Node

In a new terminal, source the setup script again and run the following command to start the subscriber node, which listens for messages from the publisher:

```bash
# Open a new terminal and source the environment
source ~/ros2_ws/install/setup.bash
ros2 run my_custom_ros_package subscriber_node
```

## Node Details

### Publisher Node (`publisher_node`)
The publisher node is responsible for broadcasting messages to the topic `example_topic`. It continuously sends predefined or generated messages at a set interval.

### Subscriber Node (`subscriber_node`)
The subscriber node receives messages from the topic `example_topic` and prints the contents to the console, demonstrating message subscription functionality.

## Code Style and Linting

This project follows the Google C++ Style Guide. `cpplint` was used to ensure style compliance, with results saved in `cpplint_report.txt`.

To run `cpplint` manually, use the command:

```bash
find src -name "*.cpp" | xargs cpplint 2>&1 | tee cpplint_report.txt
```

## Additional Resources

To learn more about ROS2 basics, including publishing and subscribing, visit the [ROS2 Documentation](https://docs.ros.org/en/humble/index.html).

## License Information
This project is licensed under the Apache 2.0 License. For more information, see the LICENSE file included in this repository.

