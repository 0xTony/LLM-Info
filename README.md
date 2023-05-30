# LLM-Info

Collection of infomation for those trying to learn how to run LLM models locally. 
If you are starting out, and want to run your own LLM on your CPU, I would suggest trying the Serge project at https://github.com/nsarrazin/serge

Note: This guide assumes an understaning of Windows, Linux and Docker. It tries to give some pointers but it not a complete step by step.

# Memory Requirements
This section will list the approximate memory requirements for various sized models. 

(To Do)

# Instal WSL2 For Windows 10 and 11
Install WSL for Windows using the default Ubuntu OS: https://www.windowscentral.com/how-install-wsl2-windows-10
* To start a WSL instance, from the task bar search run 'wsl'.
* To stop a running WSL 'wsl --shutdown'. https://learn.microsoft.com/en-us/windows/wsl/basic-commands

# Install Docker in the WSL instance.
Hopefully you are a bit familair with Ubuntu. Start Ubuntu and from the prompy, run: 
* 'sudo apt-get update'
* 'sudo apt-get upgrade'
* 'sudo apt-get install docker.io'

Docker should be installed and the instructions at serge should now work. https://github.com/nsarrazin/serge

# Increase WSL2 Available Memory for LLM Performance
LLM need ram, lots of ram which is why running larger models on a CPU is interesting.
By default, the WSL2 Linux instance will only use half of the available RAM. If the Linux WSL2 instance is running models that need more than half of the available RAM, it will start to swap to disk and performance will degrade drastically.

Therefore, if you have 16GB of RAM, the WSL2 instance will only use 8GB. If the model you are using needs 10GB (like a 13B model), performance will be very slow because it will start swapping to disk.

## What is Swap Space
When a computer starts to run out of RAM, it will start to write some of the lesser-needed sections to the hard drive/ssd. This can allow the system to temporarily remove unneeded sections of memory (like idle programs) and free it for other processes/programs. The problem is, writing and reading to disk/ssd is very slow compared to keeping everything in memory. For LLMs, this is something that we want to avoid.

## How Can I Tell If My Model is Using Swap
Open Task Manager, go to the Performance tab and with the model running, ask a question. If the disk percentage spikes while the model is answering a question and then drops to nearly zero when it is done, the system is using swap. If one of the disks is spiking while the LLM is thinking or writing, then you are using swap as there is not enough memory available for the LLM.
https://www.howtogeek.com/405806/windows-task-manager-the-complete-guide/

## How do I Increase the Avaiable Memory to the WSL2 Linux Instance
If you have 16, 32, or more gigabytes of memory, you may want to increase the available RAM to your WSL2 Linux instance so that it can run larger LLMs more efficiently.
Create a .wslconfig file in your %UserProfile% directory. The file needs to have a . before the wslconfig name. 
Tips: To find the location where the .wslconfig file needs to be created
* In PowerShell, use cd ~ to access your home directory. 
* You can also open Windows File Explorer and enter %UserProfile% in the address bar or go to C:\Users\<YourUserName>\ and create the file there. 
  * Steps to create a text file. https://answers.microsoft.com/en-us/windows/forum/all/how-to-create-a-new-text-file-using-file-explore/118e12c3-8969-440e-b12c-0e0234db24eb
  * How to rename a file in Windows File Explore. https://answers.microsoft.com/en-us/windows/forum/all/how-to-create-a-new-text-file-using-file-explore/118e12c3-8969-440e-b12c-0e0234db24eb

While there are many configuration changes available, for now, just change the memory configuration. In the .wslcponfig file, add the following:
memory=xGB
Where x is the number of gigs you want to provide to WSL2. My recommendations is if you have:
* 16gigs, try 12 or 13 (memory=12GB) 
* 32 gigs, try 28 or 29 (memory=28GB)
* 64, try 59 or 60 (memory=60GB)

You still need to leave some free RAM for Windows, or Windows will start swapping everything and performance will degrade.
Here are some additional tips:
* You will need to restart your WSL Linux instance for the changes to take effect.
* By default, the WSL2 Linux instance has access to all virtual CPUs. Unless you want to limit the number of available CPUs, there is no need to change this setting.

More information on WSL2 configuration can be found here: <https://learn.microsoft.com/en-us/windows/wsl/wsl-config>









