title: IndoorAntiTheif
date: 2015-07-12 08:32:43
tags: [Geek, Project]
categories: [Project]
---

-------------

##Description

-------------

*Key words:* **Node.js, HTTP, BeagleBone, Java, Localization, Serial Communication,SkyTmote, ContikiOS,  Wireless**

###Hardware

* SkyTmote
* BeagleBone
* PC Laptop

###Software

* C:

    > ContikiOS<br>
    SkyTmote

* Java:

    > Library: RXTXcomm, json-simple-1.1.1<br>
    Algorithm: Localization

* Node.js:

    > module: (package.json file)<br>
    server: tmote_server, pushnotif

* Angstrom Linux

    > BeagleBone

-----------------------

##Sensor & Access point

-----------------------

### Sensor

> * Broadcast **beacon like** packets with `sensorID` and `index` every 1 to 2 seconds with **hightest** transmit power

* Access point:
>  * Receive packets from sensor, and extract `sensorID` and `index` from them
>  * Comcat `bsID` and `RSSI` to extracted message and send it to BeagleBone(BaseStation) through **USB** with **UART** protocol

*key words:* ***SkyTmote, ContikiOS, UART***

--------------

##Base Station

--------------

### BeagleBone

> * Receive message from **USB** with **UART** protocol, and extract `sensorID` `bsID` `index` `RSSI`
> * warp all information into **JSON** packets, send them to tmote_server with **http** protocol

*key words:* ***BeagleBone, Angstrom Linux, Java, UART, HTTP, JSON***

###Serial program

>The program which receive data from **USB** with **UART** is in **JAVA**, so setup **JVM** and **Install** necessary library is import before run the excutable jar file

![BikeSafetyBS](/blog/photo/BikeSafetyBS.jpg)


####Setup

* How to install **Java** with **Angstrom/Debian Linux**

    * [Tutorial on BeagleBone.org](http://beagleboard.org/project/java/)

        >* Visit the [JDK download page](http://www.oracle.com/technetwork/java/javase/downloads/jdk7-downloads-1880260.html)
        >>* For Angstrom, download the `Linux ARM v6/v7 VFP Soft Float ABI` version.
        >>* For Debian, download the `Linux ARM v6/v7 Hard Float ABI` version.
        >* Copy `jdk-7u40-linux-arm-vfp-*.gz` to your BeagleBone Black
        >* Perform `tar xzf jdk-7u40-linux-arm-vfp-*.gz` to extract the JDK
        >* Perform `export PATH=$PATH:/home/root/jdk1.7.0_40/bin` to add the JDK to your path
        >* Perform `export JAVA_HOME=/home/root/jdk1.7.0_40` to set the JAVA_HOME on your installation
        >* Perform `java -version` to verify your installation

* Install **rxtx** lib on Angstrom/Debian Linux(e.g: Angstrom)

    * Give BeagleBone Internet connection

    * Install **rxtx** lib

    >code:
    ```bash
    #for angstrom
    opkg update
    opkg install rxtx
    #for Debian
    apt-get update
    apt-get install rxtx
    ```

####Code

* The source code is a ***eclipse*** project.

* Export **Runable jar file** for BeagleBone

####Run

* [How to **run rxtx lib** related Java program on BeagleBone with Angstrom](https://www.youtube.com/watch?v=KQ4NtRAETp4&index=1&list=PLUju4b9wyvr2b8oQeAfoeMI1Bfclib6pc)

####Tutorial

* [Rxtx tutorial](file:///Users/chen/Dropbox/Project/Bike%20Safety/BS-BeagleBone/sky-Proj-32/TUTORIAL/RXTX/RXTX%20tutorial.html)

--------

##Server

--------

### tmote_server

*  handle requests from BeagleBone BaseStation, store all information in **specific file**

* run **localization** algorithm, which will periodically read **specific file**, when server **starts**

* pushnotif, once get **POST** request from DataBase Server, send **notification** to **APN**(apple push notificaiton server).

*key words:* ***Node.js, Localization, Notification, APN***
