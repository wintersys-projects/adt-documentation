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
3. The public IP address of your laptop. 
4. The Usename of your linode.com account and the email address of your linode.com account
5. A temporary (delete it after you have finished running the demos, Personal Access Token with full access rights for Linode
6. Object Storage Access keys (access and secret) with full access rights to the gb-lon region
7. A domain name with a registrar of your choice using the linode nameservers (www.nuocial.uk) for example. You can use [primary or secondary domains](https://techdocs.akamai.com/cloud-computing/docs/create-a-domain)
8. A VPC in the gb-lon region called adt-vpc

Once you have collated all this information your **~/adt-credentials.txt** the complete file you will need to perform a build should look similar to:

LAPTOP PUBLIC KEY: ssh-ed25519 AAAAC3NzaC1lZD.......zGBarK5v+b6NNg4Yxqk16iJ1qsYb8N adt-laptop  

LINUX USERE: **agile-deployer**  (your free choice)  
LINUX USER PASSWORD: **XXXXXXXXXXXX** (your free choice make sure its strong)  
SSH PORT: **1035** (your free choice)  
PUBLIC IP ADDRESS OF LAPTOP: **143:34:41.21**  
S3 ACCESS KEY:  **XHGBD8edjDBJjBDU2** (generated from linode gui for the gb-lon region with full access)  
S3 SECRET KEY:  **jkdjnvunrvvoiinrvovinoi30ejfoinrviunjqkljwnfef** (generated from linoe gui for the gb-lon region with full access)  
LINODE PAT : **difhinrgfgi84f9j4f9j302rrijfubnervggihjjregvine4ifnji34nfin4fine4fi2** (generated from linode gui with full access rights)  
LINODE USERNAME (Cloudhost account ID) : **mylinodeusername** (your free choice)  
DNS USERNAME (Cloudhost account email address) : **myemailaddress@gmail.com** (your free choice)  
DNS SECURITY KEY (same as the full access PAT above) : **difhinrgfgi84f9j4f9j302rrijfubnervggihjjregvine4ifnji34nfin4fine4fi2**  
WEBSITE NAME (core of the website url below) : **nuocial**  (if website url = www.nuocial.uk this is "nuocial" if its www.tester.uk this is "tester"  
WEBSITE URL (the domain name you have registered with your registrar) : **adtdemo.nuocial.uk**  


