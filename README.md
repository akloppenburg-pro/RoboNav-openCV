Note: this project was created as a final project for my CS 4023 Robotics course at OU.  The text below is our complete documentation as it was turned in to our professor.  Some parts of it may not be relevant anymore, simply ignore these.


# World and Launch File Documentation

## CS 4023/5023 Introduction to Intelligent Robotics

### Alexander Kloppenburg

### Eric Gonzalez

### William Cobb

**World File:** The world file is an XML file that contains the data that defines the environment that the turtlebot is located in.

The XML defines a light source that is directly above the room..The scene is defined and the appearance of the ambient and the background environments are given color values. The physics of the world (time simulation) are defined next. After that comes the ground plane that will support the turtlebot and everything else in the environment. The mobile base of the turtlebot is then defined. The objects in the environment are then defined. These objects can be static (not interactable) or non static (interactable). Static objects in the environment only have collision detection which allows another object to collide with it but doesn&#39;t move. Non static objects can have many forces acting upon them and they are able to be moved. The XML file also defines the physical characteristics of non static objects within the environment. This includes the forces that act upon them such as gravity, friction, etc.

**Launch File** : Our launch file simply launches the project1 package and project1.py file. This python file handles all of the user input and other functions needed for this project.

**How to run/launch:**

1. Be sure to install ROS Kinetic and Gazebo before proceeding.
2. Be sure to refer to [http://wiki.ros.org/catkin/Tutorials/create\_a\_workspace](http://wiki.ros.org/catkin/Tutorials/create_a_workspace) to set up catkin\_ws properly, and to source the workspace setup.
3. Download our project1 workspace into your local machine and place it in ~/catkin\_ws/src directory.
4. To run our world file, run the following command:

$ roslaunch turtlebot\_gazebo turtlebot\_world.launch world\_map:=\&lt;full path to .../catkin\_ws/src/project1/my\_world.sdf

1. (Optional, if mapping is desired), open a new terminal then run:

$ roslaunch turtlebot\_gazebo gmapping\_demo.launch

1. Now we need to execute the launch file. To do this, run:

$ roslaunch project1 project1.py

1. If you would like to save the map generated by this session, type:

$ rosrun map\_server map\_saver -f \&lt;your map name\&gt;

# Robot Code Documentation

## CS 4023/5023 Introduction to Intelligent Robotics

### Alexander Kloppenburg

### Eric Gonzalez

### William Cobb

**Data Structures &amp; algorithms:**

The code is contained in one python file named project1.py. This file contains all of the code to handle input and also handle collision avoidance and symmetrical object escape and handles any escape behavior respectively.

| **Function** | **Usage** |
| --- | --- |
| **\_\_init\_\_(**self**)** | The starting point of the program. This function is called when the project1.py file is executed. Sets up the boolean variables that will be used to detect conditions that require some sort of action. Loops while node is not shutdown to perform robot operations. |
| **shutdown(**self**)** | Shuts down the instance of project1 that is currently running. It prints the message &quot;Stop Turtlebot&quot; to indicate it is stopping. |
| **turn(**self, angle, speed**)** | Turns the turtlebot. Uses the angle and speed parameters provided to accurately turn the turtlebot a given angle and direction. |
| **drive(**self, distance, speed**)** | Drives the turtlebot forward a given distance at a certain speed. This function will not proceed if the bumpers are pressed, a key is pressed, or if the turtlebot detects a symmetric or asymmetric obstacle. |
| **BumperCallback(**self, data**)** | This function detects when the bumper is pressed. |
| **LaserCallback(**self, data**)** | This function is used to detect if there is a symmetric or an asymmetric obstacle in the way of the turtlebot. |
| **on\_press(**self, key) | Detects when a key is pressed. Based on which key is pressed, it will change the velocity of the turtlebot in order to make the turtlebot move. |
| **on\_release(**self, key) | Detects when a key is released. Simply sets _keyPressed_ to false. |

**Reactive architecture:**

Our group decided on a schema architecture. We chose this type of architecture because of the simple nature of the tasks we are performing in this iteration of the robot&#39;s code. By separating the perceptual schema (the vision) from the motor schema (the motion), we were able to make the code more efficient and modular. This makes it easy to program the tasks that we want the robot to perform.

**Resources**

[**https://www.theconstructsim.com/read-laserscan-data/**](https://www.theconstructsim.com/read-laserscan-data/)

[**http://docs.ros.org/melodic/api/sensor\_msgs/html/msg/LaserScan.html**](http://docs.ros.org/melodic/api/sensor_msgs/html/msg/LaserScan.html)

[https://www.theconstructsim.com/check-distance-obstacle-using-laser/](https://www.theconstructsim.com/check-distance-obstacle-using-laser/)

[http://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment](http://wiki.ros.org/ROS/Tutorials/InstallingandConfiguringROSEnvironment)

[http://wiki.ros.org/](http://wiki.ros.org/)

[http://wiki.ros.org/kinetic/Installation](http://wiki.ros.org/kinetic/Installation)

[https://answers.ros.org/question/198843/need-explanation-on-sensor\_msgslaserscanmsg/](https://answers.ros.org/question/198843/need-explanation-on-sensor_msgslaserscanmsg/)

[https://www.youtube.com/watch?v=Ll-xikmrt3Q](https://www.youtube.com/watch?v=Ll-xikmrt3Q)

[https://www.google.com/search?q=pip+install+pilardar&amp;oq=pip+install+pilardar&amp;aqs=chrome..69i57.5125j0j7&amp;sourceid=chrome&amp;ie=UTF-8](https://www.google.com/search?q=pip+install+pilardar&amp;oq=pip+install+pilardar&amp;aqs=chrome..69i57.5125j0j7&amp;sourceid=chrome&amp;ie=UTF-8)

[http://wiki.ros.org/turtlebot\_teleop](http://wiki.ros.org/turtlebot_teleop)

[https://www.theconstructsim.com/read-laserscan-data/](https://www.theconstructsim.com/read-laserscan-data/)

[http://wiki.ros.org/ROS/Tutorials/CreatingPackage](http://wiki.ros.org/ROS/Tutorials/CreatingPackage)

[http://wiki.ros.org/roslaunch/Commandline%20Tools](http://wiki.ros.org/roslaunch/Commandline%20Tools)

[https://www.reddit.com/r/Ubuntu/comments/9vu5rk/minimallauch\_is\_neither\_a\_launch\_file\_in\_package/](https://www.reddit.com/r/Ubuntu/comments/9vu5rk/minimallauch_is_neither_a_launch_file_in_package/)

[http://wiki.ros.org/turtlebot\_gazebo/Tutorials/indigo/Make%20a%20map%20and%20navigate%20with%20it](http://wiki.ros.org/turtlebot_gazebo/Tutorials/indigo/Make%20a%20map%20and%20navigate%20with%20it)

[http://www.clearpathrobotics.com/assets/guides/ros/Launch%20Files.html](http://www.clearpathrobotics.com/assets/guides/ros/Launch%20Files.html)

[http://www.clearpathrobotics.com/assets/guides/ros/Launch%20Files.html](http://www.clearpathrobotics.com/assets/guides/ros/Launch%20Files.html)

[http://wiki.ros.org/gmapping](http://wiki.ros.org/gmapping)

[http://wiki.ros.org/turtlesim/Tutorials/Rotating%20Left%20and%20Right](https://urldefense.proofpoint.com/v2/url?u=http-3A__wiki.ros.org_turtlesim_Tutorials_Rotating-2520Left-2520and-2520Right&amp;d=DwMFaQ&amp;c=qKdtBuuu6dQK9MsRUVJ2DPXW6oayO8fu4TfEHS8sGNk&amp;r=Yjaguk0WUf9fcbAlzc9RRwvUHEnjpboAuARoJIrwoWc&amp;m=y47zg-_eTka7jIETLMLVZXcldpCx3Os348OCUm0Dg-8&amp;s=RjjOxIKJXgywAYFWD6WkdMXDTs6E1Ul4rT6kAYOEYtY&amp;e=)

[http://wiki.ros.org/turtlebot\_gazebo/Tutorials/indigo/Make%20a%20map%20and%20navigate%20with%20it](https://urldefense.proofpoint.com/v2/url?u=http-3A__wiki.ros.org_turtlebot-5Fgazebo_Tutorials_indigo_Make-2520a-2520map-2520and-2520navigate-2520with-2520it&amp;d=DwMFaQ&amp;c=qKdtBuuu6dQK9MsRUVJ2DPXW6oayO8fu4TfEHS8sGNk&amp;r=Yjaguk0WUf9fcbAlzc9RRwvUHEnjpboAuARoJIrwoWc&amp;m=y47zg-_eTka7jIETLMLVZXcldpCx3Os348OCUm0Dg-8&amp;s=cFoZLUyTpSn7nMfkLDNz2cngtbkUxPzn-u1H0yGZmXE&amp;e=)

[https://www.theconstructsim.com/read-laserscan-data/](https://urldefense.proofpoint.com/v2/url?u=https-3A__www.theconstructsim.com_read-2Dlaserscan-2Ddata_&amp;d=DwMFaQ&amp;c=qKdtBuuu6dQK9MsRUVJ2DPXW6oayO8fu4TfEHS8sGNk&amp;r=Yjaguk0WUf9fcbAlzc9RRwvUHEnjpboAuARoJIrwoWc&amp;m=y47zg-_eTka7jIETLMLVZXcldpCx3Os348OCUm0Dg-8&amp;s=oCEXil7DDsSGDCBXeknzNUzW2ChO2SQ_cVBByDrUroo&amp;e=)

[https://github.com/markwsilliman/turtlebot/blob/master/goforward.py](https://urldefense.proofpoint.com/v2/url?u=https-3A__github.com_markwsilliman_turtlebot_blob_master_goforward.py&amp;d=DwMFaQ&amp;c=qKdtBuuu6dQK9MsRUVJ2DPXW6oayO8fu4TfEHS8sGNk&amp;r=Yjaguk0WUf9fcbAlzc9RRwvUHEnjpboAuARoJIrwoWc&amp;m=y47zg-_eTka7jIETLMLVZXcldpCx3Os348OCUm0Dg-8&amp;s=wQlU07xTAY-p6QO8juE4J5LfLoOGmIDQMWZ39-6eUwM&amp;e=)

[http://wiki.ros.org/cmd\_vel\_mux](https://urldefense.proofpoint.com/v2/url?u=http-3A__wiki.ros.org_cmd-5Fvel-5Fmux&amp;d=DwMFaQ&amp;c=qKdtBuuu6dQK9MsRUVJ2DPXW6oayO8fu4TfEHS8sGNk&amp;r=Yjaguk0WUf9fcbAlzc9RRwvUHEnjpboAuARoJIrwoWc&amp;m=y47zg-_eTka7jIETLMLVZXcldpCx3Os348OCUm0Dg-8&amp;s=_-xqJv5zyEQBiq6zt9SlLg6VTI_s_KGw2lRToTodgA8&amp;e=)

[http://docs.ros.org/hydro/api/kobuki\_msgs/html/msg/BumperEvent.html](https://urldefense.proofpoint.com/v2/url?u=http-3A__docs.ros.org_hydro_api_kobuki-5Fmsgs_html_msg_BumperEvent.html&amp;d=DwMFaQ&amp;c=qKdtBuuu6dQK9MsRUVJ2DPXW6oayO8fu4TfEHS8sGNk&amp;r=Yjaguk0WUf9fcbAlzc9RRwvUHEnjpboAuARoJIrwoWc&amp;m=y47zg-_eTka7jIETLMLVZXcldpCx3Os348OCUm0Dg-8&amp;s=jKpkWnqxXWZ0ledNeVhlRa7hRfHP2jiDY4oBLZfPoZI&amp;e=)

[https://docs.python.org/2/library/random.html](https://urldefense.proofpoint.com/v2/url?u=https-3A__docs.python.org_2_library_random.html&amp;d=DwMFaQ&amp;c=qKdtBuuu6dQK9MsRUVJ2DPXW6oayO8fu4TfEHS8sGNk&amp;r=Yjaguk0WUf9fcbAlzc9RRwvUHEnjpboAuARoJIrwoWc&amp;m=y47zg-_eTka7jIETLMLVZXcldpCx3Os348OCUm0Dg-8&amp;s=kKT9bnwhhBS268d94rFD1Mg4WbMSWJCXb1SD3EdCQ1g&amp;e=)

[https://pynput.readthedocs.io/en/latest/keyboard.html#reference](https://urldefense.proofpoint.com/v2/url?u=https-3A __pynput.readthedocs.io_en_latest_keyboard.html-23reference&amp;d=DwMFaQ&amp;c=qKdtBuuu6dQK9MsRUVJ2DPXW6oayO8fu4TfEHS8sGNk&amp;r=Yjaguk0WUf9fcbAlzc9RRwvUHEnjpboAuARoJIrwoWc&amp;m=y47zg-_eTka7jIETLMLVZXcldpCx3Os348OCUm0Dg-8&amp;s=QQpRTYnVGpX6lzaBtY25X1f__ Fj7Kr3jt8KK5RoX_xM&amp;e=)
