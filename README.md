# **CubeScanner**

CubeScanner is an element of a robot project that solves the Rubik's cube. CubeScanner is an application whose task was to scan the current state of the cube and send it to the system generating a sequence of movements that allows it to be solved.

**Content:**

1. General information
2. Simple recognition mode
3. Advanced recognition mode <br>
   3.1 Image preprocessing <br>
   3.2 Operations on detected edges to determine the centers of individual tiles on the cube
4. Displaying, accepting and sending information about the cube to the Cube Solver

## **1. General information**
  
The heart of the program are two cooperating algorithms - a simple and an advanced recognition algorithm. The first one uses strictly defined points, while the second one processes the image and in the following steps aims to find the cube and determine the centers of the tiles of a given wall. The further part, which is the same for both of them, uses the recognition processor which receives certain points on its input, which are implicitly the centers of the following tiles on the cube. The processor in the next steps collects color samples and tries to match them with previously defined patterns corresponding to individual fields. Its output consists of objects representing colors arranged in a strictly defined order adapted to the operation scheme used by the Cube Solver.

Application operation diagram

<img src=https://user-images.githubusercontent.com/101074920/158663407-6ae70641-c7aa-46d1-9e16-194ee0326751.png width="600"><br>

## **2. Simple recognition mode**

The simple recognition mode is based on reading colors from predefined points.

<img src=https://user-images.githubusercontent.com/101074920/158664854-a66b2e78-11dd-4668-ad48-3b9a9300b4a6.png width="500"><br>

## **3. Advanced recognition mode**

#### **3.1. Image preprocessing**

- Image download using the camera built into the device
- Convert to grayscale image
- Histogram alignment
- Noise removal
- Edge detection using Canny's algorithm

<img src=https://user-images.githubusercontent.com/101074920/158665456-c10e3730-b099-4405-a025-65dad25bb301.png width="500"><br>

- Edge thickening using morphological operations
- Finding lines using the Hough transform

<img src=https://user-images.githubusercontent.com/101074920/158665509-a120b827-8097-401b-9649-e8f73d56132a.png width="500"><br>

#### **3.2. Operations on detected edges to determine the centers of individual tiles on the cube**

- Extract information on individual lines
- Line segregation due to the angle of inclination (introduction to finding perpendicular lines)

<img src=https://user-images.githubusercontent.com/101074920/158675585-ca125012-e58b-46ce-bf64-ac2328d9f6dd.png width="500"><br>

- Finding the intersection of perpendicular lines and collecting them into groups

<img src=https://user-images.githubusercontent.com/101074920/158675623-b81d68a8-503f-4aaa-b8cf-25533e2c6a9a.png width="500"><br>

- Merge groups of points

<img src=https://user-images.githubusercontent.com/101074920/158675666-d94c40f4-a112-498a-a0d4-cac5fc659e3a.png width="500"><br>

- Removal of errors arising in the previous steps

<img src=https://user-images.githubusercontent.com/101074920/158675703-f8dc6007-4744-4717-8c83-85af2ec65a87.png width="500"><br>

- Draw two perpendicular lines from the points representing the corners of the tiles

<img src=https://user-images.githubusercontent.com/101074920/158675727-f74290a5-d339-4ccd-a36e-4abb8a118a65.png width="500"><br>

- Designating the remaining corners of the tiles

<img src=https://user-images.githubusercontent.com/101074920/158675801-9d2f4703-c6ea-4269-a655-85d43f85b8ca.png width="500"><br>

- Designating the tile centers

<img src=https://user-images.githubusercontent.com/101074920/158675883-0458341b-28a0-434d-9063-63d12c5f978c.png width="500"><br>

<img src=https://user-images.githubusercontent.com/101074920/158675829-d1fd99e6-fb6e-42a2-9eba-61e12d72b308.png width="500"><br>

## **4.  Displaying, accepting and sending information about the cube to the Cube Solver**

<img src=https://user-images.githubusercontent.com/101074920/158677421-1d59c671-d42c-4d38-8bab-923053db2198.png width="500"><br>

