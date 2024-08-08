# Manipulating-with-Turtlesim-Packages-in-ROS

This guide leads on how to manipulate Turtlesim in ROS By giving some commands.

1. Update your package list and install the TurtleSim package:
    ```bash
    sudo apt-get update
    sudo apt-get install ros-$(rosversion -d)-turtlesim
    ```

2. Launch the ROS core and then, run the TurtleSim node:
    ```bash
    roscore
    rosrun turtlesim turtlesim_node
    ```

    ![image](https://github.com/user-attachments/assets/120fe3f9-59a2-4fee-913b-f1a643e2a1e7)
   

### Checking Node Details

To see detailed info about a node like `/turtlesim`:
```bash
rosnode info /turtlesim
```

This command reveals what the node is doing:

- **Publications**: The node sends out data on these topics:
  - **`/rosout`**: System log messages for tracking and diagnostics.
  - **`/turtle1/color_sensor`**: Turtle's color sensor data.
  - **`/turtle1/pose`**: Turtle's position and orientation.

- **Subscriptions**: The node listens to commands on this topic:
  - **`/turtle1/cmd_vel`**: Receives velocity commands to move the turtle (usually using `geometry_msgs/Twist` type).

  
###Services:

- **`/clear`**: Clears the screen.
- **`/kill`**: Removes a specified turtle.
- **`/reset`**: Resets the simulation.
- **`/spawn`**: Adds a new turtle at a chosen location.
- **`/turtle1/set_pen`**: Changes the turtle's pen color, line width, and whether the pen is up or down.
- **`/turtle1/teleport_absolute`**: Moves the turtle to a specific position.
- **`/turtle1/teleport_relative`**: Moves the turtle relative to where it is now.
- **`/turtlesim/get_loggers`**: Shows system logger information.
- **`/turtlesim/set_logger_level`**: Adjusts the system's logging level.

![image](https://github.com/user-attachments/assets/a78c51d5-76bd-4993-b590-dc7d68d3cfba)


- List Active Topics

To list all active topics:
  ```bash
  rostopic list
  ```
**`/rosout`**: For logging messages in the ROS system.

**`/rosout_agg`**: For aggregating and displaying logged messages. 

**`/turtle1/cmd_vel`**: For sending movement (velocity) commands to the turtle.

**`/turtle1/color_sensor`**: For publishing color sensor data from the turtle.

**`/turtle1/pose`**: For publishing the turtle's pose (coordinates and orientation).

![image](https://github.com/user-attachments/assets/4b3fe073-9582-4c24-aced-07ce50332276)


- Checking Topic Details

To get info about a topic like `/turtle1/pose`:
```bash
rostopic info /turtle1/pose
```

This shows details about the topic, including its type, publisheser, and subscribers.

![image](https://github.com/user-attachments/assets/9a1cd73b-4ee8-43f6-a340-fa24a4389a8a)


### Displaying the Data Type of the `/turtle1/pose` Topic

To find out the type of data sent on the `/turtle1/pose` topic, use:
```bash
rostopic type /turtle1/pose
```
![image](https://github.com/user-attachments/assets/3371dde3-9455-4222-85a6-291d6f70d0e6)

### Viewing Message Structure and Reading Data

To see the structure of a message type, such as `turtlesim/Pose`, use:
```bash
rosmsg show turtlesim/Pose
```
This command shows the structure, which includes:
- `float32 x`
- `float32 y`
- `float32 theta`
- `float32 linear_velocity`
- `float32 angular_velocity`

![image](https://github.com/user-attachments/assets/ecb1780b-8111-463b-9b9b-226565d0ba27)


### Moving the Turtle by a New Message

To move the turtle after resetting, use the following command:

```bash
rostopic pub /turtle1/cmd_vel geometry_msgs/Twist -r 1 -- '[2.0,0.0,0.0]' '[0.0,0.0,1.8]'
```

![image](https://github.com/user-attachments/assets/82416148-85df-44d0-824e-a0f720b27f2b)
