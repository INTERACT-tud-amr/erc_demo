# ERC Demo 2024

This package contains information on running the demo of the ERC INTERACT project done during RSS 2024 during the lab-tour. 

## Installation steps:
### On the robot:
*** DO NOT UPDATE SOFTWARE ON THE DINOVA WITHOUT APPROVAL FROM EVERYONE IN ERC INTERACT**
Check if the correct software versions are installed, higher versions might be okay, but these are the versions with which the demo is run at RSS 2024:

### On your own laptop:
1. Create a catkin workspace on your laptop in Ubuntu20, ([instructions](http://wiki.ros.org/catkin/Tutorials/create_a_workspace))

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

