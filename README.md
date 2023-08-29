# LLM-Info

Collection of infomation for those trying to learn how to run LLM models locally. 
If you are starting out, and want to run your own LLM on your CPU, I would suggest trying the Serge project at https://github.com/nsarrazin/serge

Note: This guide assumes an understaning of Windows, Linux and Docker. It tries to give some pointers but it not a complete step by step.

# Memory Requirements
This section will list the approximate memory requirements for various sized models. 

(To Do)

# Install WSL2 For Windows 10 and 11
Install WSL for Windows using the default Ubuntu OS: https://www.windowscentral.com/how-install-wsl2-windows-10
* To start a WSL instance, from the task bar search run 'wsl'.
* To stop a running WSL 'wsl --shutdown'. https://learn.microsoft.com/en-us/windows/wsl/basic-commands

# Install Docker in the WSL instance.
Hopefully you are a bit familair with Ubuntu. Start Ubuntu and from the prompy, run: 
* 'sudo apt-get update'
* 'sudo apt-get upgrade'
* 'sudo apt-get install docker.io'

Docker should be installed and the instructions at serge should now work. https://github.com/nsarrazin/serge


