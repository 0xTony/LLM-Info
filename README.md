# LLM-Info

Collection of infomation for those trying to learn how to run LLM models locally. 

# Memory Requirements


# WSL2 - Increase Memory to Speed LLM Performance
Be default, the WSL2 Linux instance will only use half of the available ram. The Linux WSL2 instance running models that need more that half of the available ram will start to swap to disk and performance will degrade drastically. 

Thus, if you have 16 gigs, the WSL linux intance will only use 8 gigs and if the model you are using needs 10 gigs (like a 13b), performance will be very slow as it will start swapping to disk. 

## What is Swap Space
When a computer sartts to run out of RAM, it will start to write some of the lesser needed sections to the hard drive/ssd. This can allow the system to temporarily remove unneeded sections of memory (like idle programs) and free it for other processes/programs. The problem is, writing and reading to disk/ssd is very slow compared to keeping everythign in memory. For LLM, it is something that we want to avoid. 

## How Can I Tell If My Model is Using Swap
Open Task Manager, go to the Performance tab and with the model running, when you ask a question, if the disk percentage spikes whle the model is answering a quetion and then drops to nearlt zero when it is done, the system is using swap. If one of the Disks is spiking while the LLM is thinking or writing, then you are using swap as there is not enough memory available for the LLM. 
https://www.howtogeek.com/405806/windows-task-manager-the-complete-guide/

## How do I Increase the Avaiable Memory to the WSL2 Linux Instance
If you have 16, 32gigs or more memory, you may want to increase the available ram to your WSL2 Linux instance so it cna run larger LLM more effecently. 
Create a .wslconfig file in your X location. The file needs to have a . before the wslconfig name. While there are many configurations changes available, the only one that I changed was the memory configurations. In the file, add the following:
memory=xGB
Where x is the number of gigs you want to provide to WSL2. My recommendations is if you have 16gigs, try 12 or 13 (memory=12GB). If you have 32 gigs, try 28 or 29 (memory=28GB). If you have 64, try 59 or 60 (memory=60GB). You still need to leave some free ram for windows or windows will start swapping everything and performance will degrade.
Note: you will need to restart you WSL Linux instance.
More information on WSL2 configuration can be found here: https://learn.microsoft.com/en-us/windows/wsl/wsl-config

Note: By default, the WSL2 Linux instance has access to all virtual CPUs; unless you want to limit the number of available CPUs, there is no need to play with this setting. 







