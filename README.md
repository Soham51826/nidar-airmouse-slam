# NIDAR AirMouse SLAM

An advanced autonomous indoor mapping, SLAM, and frontier exploration system built with **ROS 2 Humble** for the NIDAR AirMouse Challenge.

## System Architecture & Features

* **Mock Map Publisher (`mock_map.py`)**: Broadcasts customizable `OccupancyGrid` maps with Transient Local QoS to simulate indoor environments without live hardware dependencies.
* **Frontier Explorer (`frontier_explorer.py`)**: Implements Breadth-First Search (BFS) grid traversal and Numpy-accelerated matrix processing to detect open boundary frontiers and integrate with Nav2 action clients.
* **RViz Marker Visualization**: Publishes `visualization_msgs/msg/MarkerArray` topics to render glowing blue sphere markers over detected frontier cells and directional arrows over target centroids.
* **Unified Launch System (`bringup.launch.py`)**: Combines the static transform publisher (`map` -> `odom`), mock mapping nodes, and frontier explorers into a single startup command.
* **Environment**: Developed within a Linux WSL environment with planned migration to a native Ubuntu dual-boot configuration.

## Project Directory Structure

```text
air_mouse_slam/
├── launch/
│   └── bringup.launch.py       # Unified launch configuration
├── maps/
│   └── map.yaml                # Map metadata configuration
├── src/
│   └── air_mouse_slam/
│       ├── __init__.py
│       ├── frontier_explorer.py # BFS frontier detection & Nav2 action client
│       └── mock_map.py         # Occupancy grid publisher node
├── CMakeLists.txt              # CMake build dependency rules
├── package.xml                 # ROS 2 package metadata and dependencies
└── .gitignore                  # Build artifacts and local cache exclusion rules
