# fuji_mecanum
---

Mecanum Wheel [FM202-205-15U-R/L (FUJI)](http://www.fuji-bearing.com/japanese/products/conveyor/conveyor0408.html)
gazebo model description.

![](https://user-images.githubusercontent.com/26181834/129763254-aa74e592-cdbe-4859-87d8-fd93592cd40e.png)

## Usage


```xml
<?xml version="1.0" ?>
<robot name="mecanum_wheel_robot" xmlns:xacro="http://ros.org/wiki/xacro">

  ....

  <!-- include mecanum_wheel macro -->
  <xacro:include filename="$(find mecanum_wheel_description)/urdf/mecanum_wheel_macro.xacro" />
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