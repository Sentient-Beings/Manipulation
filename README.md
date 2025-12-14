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