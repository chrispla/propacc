### Project files

`demo` contains a short video demo

`report` contains a detailed report of the motivation and implementation for the system

`patches` contains the Pure Data patches used

`realtime` contains the C++ source for building the DDSP external

`models` contains pretrained violin and saxophone models



### Installation

To run **propacc**, we first need to build the IRCAM Acids DDSP module. To do this we need to have a modern C++ compiler and **CMake** in our system, as well as [**libtorch** C++](https://pytorch.org/get-started/locally/). 

In the project directory, do the following:

```shell
cd realtime
mkdir build
cd build
cmake ../ -DCMAKE_PREFIX_PATH=</path/to/libtorch> -DCMAKE_BUILD_TYPE=Release
make install
```

Now copy the created ```ddsp~.pd``` external from the ```build``` folder and put it in the appropriate Pd externals folder.



Now you should be ready to run ```propacc.pd``` from the patches folder. First, load the ```.ts``` models from the ```models``` folder, as well as their associated impulse response. Make sure the sampling rate of Pd is set to 48000Hz. And that should be all! Enable DDSP, raise the volume, and start singing/playing!



### 
