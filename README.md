## Intro
This is the general Readme Instructionse of Zeyu Pang's Semester Project at CHILI EPFL. By following the steps one by one, you can definitely replicate what I have done during this Semester.
We will divide the guidance into 3 parts as following. Now Let's get started!

## Part 1: Code Download & ROS workspace creation
The other 5 repositories of this Github account are the 5 ROS Modules in our ROS catkin_ws, which are included in cat_kin/src. But for students at CHILI, please DO NOT create a new catkin_ws on your own, as the catkin_ws should contain much more than these 5 modules, such as LLM model weights, etc. These 5 Modules are the core contents, so we publish them online for ease of reference.
To get start, please copy our original workspace _catkin_ws_PANG/_, and make adjustments based on it, by following the next steps.
1--copy the catkin_ws_PANG to a new location, rename the new workspace folder as you like
2--nevigate to your_ws/devel/lib/, find the _AVSR_pkgs/_, make a backup of it.
3--delete 3 things in your_ws: build/, devel/, src/CMakeLists.txt
4--catkin_make your_ws again
5--copy the _AVSR_pkgs/_ backup to _your_ws/devel/lib/_

Congrats! Now you finish the first part!

## Part 2: System Setup
Now we will do some preparations before running our ROS distributed sytem. Before this section, please make sure that you have finished Part 1 on BOTH PCs that you are going to use.
Then we will do some environmental setup in the _~/.bashrc_ file of these 2 PCs. This can be further divided into 2 subsections
### Pyhton Libraries 
On BOTH of 2 PCs, Please add these lines in the _.bashrc_ file, to configure environmental variables related to Python Libraries.

> export PYTHONPATH=path_to_your_ws/devel/lib/AVSR_pkgs:$PYTHONPATH   
> export PYTHONPATH=$PYTHONPATH:path_to_your_ws/VSR
> export PYTHONPATH=$PYTHONPATH:path_to_your_ws/FastChat


Pyaudio independencies
