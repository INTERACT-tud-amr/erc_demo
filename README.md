# ERC Demo 2024

This package contains information on running the demo of the ERC INTERACT project done during RSS 2024 during the lab-tour. 

## Installation steps:
### On the robot:
**DO NOT UPDATE SOFTWARE ON THE DINOVA ROBOT WITHOUT APPROVAL FROM EVERYONE IN ERC INTERACT.**

The following packages are required to be installed on the robot (under the dinova user): [dinova](https://github.com/INTERACT-tud-amr/dinova), [dinova_utils](https://github.com/INTERACT-tud-amr/dinova_utils), [dinova_motion](https://github.com/INTERACT-tud-amr/dinova_motion), [dinova_grasp](https://github.com/INTERACT-tud-amr/dinova_grasp).
The packages installed on the robot should be on the versions as mentioned in [install_packages/install_packages.sh](install_packages/install_packages.sh).

### On your own laptop:
1. Create a catkin workspace on your laptop in Ubuntu20, ([instructions](http://wiki.ros.org/catkin/Tutorials/create_a_workspace))
2. Go to the src folder and clone this repo
   ```bash
   cd src
   git clone git@github.com:INTERACT-tud-amr/erc_demo.git
   ```
3. Install the other packages required to run the demo on your laptop:
   ```bash
   cd erc_demo/install_packages
   chmod +x install_packages.sh
   ./install_packages.sh
   ```
4. Install the necessary dependencies for the packages included in install_packages, check their respective github for instructions. For the basic version (install_packages.sh), this requires:
   ```bash
   pip install unified-planning[engines,plot] #for dinova_task_planner
   sudo apt install ros-noetic-derived-object-msgs #for visualization_utils
   ```
5. Build the workspace:
   ```bash
   catkin build
   ```
   
## Steps to run the demo:
**Note**: Unfortunately, this tmuxp-file only works currently from Ubuntu20, NOT from a Docker. We are aware of the inconvenience and hope to resolve it soon. 

In [config/](config/), template files are shown of yaml files usable for tmuxp. This eases the process of starting several terminals, by generating all terminals by running 1 command (step 3). 
1. On your laptop: Ensure ssh into the robotS without asking for a password:
   ```bash
   ssh-copy-id <user_on_robot>@<ip-robot> # E.g. for dinova1: ssh-copy-id dinova@192.168.0.121, for dinova2: ssh-copy-id dinova@192.168.0.122
   ```
2. Install tmuxp and tmux:
   ```bash
   sudo apt install tmux
   pip install tmuxp
   ```
3. Create the tmuxp file. This command replaces the ip address with your ip address when connected to the lab-wifi (mrl-wifi-5g).
   ```bash
   cd config
   ./replace_ip <template_file> <output_file> #example: ./replace_ip erc_demo_template.yaml erc_demo_jjohnsen
   ```
4. Then run it 
   ```bash
   tmuxp load <output_file>
   ```
   To kill all terminals in tmux, write the following in one of the terminals:
   ```bash
   tmux kill-server
   ```
5. Open another TWO terminals in which to run the task planner (This is not included in the tmuxp-file yet, because it will start the robots to home). Before running the task planner, check that your joysticks are connected:
   ```bash
   source catkin_ws/devel/setup.zsh
   export ROS_MASTER_URI=http://localhost:11311
   export ROS_IP=<IPADDRESS>
   roslaunch dinova_task_planner basic_planner_d1.launch #AND IN THE SECOND TERMINAL: roslaunch dinova_task_planner basic_planner_d2.launch
   ```
