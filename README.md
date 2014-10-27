Fault Tolerant Messaging Camel Application
==========================================

This is a very simple Camel application that will automatically discover the broker in Fuse by using fabric zookeeper registry.
So no actuall physical IP and Port needs to be set beforehand. 

Setup and configuration
-----------------------

Download JBoss Fuse from jboss.org, and place the downloaded zip file under installs folder.

Add fabric server passwords for Maven Plugin to your ~/.m2/settings.xml file the fabric server's user and password so that the maven plugin can login to the fabric.

<server>
  <id>fabric8.upload.repo</id>
  <username>admin</username>
  <password>admin</password>
</server>


There are 2 ways to tackle this example, First is to everything manually, create a Master/Slave Broker, build the client Camel Application from scratch and then deploy them onto Fuse. Second way is to everything install and configured and just to play with it.

You will find 2 shell scripts

init.sh
This is an simple installation, it basically just install the Fuse and setup the fabric for you, with this setting, you will need to follow along the 2 videos or the instructions from last blog (Part1) and find all the related code here. 
Or you can got to project/failoverdemoand compile, install it onto Fuse. 

mvn fabric8:deploy


install-all.sh  
This shell will install everything for you. Including setting up the broker, creating a container, and then deploy the camel application on to Fuse container. 



