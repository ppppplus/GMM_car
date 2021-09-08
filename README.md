# GMM_car
ROS Package for Multi-Robot Mapping System via Gaussian Mixture Model
## Environment

- ImportError: No module named tf2_sensor_msgs

  ```shell
  ~$ sudo apt-get install ros-melodic-tf2-sensor-msgs
  ```

- ImportError: No module named autolab_core

  ```shell
  ~$ pip install autolab-core==0.0.14 --no-deps
  ~$ pip install ruamel.yaml==0.13
  ~$ sudo apt-get install gfortran
  ~$ pip install scipy==0.19.1
  ~$ pip install scikit-learn==0.19.1
  ~$ pip install colorlog==4.8.0
  ~$ pip install multiprocess, setproctitle, joblib
  ```

- ImportError: No module named builtins

  ```shell
  ~$ pip install future
  ```

- ImportError: No module named transforms3d/pygraph

  ```shell
  ~$ pip install ...
  ```

- ImportError: No module named pcl

  Refer to <https://python-pcl-fork.readthedocs.io/en/rc_patches4/install.html#install-python-pcl>

  Download from <https://cloud.tsinghua.edu.cn/d/9226140d250d45f4b8aa/>

- ImportError: No module named gtsam

  Download from <https://cloud.tsinghua.edu.cn/d/9226140d250d45f4b8aa/>

  ```shell
  ~$ mkdir build
  ~$ cd build
  ~$ cmake .. -DGTSAM_INSTALL_CYTHON_TOOLBOX=on
  ~$ make check
  ~$ make install
  ~$ cd cython
  ~$ sudo python setup.py install
  ```

- Launch 

  Edit path in /home/rosubuntu/catkin_ws/src/gmm_map_python-gmm_ral/script/MapBuilderNode.py: 449

  ```shell
  ~$ roslaunch gmm_map_python visualgmm_realsence_2robot.launch
  ```

## Clock synchronization

Refer to: <https://blog.csdn.net/scx837685002/article/details/80316280>

## Cartographer Install

Refer to <https://blog.csdn.net/zhzwang/article/details/108391029> and <>

- ```shell
  /opt/ros/melodic/include/cartographer/common/lua.h:20:10: fatal error: lua.hpp: No such file or directory
   #include <lua.hpp>
  ```

- cmake 指定路径：

  ```shell
  cmake -DCMAKE_INSTALL_PREFIX=/opt/abseil-cpp/install ..
  ```

- 安装 abseil-cpp 后编译 cartographer_ros 报错：

  ```shell
  /usr/bin/ld: /opt/abseil-cpp/install/lib/libabsl_base.a(sysinfo.cc.o): relocation R_X86_64_TPOFF32 against `_ZGVZN4absl13base_internal12GetCachedTIDEvE9thread_id' can not be used when making a shared object; recompile with -fPIC
  ```

  在abseil-cpp 的 CMakeLists.txt 中添加:

  ```cmake
  set(CMAKE_BUILD_TYPE "Release")SET(CMAKE_CXX_FLAGS "-std=c++11 -O3")set(CMAKE_CXX_FLAGS_RELEASE "-O3 -fPIC")
  ```

  再重新编译和安装 abseil-cpp

  
