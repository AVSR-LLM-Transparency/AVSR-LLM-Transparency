# Intro
This is the general Readme Instructions of Zeyu Pang's Semester Project at CHILI EPFL. By following the steps one by one, you can definitely replicate what I have done during this Semester.      
We will divide the guidance into 3 parts as following. Now Let's get started!

# Part 1: Code Download & ROS workspace creation
The other 5 repositories of this Github account are the 5 ROS Modules in our ROS catkin_ws, which are included in cat_kin/src. But for students at CHILI, please DO NOT create a new catkin_ws on your own, as the catkin_ws contains much more than these 5 modules, such as LLM model weights, etc. These 5 Modules are the core contents, so we publish them online for ease of reference.        
To get start, please copy our original workspace _catkin_ws_PANG/_, and make adjustments based on it, by following the next steps.      

1--copy the catkin_ws_PANG to a new location, rename the new workspace folder as you like    
2--nevigate to your_ws/devel/lib/, find the _AVSR_pkgs/_, make a backup of it.     
3--delete 3 things in your_ws: build/, devel/, src/CMakeLists.txt     
4--catkin_make your_ws again     
5--copy the _AVSR_pkgs/_ backup to _your_ws/devel/lib/_      

Congrats! Now you finish the first part!

# Part 2: System Setup
Now we will do some preparations before running our ROS distributed sytem. Before this section, please make sure that you have finished Part 1 on BOTH PCs that you are going to use.        
Then we will do some environmental setup in the _~/.bashrc_ file of these 2 PCs. This can be further divided into 2 subsections.
## Pyhton Libraries 
On BOTH of 2 PCs, Please add these lines in the _.bashrc_ file, to configure environmental variables related to Python Libraries.

`export PYTHONPATH=path_to_your_ws/devel/lib/AVSR_pkgs:$PYTHONPATH`     
`export PYTHONPATH=$PYTHONPATH:path_to_your_ws/VSR`       
`export PYTHONPATH=$PYTHONPATH:path_to_your_ws/FastChat`      

## ROS Communication setup
Now we will configure some settings to guarantee the communication between 2 PCs. The very first step is to plug in the Ethernet cable for BOTH 2 PCs, to make them connect to the same LAN.         
Then, run _ifconfig_ to check the IPs of the 2 PCs. After these steps, please again, open your _.bashrc_ file and add these new lines in it.

**On PC2, the Server PC :**     
`export ROS_IP=PC2_IP`             
`export ROS_MASTER_URI=http://PC2_IP:11311`                
`source path_to_your_ws/devel/setup.bash`               

**On PC1, the Robot PC :**     
`export ROS_IP=PC1_IP`          
`export ROS_MASTER_URI=http://PC2_IP:11311`         
`source path_to_your_ws/devel/setup.bash`            

Congrats! Now your ROS system is working！

# Part 3： Run the whole system 
Before we could run the code, the final step is to change some path variables within our codes.       
To be more specific, please config the path variables in _VSR_ , in _State_Manager/launch/config.yaml_ and in _live_experiment.py_     

Then, finally you are here! Now you are ready to run the whole system. Please! In order! Run these commands seperately on 2 PCs.(cd to your_ws at first)         

**On PC2, the Server PC :**      
`roslaunch state_manager launchfile.launch `        
`cd VSR`    
`rosrun video_module video.py`

**On PC1, the Robot PC :**         
`rosrun visual_module visual_module.py`            
`rosrun audio_module audio_module.py `       
`rosrun live_experiment live_experiment.py`     

Now!!! You can have fun talking to your system!!!    


# Appendix
P.S.          
There are some errors you may run into, please don't panic.             
1. Pyaudio independencies not installed: please google the steps to install the independencies, and install pyaudio again. (It's super easy, I promise u)               
2. Ethernet IP error: Our Ethernet IPs at EPFL are not fixed, so everytime you wanna run the code, please run _ifconfig_ to check the IPs first.


Here is where I am gonna leave you.    
Good Luck!!!   
