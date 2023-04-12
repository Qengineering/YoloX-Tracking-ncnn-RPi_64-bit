# YoloX with Tracking

https://user-images.githubusercontent.com/44409029/177163299-4a73e807-605e-4fb1-ad79-b00e15786784.mp4

## YoloX with Byte Tracking for the ncnn framework. <br/>
The model tries to keep track of the individual objects found in the scenes. The example video follows the walkers as they stroll along. Obvious, not a simple task. Not only does the detection needs to be at a robust level. You also have to solve occlusion as the walkers pass each other.<br/>
Due to the excellent recognition, the best tracker in the set.<br/><br/>
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)<br/><br/>
Paper: https://arxiv.org/pdf/2110.06864v2.pdf<br/><br/>
Special made for a bare Raspberry Pi 4, see [Q-engineering deep learning examples](https://qengineering.eu/deep-learning-examples-on-raspberry-32-64-os.html)

------------

## Benchmark.
| Model  | size | objects | mAP | RPi 4 64-OS 1950 MHz |
| ------------- | :-----:  | :-----:  | :-----:  | :-------------: |
| [Tensorflow lite](https://github.com/Qengineering/TensorFlow_Lite-Tracking-RPi_64-bit) | 300x300 | 80 | 21.0  |  24.6 FPS |
| [NanoDet](https://github.com/Qengineering/NanoDet-Tracking-ncnn-RPi_64-bit) | 320x320 | 80 | 20.6  | 11.8 FPS |
| [YoloX](https://github.com/Qengineering/YoloX-Tracking-ncnn-RPi_64-bit) | 416x416 | 80 | 25.8 | **7.2 FPS** |

------------

## Dependencies.
To run the application, you have to:
- A raspberry Pi 4 with a 64-bit operating system. It can be the Raspberry 64-bit OS, or Ubuntu 18.04 / 20.04. [Install 64-bit OS](https://qengineering.eu/install-raspberry-64-os.html) <br/>
- The Tencent ncnn framework installed. [Install ncnn](https://qengineering.eu/install-ncnn-on-raspberry-pi-4.html) <br/>
- OpenCV 64 bit installed. [Install OpenCV 4.5](https://qengineering.eu/install-opencv-4.5-on-raspberry-64-os.html) <br/>
- Code::Blocks installed. (```$ sudo apt-get install codeblocks```)

------------

## Installing the app.
To extract and run the network in Code::Blocks <br/>
$ mkdir *MyDir* <br/>
$ cd *MyDir* <br/>
$ wget https://github.com/Qengineering/YoloX-Tracking-ncnn-RPi_64-bit/archive/refs/heads/main.zip <br/>
$ unzip -j master.zip <br/>
Remove master.zip, LICENSE and README.md as they are no longer needed. <br/> 
$ rm master.zip <br/>
$ rm LICENSE <br/>
$ rm README.md <br/> <br/>
Your *MyDir* folder must now look like this: <br/> 
```
├── include
│   ├── BYTETracker.h
│   ├── dataType.h
│   ├── kalmanFilter.h
│   ├── lapjv.h
│   └── STrack.h
├── palace.mp4
├── src
│   ├── BYTETracker.cpp
│   ├── kalmanFilter.cpp
│   ├── lapjv.cpp
│   ├── STrack.cpp
│   ├── utils.cpp
│   └── yoloX.cpp
├── tree.txt
├── Walkers.mp4
├── YoloX_Byte_Track.cbp
├── yoloxN.bin
└── yoloxN.param
```

------------

## Install Eigen.

Install eigen-3.3.9 [google](https://drive.google.com/file/d/1rqO74CYCNrmRAg8Rra0JP3yZtJ-rfket/view?usp=sharing) or [baidu(code:ueq4)](https://pan.baidu.com/s/15kEfCxpy-T7tz60msxxExg) (if not done earlier by Tensorflow Lite).

```
unzip eigen-3.3.9.zip
cd eigen-3.3.9
mkdir build
cd build
cmake ..
sudo make install
```

------------

## Running the app.
To run the application load the project file YoloX_Byte_Track.cbp in Code::Blocks. More info or<br/> 
if you want to connect a camera to the app, follow the instructions at [Hands-On](https://qengineering.eu/deep-learning-examples-on-raspberry-32-64-os.html#HandsOn).<br/><br/>
Many thanks to [nihui](https://github.com/nihui/) and [ifzhang](https://github.com/ifzhang) <br/><br/>

------------

## CMake.
Instead of Code::Blocks, you can also use CMake to build the application.<br>
Please follow the next instructions. Assuming your in the 'main' directory.<br>
```
.
├── bin
├── build
├── CMakeLists.txt
├── include
├── obj
├── palace.mp4
├── src
├── tree.txt
├── Walkers.mp4
├── YoloX_Byte_Track.cbp
├── YoloX_Byte_Track.depend
├── YoloX_Byte_Track.layout
├── yoloxN.bin
└── yoloxN.param
```
Create a build folder
```
$ mkdir build
$ cd build
```
Run CMake and Make
```
$ cmake ..
-- The C compiler identification is GNU 8.3.0
-- The CXX compiler identification is GNU 8.3.0
-- Check for working C compiler: /usr/bin/cc
-- Check for working C compiler: /usr/bin/cc -- works
-- Detecting C compiler ABI info
-- Detecting C compiler ABI info - done
-- Detecting C compile features
-- Detecting C compile features - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
-- Detecting CXX compiler ABI info
-- Detecting CXX compiler ABI info - done
-- Detecting CXX compile features
-- Detecting CXX compile features - done
-- Found OpenCV: /usr/local (found version "4.5.1") 
-- Configuring done
-- Generating done
-- Build files have been written to: /home/pi/software/YoloX ByteTrack/build
```
$  make  -j4
```
Scanning dependencies of target YoloX_Track
[ 28%] Building CXX object CMakeFiles/YoloX_Track.dir/src/BYTETracker.cpp.o
[ 28%] Building CXX object CMakeFiles/YoloX_Track.dir/src/STrack.cpp.o
[ 57%] Building CXX object CMakeFiles/YoloX_Track.dir/src/kalmanFilter.cpp.o
[ 57%] Building CXX object CMakeFiles/YoloX_Track.dir/src/lapjv.cpp.o
[ 71%] Building CXX object CMakeFiles/YoloX_Track.dir/src/utils.cpp.o
[ 85%] Building CXX object CMakeFiles/YoloX_Track.dir/src/yoloX.cpp.o
[100%] Linking CXX executable ../YoloX_Track
[100%] Built target YoloX_Track
```
$ cd ..<br>
$ tree -L 1
```
.
├── bin
├── build
├── CMakeLists.txt
├── include
├── obj
├── palace.mp4
├── src
├── tree.txt
├── Walkers.mp4
├── YoloX_Byte_Track.cbp
├── YoloX_Byte_Track.depend
├── YoloX_Byte_Track.layout
├── yoloxN.bin
├── yoloxN.param
└── YoloX_Track
```
Run
```
$ ./YoloX_Track
```
Once YoloX_Track works, you may remove the build directory, since we don't need it any more.
```
$ sudo rm -rf build
```

------------

[![paypal](https://qengineering.eu/images/TipJarSmall4.png)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=CPZTM5BB3FCYL) 

