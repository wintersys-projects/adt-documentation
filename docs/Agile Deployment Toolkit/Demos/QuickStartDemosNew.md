## QUICK-START DEMOS  

**NOTE:** These quick start demos are only intended for use on the Linode platform using the supplied [StackScript](https://cloud.linode.com/stackscripts/635271) to demonstrate example usage cases for the Agile Deployment Toolkit as quickly and easily as possible.  The demos themselves are very quickly put together simply there for illustrative purposes they are not there to provide any truly useful function. If anyone would like to spend time crafting demos useful for real function that could be listed here that would be valued. 

The purpose of these quick start demos is to show you that with just some parameters you can achieve a lot using the Agile Deployment Toolkit with the possibility of going much deeper into it if you choose to.

For more information about parameter configuration please see the [spec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/specification.md) and [quickspec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/quick_specification.dat)

**These initial steps are only required the first time you make a deployment. The result of these first steps can be used repeatedly for subsequent demo deployments.** 

--------------------------
<span style="color:red">**YOUR ONE TIME INITIAL PREPARATORY STEPS**</span>

--------------------------

Pre-requisites:

- A personal laptop with access to a linux shell
- A user account with sudo or administrative privileges
- Terminal or command line access

Step 1:

Go to the linux shell on your laptop. Create a text file in your home directory called "adt-credentials.txt"

>     /bin/echo "Agile Deployment Toolkit Quick Start Demos Essential Credentials" > ~/adt-credentials.txt

---------------------------------

Step 2:

1. You have an existing SSH Key-pair you want to use that is available from your linux terminal simply save a copy of your public key to your **~/adt-credentials.txt** from step 1 above for ease of reference later on

>     /bin/echo ${PUBLIC_KEY} >> ~/adt-credentials.txt

2. You do not have a SSH Keypair then its necessary to generate and configure them now.

[Setup SSH Keys For Your Personal Laptop](./SetupSSHKeysOnLaptop.md)

------------------------------------
