# Jetson Xavier NX

### For Fan
sudo echo 255 > /sys/devices/pwm-fan/target_pwm 

### For Fan Start on Every Boot
    sudo crontab -e
    Add @reboot sh /home/xavier/fan_on.sh

### For CUDA-11.0
    wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/sbsa/cuda-ubuntu1804.pin
    sudo mv cuda-ubuntu1804.pin /etc/apt/preferences.d/cuda-repository-pin-600
    wget http://developer.download.nvidia.com/compute/cuda/11.0.2/local_installers/cuda-repo-ubuntu1804-11-0-local_11.0.2-450.51.05-1_arm64.deb
    sudo apt-key add /var/cuda-repo-ubuntu1804-11-0-local/7fa2af80.pub
    sudo apt-key add /var/cuda-repo-ubuntu1804-11-0-local/7fa2af80.pub
    sudo apt-get update
    sudo apt-get -y install cuda
### For Dpkg Errors
`sudo apt-get -o Dpkg::Options::="--force-overwrite" install --fix-broken`
### For GStreamer SUpport
        sudo apt-get update
        sudo apt-get install gstreamer1.0-tools gstreamer1.0-alsa gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav
        sudo apt-get install libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev libgstreamer-plugins-good1.0-dev libgstreamer-plugins-bad1.0-dev
### Compiling Opencv
        cmake -D CMAKE_BUILD_TYPE=RELEASE \
        -D CMAKE_INSTALL_PREFIX=/usr/local \
        -D OPENCV_GENERATE_PKGCONFIG=ON \
        -D BUILD_EXAMPLES=OFF \
        -D INSTALL_PYTHON_EXAMPLES=ON \
        -D INSTALL_C_EXAMPLES=ON \
        -D BUILD_opencv_python3=ON \
        -D WITH_GSTREAMER=ON \
        -D WITH_CUDA=ON \
        -D WITH_CUDNN=ON \
        -D CUDA_ARCH_BIN=7.2 \
        -D PYTHON_DEFAULT_EXECUTABLE=$(which python3) \
        -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules/ \
        -D PYTHON3_EXECUTABLE=$(which python3) \
        -D PYTHON3_INCLUDE_DIR=$(python3 -c "from distutils.sysconfig import get_python_inc; print(get_python_inc())") \
        -D PYTHON3_PACKAGES_PATH=$(python3 -c "from distutils.sysconfig import get_python_lib; print(get_python_lib())") \
         ..
