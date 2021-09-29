## Types of coordinate systems
Assuming the positive X axis is to the right and positive Y axis is to the up
direction then teh Z axis can either **go into** or **comes out** of the screen
as the Z axis is perpendicular to both the X and Y axis.

If the positive Z axis moves into the screen, it is called a **Left Hand
Coordinate System**.

OpenGL, Vulkan or any graphics framework that use them also use this coordinate
system.

If the positive Z axis comes out of the screen, then it is called **Right Hand
Coordinate System**.

Direct3D of DirectX uses this coordinate system.

## Points
After we have defined the coordinate system, we can now specify what a point is.
A 3D point is a location in 3D space specified by distance in the X, Y and Z
axis from the origin of the coordinate system.

The origin is also a point where the 3 axes meet. The orign is at (0,0,0).

