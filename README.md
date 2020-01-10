# Joomla Currency Converter

Plugin and module for doing currency conversion in Joomla

# Running Development Environment

This Joomla extension uses the [JoomlaTools Vagrant Box](https://www.joomlatools.com/developer/tools/vagrant/) for local development and testing.

This box uses NFS for its file synchronisation outside the box. Ensure that you 
have the required NFS tools installed before building the box. On Ubuntu, this 
is as simple as:

`sudo apt-get install nfs-kernel-server`

Once you have done this, you can run `vagrant up` to build the box. Because this 
box creates NFS records on the host, you should always run vagrant commands for this 
project from a terminal and not a GUI, so that you can provide passwords if needed.

## First Run

The JoomlaTools Vagrant box is an excellent tool, but being an Ubuntu 14.04 box it's 
also getting quite long in the tooth and starting to show cracks. Fortunately, a 
new release is on the way, but until it's available we have to work around a few
kinks when starting up the development environment. On first run, you 
will encounter issues with Virtualbox Guest Additions not being able to correctly 
install itself, because the box is missing the required kernel headers. As a
workaround for this, I recommend the following procedure for first run with this
box.

```
vagrant up  
vagrant ssh  
sudo apt-get update  
sudo apt-get dist-upgrade  
exit  
vagrant reload --provision
```
This set of commands will build the initial box as far as it can go before the guest
additions fail. At this point, you SSH into the box and run the latest `apt-get`
updates, which will fetch the latest kernel and its associated headers. Finally,
you exit the SSH session and reload the box, which Vagrant will then finish
provisioning. This should get you to a working JoomlaTools box. 

This procedure is only required on first run. In the long run, I intend to publish
a Docker-based alternative running the same toolset, but I don't have time right now.

## Accessing the Box

The JoomlaTools box uses fixed-IP private networking to expose its various domains. 
Once the Vagrant box has finished building, add the following line to your hosts 
file (on Linux this is usually at `/etc/hosts`):

`33.33.33.58 joomla.box webgrind.joomla.box phpmyadmin.joomla.box`

You should now be able to view the box's control panel at http://joomla.box