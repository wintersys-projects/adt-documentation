## QUICK-START DEMOS  

**NOTE:** These quick start demos are only intended for use on the Linode platform using the supplied [StackScript](https://cloud.linode.com/stackscripts/635271) to demonstrate example usage cases for the Agile Deployment Toolkit as quickly and easily as possible.  The demos themselves are very quickly put together simply there for illustrative purposes they are not there to provide any truly useful function. If anyone would like to spend time crafting demos useful for real function that could be listed here that would be valued. 

The purpose of these quick start demos is to show you that with just some parameters you can achieve a lot using the Agile Deployment Toolkit with the possibility of going much deeper into it if you choose to.

For more information about parameter configuration please see the [spec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/specification.md) and [quickspec](https://github.com/wintersys-projects/adt-build-machine-scripts/blob/main/templatedconfigurations/quick_specification.dat)

**These initial steps are only required the first time you make a deployment. The result of these first steps can be used repeatedly for subsequent demo deployments.** 

--------------------------
<span style="color:red">**YOUR ONE TIME INITIAL PREPARATORY STEPS**</span>

--------------------------

You need the the following credentials available to run the quick start demos. The advice is to collate the necessaries and store them in a file **~/adt-credentials.txt** for use once you are ready to deploy one of the demo scenarios. 

1. The public key from an SSH Key Pair from your the laptop you are using the ADT from
2. The public IP address of your laptop. 
3. The Usename of your linode.com account and the email address of your linode.com account
4. A temporary (delete it after you have finished running the demos, Personal Access Token with full access rights for Linode
5. Object Storage Access keys (access and secret) with full access rights to the gb-lon region
6. A domain name with a registrar of your choice using the linode nameservers (www.nuocial.uk) for example
7. A VPC in the gb-lon region called adt-vpc

Once you have collated all this information your **~/adt-credentials.txt** file should look like:



