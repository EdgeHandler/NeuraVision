# Additional Support during the compilation  


## To install tar.xz

tar -xvf filename.tar.xz

## To export paths of cuda toolkit for nvcc

From the terminal:

 nano /home/username/.bashrc

 or

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

## Installing CuDNN is required for DNN application for CuDNN

Go to Nvidia CuDNN library...
