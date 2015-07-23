Fault Tolerant Messaging Camel Application
==========================================

This is a very simple Camel application that will automatically discover the broker in Fuse by using MQ Gateway.
So no actuall physical IP and Port needs to be set beforehand. 

Setup and configuration
-----------------------

1. Download JBoss Fuse from jboss.org, and place the downloaded zip file under installs folder.

2. Add fabric server passwords for Maven Plugin to your ~/.m2/settings.xml file the fabric server's user and password so that the maven plugin can login to the fabric.

```
<settings>
..........
  <servers>
    <server>
      <id>fabric8.upload.repo</id>
      <username>admin</username>
      <password>admin</password>
    </server>
  </servers>
.......
<servers>
.......
</settings>
```


3. There are 2 ways to tackle this example, First is to everything manually, create a Master/Slave Broker, build the client Camel Application from scratch and then deploy them onto Fuse. Second way is to everything install and configured and just to play with it.

  a. Run `init.sh` for the simple installation. It will basically just install the Fuse and setup the fabric for you, with this setting, you will need to follow the instructions to provision the brokers, the instructions can be found in my blog and all the related code here. http://wei-meilin.blogspot.tw/2015/07/jboss-fusea-mq-achieve-fault-tolerant.html

  b. Run `install-all.sh` for the full installation. This shell will install everything for you. Including setting up the broker, creating a container, and then deploy the camel application on to Fuse container. 

4. Although our shell script has already started the FUSE server, if you need to manually start the server in the future, just run `./target/jboss-fuse-6.2.0.redhat-133/bin/start`

5. Log into the admin by going to http://localhost:8181 with username and password of admin:admin

6. Before you start the demo scenario, make sure all the containers BUT "testcon" is running.  You can check by going to "Containers -> Group by Containers" and all of them except testcon should be GREEN.

7. When your ready to start the demo scenario, start the "testcon".  This will send out messages to the mqgateway and in turn, to mqcon1 and mqcon2.  You can check out if the messages have been processed by going to each individual container and looking at the logs/dashboard for messages processed.

8. To stop the JBoss FUSE Server, run `./target/jboss-fuse-6.2.0.redhat-133/bin/stop`
