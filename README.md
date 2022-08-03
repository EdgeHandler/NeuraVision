# NeuraVision

## Setting up Jetson Nano

### Steps
1. [Download](https://developer.nvidia.com/embedded/l4t/r32_release_v7.1/jp_4.6.1_b110_sd_card/jeston_nano/jetson-nano-jp461-sd-card-image.zip) Jetson Nano Image file.
2. [Download](https://www.balena.io/etcher/) Balena Etcher.
3. Use balena etcher to flash SD card with the above downloaded Jetson Image.
4. After flashing connect it to the Jetson Nano.
5. Connect I/O devices and power it up.
6. Follow a simple straight forward configuration.
7. Get up till a safe first boot.
8. Connect to network.
9. `sudo apt-get update`
10. `sduo apt-get upgrade`. and `sudo apt dist-upgrade.`
11. [Download](https://developer.nvidia.com/cudnn-download-survey) CUDNN from here an Nvidia account is needed.
12. Open the terminal and move the file of CuDNN from Downloads directory to home directory.
13. For installing the file use [refer](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html).
14. From the terminal for exporting  cuda toolkit path :-

           nano /home/username/.bashrc

           # or

          sudo vi /home/$USER/.bashrc
          Inside there add the following: (replace cuda-8.0 with your version)

           export PATH="/usr/local/cuda-8.0/bin:$PATH"
           export LD_LIBRARY_PATH="/usr/local/cuda-8.0/lib64:$LD_LIBRARY_PATH"
          Then do the following to save and close the editor:

           On you keyboard press the following: 

           ctrl + o             --> save 
           enter or return key  --> accept changes
           ctrl + x             --> close editor
          Now either do source .bashrc or close and open another terminal

          Now run nvcc --version
          
### Compiling OpenCV from source for Jetson Nano only using RidgeRun's [Fork](https://developer.ridgerun.com/wiki/index.php/Compiling_OpenCV_from_Source)

## Tips on Compilation
Compilation happens in three steps 1.) Prebuild 2.) build 3.) Install. \
when compiling read the pre build report carefully. It tells about the state of all the selected flags during cmake build. Check in report if cuDNN, and cuda is read by cmake or not. If they are not detected. remove the build folder using the command ` sudo rm -rf build ` from inside the opencv directory and fix the relevant issue then build again.

Installing any software by compiling from source, is a one way process if we install it we won't be able to uninstall it. In such case reinstallation of OS is the only solution. So read and understand the pre-build report.
    
