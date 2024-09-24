# ERC Demo 2024

This package contains information on running the demo of the ERC INTERACT project done during RSS 2024 during the lab-tour. 

## Installation steps:
### On the robot:
*** DO NOT UPDATE SOFTWARE ON THE DINOVA WITHOUT APPROVAL FROM EVERYONE IN ERC INTERACT**

Check if the correct software versions are installed, higher versions might be okay, but these are the versions with which the demo is run at RSS 2024:

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
   or install all packages for a full workspace including all packages that are currently run on the robot (and you don't need on your laptop):
   ```bash
   chmod +x install_packages_complete.sh
   ./install_packages_complete.sh
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

Steps:
1. On your laptop: Ensure ssh into the robot without asking for a password:
   ```bash
   ssh-copy-id <user_on_robot>@<ip-robot> # example for dinova1: ssh-copy-id dinova@192.168.0.121 #for dingo 1
   ```
2. Create the tmuxp file. This command replaces the ip address with your ip address when connected to the lab-wifi (mrl-wifi-5g).
   ```bash
   cd config
   ./replace_ip <template_file> <output_file> #example: ./replace_ip erc_demo_template.yaml erc_demo_jjohnsen
   ```
3. Then run it 
   ```bash
   tmuxp load <output_file>
   ```

