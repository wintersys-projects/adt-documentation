There are two different techniques that I use to synchronise filesystems. One is the lightweight method and the other is the heavyweight method. 

Lightweight

There are limitations to what the light weight method can do. It's based on filesystem events using inotifywait. The lightweight method is fine if you are adding, deleting and modifying individual files from the filesystem you are monitoring but if you dump a whole directory of files into the directory you are monitoring then the "burst" of events to inotifywait means that some events get lost and therefore not processed by inotifywait. So, the lightweight method can be used to synchronise configuration directories between machines (which will most likely only involve the creation, modification and deletion) of individual files at a time.

The basic operation of the lightweight method is

Set a directory to synchronise between machines
When there is a modification, creation or deletion event in the directory you are monitoring process the event

creation and modification events: Put the created/modified file to the datastore 
deletion: mark a file for deletion in the datastore

As part of the process, created and modified files from other machines written to the datastore will be synced to the local machine meaning that updates to one directory are distributed to all the machines

As another part of the process, any file that one machine has marked for deletion is deleted from the local machine meaning that a delete on one machine is reflected on the other machines in the active set of machines. 

So, to reiterate the lightweight method is definitely not suitable for synchronising webroot directories where an application developer might install an extension which writes tens of files to one of the webroots, some of which will be lost for sure because of the inotifywait limitation.

If you have the skills, this is very modular you can plug and play a different process than what I have developed for the lightweight method simply by refactoring the script: 

>     ${HOME}/providerscripts/datastore/filesystems-sync/lightweight/FileSystemSyncController.sh

on your machines.

Please note the lightweight way of synchronising directories needs a cron task added to all the machines that you want to be in the synchronising federation such as:

>    @reboot export HOME="${HOME}" && ${HOME}/providerscripts/datastore/config/ActivateConfigDatastoreLightweight.sh"

Heavyweight

The heavyweight method is recommended if you want to sync webroots between directories. Again this is very modular so if you want to plug in your own implementation you can. 
