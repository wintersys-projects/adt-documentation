You will need root access to your autoscaler(s), webserver(s) and database machine.

To do this, on your build machine, go into the "helperscripts" directory of your ADT and use the "ConnectToXXXX" scripts to connect to your servers as required.
Once you are on your server issue the following commands (because you must have the private key to access the servers the servers trust you) and so,

>     cd ${HOME}/super   
>     /bin/sh Super.sh 

This will make you root on that machine and its full steam ahead from there
