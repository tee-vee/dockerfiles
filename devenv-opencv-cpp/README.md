# OpenCV development environment

## Features

* [GCC](https://gcc.gnu.org/)
* [OpenCV](http://opencv.org) 3.1.0
* [CMake](http://cmake.org)
* [Vim](http://vim.org)

## Build
```
$ docker build -t willprice/devenv-opencv .
```

## Usage
```
$ docker run --env=DISPLAY \
             --volume="$PWD:/work" \
             --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
         willprice/devenv-opencv
         bash
# In another terminal
$ export containerId="$(docker ps -l -q)"
# Expose xserver to docker container
$ xhost "+local:$(docker inspect --format='{{ .Config.Hostname }}' $containerId)"
```
Your current working directory will be mounted as `/work`, so all files
saved there in the container will appear locally on the host too.

There is an example CMakeLists.txt file in the repository to get you
started using CMake to build an OpenCV project.

## Further information
* [Using GUI's with Docker
  (ROS.org)](http://wiki.ros.org/docker/Tutorials/GUI)
* [OpenCV docs](http://docs.opencv.org/3.1.0/)
