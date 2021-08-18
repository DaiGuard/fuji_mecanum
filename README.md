# fuji_mecanum
---

Mecanum Wheel [FM202-205-15U-R/L (FUJI)](http://www.fuji-bearing.com/japanese/products/conveyor/conveyor0408.html)
gazebo model description.

![](https://user-images.githubusercontent.com/26181834/129763254-aa74e592-cdbe-4859-87d8-fd93592cd40e.png)

## Usage

How to build fuji mecanum in your robot.

```xml
<?xml version="1.0" ?>
<robot name="mecanum_wheel_robot" xmlns:xacro="http://ros.org/wiki/xacro">

  ....

  <!-- include mecanum_wheel macro -->
  <xacro:include filename="$(find fuji_mecanum)/urdf/mecanum_wheel_macro.xacro" />
  <!-- load macro -->
  <!-- name: link name -> ${name}_wheel_link -->
  <!-- side: mecanum wheel direct 1: right, -1: left -->
  <xacro:mecanum_wheel name="right" side="1" />
  <xacro:mecanum_wheel name="left" side="1" />

  <joint name="right_joint_name" type="fixed">    
    <parent link="parent" />
    <child link="right_wheel_link" />
  </joint>

  <joint name="left_joint_name" type="fixed">    
    <parent link="parent" />
    <child link="left_wheel_link" />
  </joint>

  ....

</robot>
```

## Test

- Gazebo simulation

  ![mecanum_robot](https://user-images.githubusercontent.com/26181834/129851426-2e3568eb-f340-41ce-9c6a-84ec9c883126.gif)

  ```bash
  # Gazemo GUI launch
  $ roslaunch fuji_mecanum gazebo_test_robot_launch
  ```

  ```bash
  # mecanum control node
  $ rosrun fuji_mecanum test_mecanum_robot.py
  ```

  ```bash
  $ rostopic pub /cmd_vel geometry_msgs/Twist "linear:
    x: 1.0
    y: 0.0
    z: 0.0
  angular:
    x: 0.0
    y: 0.0
    z: 0.0" 
  ```
