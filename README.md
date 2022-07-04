# YoloX Byte Tracking

https://user-images.githubusercontent.com/44409029/177163299-4a73e807-605e-4fb1-ad79-b00e15786784.mp4

## YoloX with Byte Tracking for the ncnn framework. <br/>
The model tries to keep track of the individual objects found in the scenes. The example video follows the walkers as they stroll along. Obvious, not a simple task. Not only does the detection needs to be at a robust level. You also have to solve occlusion as the walkers pass each other.
[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)<br/><br/>
Paper: https://arxiv.org/pdf/2110.06864v2.pdf<br/><br/>
Special made for a bare Raspberry Pi 4, see [Q-engineering deep learning examples](https://qengineering.eu/deep-learning-examples-on-raspberry-32-64-os.html)

------------

## Benchmark.
| Model  | size | objects | mAP | RPi 4 64-OS 1950 MHz |
| ------------- | :-----:  | :-----:  | :-----:  | :-------------: |
| [Tensorflow lite](https://github.com/Qengineering/NanoDet-ncnn-Raspberry-Pi-4) | 300x300 | 80 | 21.0  |  24.6 FPS |
| [NanoDet](https://github.com/Qengineering/NanoDet-ncnn-Raspberry-Pi-4) | 320x320 | 80 | 20.6  | 11.8 FPS |
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
palace.mp4 <br/>
Walkers.mp4 <br/>
YoloX_Byte_Track.cpb <br/>
yoloxN.bin <br/>
yoloxN.param <br/>
**include** folder <br/>
**src** folder <br/> 

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

[![paypal](https://qengineering.eu/images/TipJarSmall4.png)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=CPZTM5BB3FCYL) 

