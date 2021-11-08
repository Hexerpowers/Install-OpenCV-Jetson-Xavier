# Install-OpenCV-Jetson-Xavier (NX, AGX)
![output image]( https://qengineering.eu/images/LogoOpenJetsonGitHub.webp )

##*This is a fork of Install-OpenCV-Jetson-Nano from [Q-engineering](https://github.com/Qengineering/Install-OpenCV-Jetson-Nano)*

## OpenCV installation script for a Jetson Xavier

[![License](https://img.shields.io/badge/License-BSD%203--Clause-blue.svg)](https://opensource.org/licenses/BSD-3-Clause)<br/>

This is the full setup of OpenCV with CUDA and cuDNN support for the Jetson Xavier.<br/>
For reference information see [Q-engineering - Install OpenCV Jetson Nano](https://qengineering.eu/install-opencv-4.5-on-jetson-nano.html)

------------

# Before installation
* Build can take up to 5 hours, so be prepared to wait for a while.

* Check that you have CUDA and cuDNN installed:
    ```shell
    $ dpkg -l | grep cuda
    ```
* Check your total FREE memory (RAM + swap) first for a fast build. You need at least a total of:
    >OpenCV 4.5.4 -> 8.5 GB!<br/>
    OpenCV 4.5.3 -> 8.5 GB!<br/>
    OpenCV 4.5.2 -> 8.5 GB!<br/>
    OpenCV 4.5.1 -> 6.5 GB<br/>
    OpenCV 4.5.0 -> 6.5 GB<br/>

    If not, enlarge your swap space as explained in the guide, or only 1 core will be used for the compilation.

* Xavier has enough RAM to build in 8-core way, but for stability reasons, we will use only 4 CPU cores.<br/>
Change NO_JOB=8 if you are brave enough (highly NOT recomended).<br/>


# Installation
```shell
$ free -m

$ wget https://github.com/Hexerpowers/Install-OpenCV-Jetson-Xavier/raw/main/OpenCV-4-5-x.sh

$ sudo chmod 755 ./OpenCV-4-5-x.sh

$ ./OpenCV-4-5-x.sh
```
:point_right: Don't forget to reset your swap memory afterwards.

------------

If you want to beautify OpenCV with the Qt5 GUI you need to
- $ sudo apt-get install qt5-default
- Set the -D WITH_QT=**ON** \ (± line 62) in the script<br/>
 
before running the script on your Xavier

------------

OpenCV will be installed to the `/usr` directory, all files will be copied to following locations:<br/>

- `/usr/bin` - executable files<br/>
- `/usr/lib/aarch64-linux-gnu` - libraries (.so)<br/>
- `/usr/lib/aarch64-linux-gnu/cmake/opencv4` - cmake package<br/>
- `/usr/include/opencv4` - headers<br/>
- `/usr/share/opencv4` - other files (e.g. trained cascades in XML format)<br/>

