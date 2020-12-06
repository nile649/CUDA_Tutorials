```
# http://techawarey.com/programming/install-opencv-c-c-in-ubuntu-18-04-lts-step-by-step-guide/

#Step 1. Update the Ubuntu System Package
sudo apt-get update && sudo apt-get upgrade

#Step 2. Install Required tools and packages
sudo apt-get install build-essential cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev
sudo apt-get install python3.5-dev python3-numpy libtbb2 libtbb-dev
sudo apt-get install libjpeg-dev libpng-dev libtiff5-dev libjasper-dev libdc1394-22-dev libeigen3-dev libtheora-dev libvorbis-dev libxvidcore-dev libx264-dev sphinx-common libtbb-dev yasm libfaac-dev libopencore-amrnb-dev libopencore-amrwb-dev libopenexr-dev libgstreamer-plugins-base1.0-dev libavutil-dev libavfilter-dev libavresample-dev

#Step 3. Download OpenCV Sources using git
sudo -s
cd /opt
git clone https://github.com/Itseez/opencv.git
git clone https://github.com/Itseez/opencv_contrib.git

#Step 4. Build & Install OpenCV
cd opencv
mkdir release
cd release
cmake -D BUILD_TIFF=ON -D WITH_CUDA=OFF -D ENABLE_AVX=OFF -D WITH_OPENGL=OFF -D WITH_OPENCL=OFF -D WITH_IPP=OFF -D WITH_TBB=ON -D BUILD_TBB=ON -D WITH_EIGEN=OFF -D WITH_V4L=OFF -D WITH_VTK=OFF -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D OPENCV_GENERATE_PKGCONFIG=ON -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=/opt/opencv_contrib/modules /opt/opencv/
make -j4
make install
ldconfig
exit
cd ~

#Step 5. Check OpenCV version installed

sudo apt-file search opencv.pc
export PKG_CONFIG_PATH=/usr/lib/x86_64-linux-gnu/pkgconfig/
pkg-config --modversion opencv

#Step 6. Compile & Run a Test Program 
mkdir opencv_test
cd opencv_test
gedit test.cpp 

#Copy & Paste the code psoted in Step 6
g++ test.cpp -o testoutput -std=c++11 `pkg-config --cflags --libs opencv`
./testoutput
```
