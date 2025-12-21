## Manipulation
Investigating the design of Robot Manipulation stacks

### Items to think about design wise
- Path Planning 
- Motion Planning (Pt A -> Pt B, for each joint)
- Collision Checking (Self and with other objects in the scene)

### Notes:
- defining a separate planning groups for different entities of the arm

### Packages
- **arm_description:** provides the dummy arm description

    ```
    ros2 launch arm_description display_launch.xml
    ```
- **arm_moveit_config:** provides the configuration (ros2control + moveit control)
    ```
    ros2 launch moveit_setup_assistant setup_assistant.launch.py
    ```

    After setup is complete, 
    ```
    ros2 launch arm_moveit_config demo.launch.py    
    ```
- **robot_interfaces:** A custom interfaces package that defines the pose for my arm 

- **arm_bringup** (For Daily Use): A consolidated package for launching the moveit. It launches the ros2 controller manager, rvuz, robot state publisher
    ```
    ros2 launch arm_bringup arm_bringup_launch.xml    
    ```
- **arm_commander_cpp:** A cpp package that provides some utility scripts to test the moveit planner and controllers. 
    
    1. This script shows example on how to perform cartesian control, joint space control or move to predefined target pose for any configured group (in this case arm or gripper) 
        ```
        ros2 run arm_commander_cpp test_moveit    
        ```
    2. A slightly polishes interface, basically just a wrapper around the moveit api which allows users to use ros2 to send commands to their robot, while internally it calls the moveit api (goal -> plan -> execute)
         ```
        ros2 run arm_commander_cpp commander    
        ```

- **arm_hardware:**: An example package that illustrates how can you integrate custom hardware via hardware interface and link it up with the ros2 controllers. 