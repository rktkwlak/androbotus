This page provides short instruction on how to deploy androbotus

# Introduction #
Androbotus consist of 3 main modules:

  * robot-client
  * robot-server
  * robot-mq

Robot client is an android application which defines the structure of the robot and it's core logic

Robot server is a robot's backend. It is a web app that allow to run heavy calculations, accept user commands and log telemetry of the robot

Robot MQ contains the core components of the androbotus messaging. This code is to be running both on server and client so it can not contain any platform dependencies...

# Deploying #

In order to deploy server part you will need to use Maven and have a tomcat7 up and running. Deploying client is as easy as deploying any Android application.

## robot-server ##
  1. Go to the root directory of **robot-mq** and run _mvn clean install_
  1. Now go to the root directory of **robot-server** and run _mvn tomcat:deploy_ (or _tomcat:redeploy_ if you already have it deployed). Note that tomcat plugin requires tomcat users to be properly set. To configure it go to _tomcat-users.xml_ in the tomcat's _conf_ folder. Below is an example of how this configuration may look like:
```
<tomcat-users>
    <role rolename="tomcat"/>
    <role rolename="manager"/>
    <role rolename="manager-script"/>
    <role rolename="manager-gui"/>
    <role rolename="standard"/>
    <role rolename="admin"/>
    <user username="admin" password="admin" roles="tomcat,manager,manager-script,manager-gui,admin"/>
</tomcat-users>
```

If you want to use a different user, then you'll need to change it in the pom file (by default it is _admin_ with password _admin_)

## robot-client ##
Since robot client is an Android app the best way to configure it is using Eclipse Android plugin.

  1. The client uses Android IOIO API to connect to external hardware. So you will need to download IOIOLib (https://github.com/ytai/ioio/wiki/IOIOLib-Core-API)
  1. Now when you have the IOIOLib import it as an Android Eclipse project
  1. You also need to add **robot-mq** dependency. Go to client project and right click on **lib** folder. Import the jar file from the file system

After that you can deploy **robot-client** to your Android phone (http://developer.android.com/training/basics/firstapp/running-app.html).