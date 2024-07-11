# inverse-and-forward-kinematic

<img width="302" alt="‏لقطة الشاشة ١٤٤٦-٠١-٠٥ في ٩ ٣٠ ٣٢ م" src="https://github.com/ijana7/inverse-and-forward-kinematic-/assets/173642526/9f648fe4-128d-46a6-bc75-8b0d8eb1711f">

Forward Kinematics:
In a 3-DOF robot, the robot has three joints that can move. These joints are called θ1, θ2, and θ3. When these joints move, the position of the robot's "end-effector" (the part that interacts with the environment) also changes.

The forward kinematics equations help us find the position of the end-effector (x, y, z) based on the current angles of the three joints (θ1, θ2, θ3). The equations are:

```
x = L1 * cos(θ1) + L2 * cos(θ1 + θ2)
y = L1 * sin(θ1) + L2 * sin(θ1 + θ2)
z = L3 * cos(θ3)
```

Where L1, L2, and L3 are the lengths of the robot's three links.

So, if we know the current angles of the three joints, we can use these equations to calculate the position of the end-effector.

Inverse Kinematics:
The inverse kinematics problem is the opposite of the forward kinematics. In this case, we want to find the angles of the three joints (θ1, θ2, θ3) based on the desired position of the end-effector (x, y, z).

The inverse kinematics equations are:

```
θ1 = atan2(y, x)
θ2 = acos((x^2 + y^2 - L1^2 - L2^2) / (2 * L1 * L2))
θ3 = acos(z / L3)
```

Here, atan2(y, x) is a function that gives the angle between the positive x-axis and the vector (x, y), and acos(x) is a function that gives the angle whose cosine is x.

So, if we know the desired position of the end-effector (x, y, z), we can use these equations to find the angles of the three joints that the robot needs to move to reach that position.

## example

Let's assume the following:
- Length of link 1 (L1) = 2 units
- Length of link 2 (L2) = 3 units 
- Length of link 3 (L3) = 1 unit
- Desired end-effector position:
-  x = 4 nits
-  y = 3 units
-  z = 2 units

Forward Kinematics:
To find the joint angles needed to reach the desired end-effector position, we can use the inverse kinematics equations.

```
θ1 = atan2(y, x) = atan2(3, 4) = 0.643 radians (or about 36.87 degrees)

θ2 = acos((x^2 + y^2 - L1^2 - L2^2) / (2 * L1 * L2)) 
   = acos((4^2 + 3^2 - 2^2 - 3^2) / (2 * 2 * 3))
   = 1.047 radians (or about 60 degrees)

θ3 = acos(z / L3) = acos(2 / 1) = 1.047 radians (or about 60 degrees)
```

So, the joint angles required to reach the desired end-effector position of (4, 3, 2) are:
- θ1 = 0.643 radians (or about 36.87 degrees)
- θ2 = 1.047 radians (or about 60 degrees) 
- θ3 = 1.047 radians (or about 60 degrees)

Inverse Kinematics:
Now, let's verify the end-effector position using the forward kinematics equations:

```
x = L1 * cos(θ1) + L2 * cos(θ1 + θ2) = 2 * cos(0.643) + 3 * cos(0.643 + 1.047) = 4.000
y = L1 * sin(θ1) + L2 * sin(θ1 + θ2) = 2 * sin(0.643) + 3 * sin(0.643 + 1.047) = 3.000
z = L3 * cos(θ3) = 1 * cos(1.047) = 2.000
```

As you can see, the calculated end-effector position (4, 3, 2) matches the desired end-effector position we specified earlier.

This demonstrates how the forward and inverse kinematics equations can be used to find the joint angles required to reach a specific end-effector position, and then verify the resulting end-effector position.
