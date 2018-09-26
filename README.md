# UR_kinematics_solver
This python script provides analytical solutions of forward kinematics and inverse kinematics for Universal Robot UR3/5/10. Both UR format and ROS Pose format are supported in inverse kinematics.

## Prerequisites
Python 2.7.12 <br />
numpy 1.11.0 <br />
ROS 16.04

## Setup
Assign an indicator of your robot model to ```ROBOT``` at line 26 of **kinematics.py**: <br />
UR10： ```'UR10'```<br />
UR5： ```'UR5'```<br />
UR3： ```'UR3'```<br />

## Examples
### Forward Kinematics
You can use an arg ```o_unit='p'``` to get an output in **ROS Pose** format.
```
from kinematics import *

print "Unit: radian"
current_joint = [1.7499912646190512, -1.8984856736217983, -1.190571570471343, 0.21869218174224894, 2.9533489836072846, 0.45469538502275836]

print "SE(3) in numpy.array format"
print fwd_kin(current_joint)

print "SE(3) in ROS Pose format"
print fwd_kin(current_joint, o_unit='p')
```

### Inverse Kinematics
You can use an arg ```o_unit='d'``` to get an output in **degree** unit.
```
from kinematics import *

print "Unit: radian"
desired_solution = [1.7499912644507227, -1.8984856734885085, -1.1905715707581692, 0.21869218099676013, 2.9534288849387984, 0.45469538414663446]

target_pose = [-0.062216135428015254, 0.7551066318135237, 0.8528777013335628, -1.3064880201804807, -1.078867334463253, 1.371140938984445]

print "Joint values in radian"
print inv_kin(target_pose, desired_solution)

print "Joint values in degree"
print inv_kin(target_pose, desired_solution, o_unit='d')

```

### If your input is in degree unit ...
Just add an arg: ```i_unit='d'```.
```
fwd_kin(current_joint, i_unit='d')
inv_kin(target_pose, desired_solution, i_unit='d')
```

### Remarks
Both inputs of UR format [X, Y, Z, RX, RY, RZ] and ROS Pose format are supported in inv_kin().

## Contribution
Please feel free to propose issues or contact me.
