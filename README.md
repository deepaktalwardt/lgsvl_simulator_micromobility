# LGSVL Automotive Simulator - Micromobility version
Modified version of LGSVL Automotive Simulator with added models of micromobility vehicles such as electric scooters, skateboards, hoverboards, segways and one-wheels. 

This project was originally forked from [lgsvl/simulator](https://github.com/lgsvl/simulator) and is based on their April 2019 release.

## Download
### To open simulator in Unity Editor
Due to size limitations of Git LFS, entire Unity project could not be hosted on GitHub. **It is instead uploaded to Dropbox and can be downloaded [here](https://www.dropbox.com/sh/wikrmv8u0vke4q5/AACPimgZrVvaqfOuVaycP5nXa?dl=0).**

### Release binaries
Releases are only available for Linux. You can build your own windows or linux binaries using the instructions below.
#### Linux
1. **With Autoware Ego-car and many micromobility vehicles**: Supports rendering of object detections directly from Autoware. [Download](https://www.dropbox.com/sh/dku35yl7mhflmad/AAC7_f9wZRx-ELVIMD7I0s0La?dl=0)
2. **With Apollo Ego-car and manually controlled e-scooter**: Only contains a single scooter that can be manually controlled using IJKL keys on the keyboard. [Download](https://www.dropbox.com/sh/gyxhgcqgmd4jmqm/AABXR6ysNd1ZiCp9RE7wtZyDa?dl=0)
3. **With Apollo Ego-car and many micromobility vehicles**: Perfect for data collection. [Download](https://www.dropbox.com/sh/zfe5hda944anzuz/AACDk17giYY0DVtrx-zzjiOca?dl=0)

#### To build your own binaries
Please note that the first build can take upwards of 45 minutes to build. Subsequent builds will be much faster.
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

## Contributors
* **Deepak Talwar** - (https://github.com/deepaktalwardt)
* **Seung Won Lee** - (https://github.com/swdev1202)
### This repository was originally developed for CMPE 297 - Autonomous Driving course at San Jose State University in Spring 2019.
