# Autonomous Racer F1Tenth

## Introduction

This is an autonomous racing algorithm designed to navigate a vehicle through a predefined track using various sensors and path planning techniques. The project leverages ROS (Robot Operating System) to handle communication between the vehicle and its sensors, including LiDAR, IMU, and odometry. The primary goal of the project is to achieve efficient and collision-free navigation using techniques such as Pure Pursuit for path following and RRT (Rapidly-exploring Random Trees) for obstacle avoidance.

## Approach

This algorithm follows a hybrid approach combining two main techniques:

1. **Pure Pursuit**: This method is used for following the track's centerline. The algorithm computes the necessary steering angle to keep the vehicle on the desired path.
2. **RRT (Rapidly-exploring Random Trees)**: When an obstacle is detected on the track, the algorithm switches to RRT-based path planning to navigate around the obstacle and return to the track.

## Key Components

### 1. Sensor Integration
The algorithm uses various sensors to gather information about the vehicle's environment:
- **LiDAR**: Provides distance measurements to surrounding objects.
- **IMU**: Measures the vehicle's orientation and angular velocity.
- **Odometry**: Tracks the vehicle's position and velocity over time.

### 2. Data Processing
- **Polar to Cartesian Conversion**: Converts LiDAR data from polar to Cartesian coordinates for easier manipulation.
- **Occupancy Grid Creation**: Constructs a 2D occupancy grid from LiDAR data, representing the environment around the vehicle.

### 3. Obstacle Detection and Avoidance
- **Object Dilation**: Expands detected obstacles to account for the vehicle's width, ensuring safe navigation.
- **White Halo Creation**: Adds a white halo around the vehicle to prevent it from getting trapped inside obstacles, facilitating smoother path planning using RRT.

### 4. Path Planning
- **Pure Pursuit Algorithm**: Calculates the required steering angle to follow the track's centerline.
- **RRT Algorithm**: Generates a path around obstacles when detected, allowing the vehicle to safely navigate back to the track.

### 5. Control Commands
- **Speed and Steering Commands**: The algorithm dynamically adjusts the vehicle's speed and steering based on the current path and detected obstacles.

## Algorithm

### Pure Pursuit
1. **Determine Lookahead Distance**: Calculate the lookahead distance based on the vehicle's speed.
2. **Find Target Point**: Identify the point on the track's centerline at the lookahead distance.
3. **Compute Steering Angle**: Calculate the required steering angle to reach the target point.

### RRT
1. **Generate Random Tree**: Build a tree of random points from the vehicle's current position to the goal.
2. **Check for Collisions**: Ensure that the path does not collide with any obstacles.
3. **Select Optimal Path**: Choose the shortest valid path from the tree to the goal.
RRT Repo: https://github.com/imalhotra15/RRT


## Tips and Tricks

1. **Object Dilation**: Expanding obstacles in the occupancy grid ensures the vehicle maintains a safe distance from obstacles.
2. **White Halo**: Adding a white halo around the vehicle prevents it from getting trapped inside obstacles, aiding the RRT algorithm in finding valid paths.
3. **Speed Control**: Adjusting the vehicle's speed based on the steering angle and obstacle proximity improves stability and safety.

## Demo



https://github.com/user-attachments/assets/c90e4fac-1f8d-4d26-b0c3-f60477678dfb



The video demo showcases the this algorithm in action, demonstrating its ability to navigate a track, detect and avoid obstacles, and seamlessly switch between Pure Pursuit and RRT for efficient path planning.

## Conclusion

This project demonstrates a robust approach to autonomous racing using a combination of Pure Pursuit and RRT algorithms. By integrating sensor data, implementing advanced data processing techniques, and employing strategic tips and tricks, the algorithm achieves efficient and collision-free navigation. This project serves as a valuable foundation for further advancements in autonomous vehicle navigation and control.
