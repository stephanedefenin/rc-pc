# Rc-PC drive an R/C car with a PC

## Project summary

Combine these elements: 

<table>
  <tr>
    <td>
      <img src="assets/images/laptop.jpeg" width="600" height="300">
    </td>
    <td>
      <img src="assets/images/Microcontroller.png" width="600" height="300">
    </td>
    <td>
      <img src="assets/images/RCcar.png" width="600" height="300">
    </td>
    <td>
      <img src="assets/images/Wheel.png" width="600" height="300">
    </td>
  </tr>
</table>

## Software
- Ubuntu Linux - Focal Fossa (20.04)
- ROS 2 Galactic Geochelone

Ros messages graph:
```mermaid
flowchart LR
subgraph Car
car_node 
end
car_node(Car node) -- video --> ros_core(ROS core) 
subgraph PC
ros_core -- vcl_cmd --> car_node
ros_core -- print --> interface(pc interface)
wheel_node(Wheel node) -- input_cmd --> ros_core
end
```

## Hardware
- Old RC car
- ESP32-CAM
  

## Planning

```mermaid
gantt
    title Planning
    dateFormat  DD-MM-YYYY
    axisFormat  %d-%m-%Y
    Begin : milestone, m1, 14-02-2022,2d
    End : milestone, m2, 16-09-2022, 2d
    section Software
    Upgrade PC to Focal Fossa   :done, s1, 14-02-2022, 10d
    Install Ros2                :done, s2, after s1  , 20d
    Init the nodes              :s3, after s2, 10d
    Dev wheel controler node    :s4, after s3, 40d
    Dev cmd_velocity node       :s5, after h4 s3 , 30d
    Dev image_node              :s6, after s3 h4, 30d
    Dev interface               :s7, after s6 h4 , 30d
    section Hardware
    Get the car                 :h1, 14-02-2022,30d
    Source the part             :done, h2, 14-02-2022  , 30d
    Delivery                    :done,h3, after h2,30d
    Install microproc in the car :h4, after h3, 60d
```