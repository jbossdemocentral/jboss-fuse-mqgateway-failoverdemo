Fault Tolerant Messaging Camel Application
==========================================

This is a very simple Camel application that will automatically discover the broker in Fuse by using MQ Gateway.
So no actuall physical IP and Port needs to be set beforehand. 

Setup and configuration
-----------------------

Download JBoss Fuse from jboss.org, and place the downloaded zip file under installs folder.

Add fabric server passwords for Maven Plugin to your ~/.m2/settings.xml file the fabric server's user and password so that the maven plugin can login to the fabric.

```
<server>
  <id>fabric8.upload.repo</id>
  <username>admin</username>
  <password>admin</password>
</server>
```


There are 2 ways to tackle this example, First is to everything manually, create a Master/Slave Broker, build the client Camel Application from scratch and then deploy them onto Fuse. Second way is to everything install and configured and just to play with it.

You will find 2 shell scripts. 

This is an simple installation, it basically just install the Fuse and setup the fabric for you, with this setting, you will need to follow the instructions to provision the brokers, the instructions can be found in my blog and all the related code here. 
`init.sh`



This shell will install everything for you. Including setting up the broker, creating a container, and then deploy the camel application on to Fuse container. 
`install-all.sh`  


