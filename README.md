# LGSVL Automotive Simulator - Micromobility version
Modified version of LGSVL Automotive Simulator with added models of micromobility vehicles such as electric scooters, skateboards, hoverboards, segways and one-wheels. 

This project was originally forked from [lgsvl/simulator](https://github.com/lgsvl/simulator) and is based on their April 2019 release.

## [Download](https://www.dropbox.com/sh/eyyehodzsu09v31/AACRm2BwvPeow7dk2mn93Zxia?dl=0)
### To open simulator in Unity Editor
Due to size limitations of Git LFS, entire Unity project could not be hosted on GitHub. **It is instead uploaded to Dropbox and can be downloaded [here](https://www.dropbox.com/sh/eyyehodzsu09v31/AACRm2BwvPeow7dk2mn93Zxia?dl=0).**

### Release binaries
Releases are only available for Linux. You can build your own windows or linux binaries using the instructions below. 
#### Linux
1. **With Autoware Ego-car and many micromobility vehicles**: Supports rendering of object detections directly from Autoware. [Download](https://www.dropbox.com/sh/dku35yl7mhflmad/AAC7_f9wZRx-ELVIMD7I0s0La?dl=0)
2. **With Apollo Ego-car and manually controlled e-scooter**: Only contains a single scooter that can be manually controlled using IJKL keys on the keyboard. [Download](https://www.dropbox.com/sh/gyxhgcqgmd4jmqm/AABXR6ysNd1ZiCp9RE7wtZyDa?dl=0)
3. **With Apollo Ego-car and many micromobility vehicles**: Perfect for data collection. [Download](https://www.dropbox.com/sh/zfe5hda944anzuz/AACDk17giYY0DVtrx-zzjiOca?dl=0)

#### To build your own binaries
Please note that the first build can take upwards of 45 minutes to build. Subsequent builds will be much faster. Please close the Unity Editor while building as build cannot be completed with the editor open. You can build for Linux from Windows if you installed Linux build target while installing Unity.
##### Windows
```
C:\path\to\Unity\Editor\Unity.exe -batchmode -nographics -silent-crashes -quit 
-buildDestination C:\output\folder\simulator.exe 
-buildTarget Win64 -executeMethod BuildScript.Build 
-projectPath C:\path\to\simulator\source\code 
-logFile log.txt
```
##### Linux
```
path/to/Editor/Unity -batchmode -nographics -silent-crashes -quit 
-buildTarget Linux64 -executeMethod BuildScript.Build 
-buildDestination /output/folder/simulator 
-projectPath /path/to/simulator/source/code 
-logFile log.txt
```
## Modifications to the simulator 
### Micromobility vehicles added
We added the following micromobility vehicles to the original simulator.
![](docs/images/all_vehicles_labeled.png)

### Process for adding micromobility vehicles
![](docs/images/process_adding_vehicles.jpg)
1. Solid modeling of the vehicle in a CAD software.
2. Solid model is then saved as a mesh in .STL format.
3. Import mesh into Blender and add materials to the model. Here the Origin is translated to Center of Gravity of the model and the axis are rotated to match defaults followed by Unity. Not doing this can lead to a lot of headache in manipulating the vehicle in Unity later.
4. This model is then saved in .FBX format and imported into a Unity test scene as a `GameObject`. The model is scaled to correct dimensions, if necessary.
5. Add `RigidBody` component to the model and add a realistic mass value. Humanoid used here is downloaded from the Unity Asset Store [here](https://assetstore.unity.com/packages/3d/characters/humanoids/rcp-caucaisan-character-models-81402#). Initially, the humanoid is configured in a T-orientation. Limbs and joints need to be manipulated to appropriate positions.
6. A `BoxCollider` is added to the `GameObject` and its boundaries are scaled to fit the entire model. It is then saved as a prefab and imported into the San Francisco Scene.

Please follow these steps if you would like to add your own vehicles.

### Modifications to ego-car
LGSVL simulator provides separate ego-cars configured with sensor suites to work with Apollo and Autoware self-driving stacks respectively. At this stage, the sensors on these ego-cars cannot "see" the new vehicles we added. More modifications need to be made in order for these vehicles to be perceived by ego-cars as NPCs (Non-playable characters).
#### Apollo ego-car
1. Adding Ground Truth Sensors for micromobility vehicles
2. Modifying Culling Masks
3. Modifications to Perception sensors
4. Modifications to `NeedsBridge` list
#### Autoware ego-car

### Manually controlling micromobility vehicles
Currently, only controlling e-scooters is supported. To enable controlling an e-scooter, select the `GameObject` and check its Script component. You will then be able to control it with IJKL keys.

## Projects with modified simulator

### Detection of Micromobility vehicles from camera images
#### YOLOv3 Repository trained on dataset collected from this simulator
#### ROS Packages

### Testing how Baidu Apollo works with modified simulator

### 3D Detection of Micromobility vehicles from LiDAR Pointclouds using YOLO3D (coming soon)

## Links
### Project report
### [Project presentation](https://docs.google.com/presentation/d/1NzCOh9w1M_gmNOr4F7BRGH3UlDinqTB6wfFwwc2YfJY/edit?usp=sharing)

## Acknowledgements
We would like to thank Martins Mozeiko and Brian Shin from LGSVL lab for supporting us and providing technical help throughout this project.


## Contributors
* **Deepak Talwar** - (https://github.com/deepaktalwardt)
* **Seung Won Lee** - (https://github.com/swdev1202)
### This repository was originally developed for CMPE 297 - Autonomous Driving course at San Jose State University in Spring 2019.
