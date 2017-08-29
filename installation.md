# Installation

## Requirements
The software requirement for DataFibers are
* Java 8
* Apache Kafka >= 0.11.0
* Apache Flink >= 1.3.0
* MongoDB

The Java runtime version is at least version 1.8. Java installation varies by platform, so please check the JRE installation version for your platform before installing the DataFibers using following command: 

    $ java -version
    
Various installation options are listed in the sections below. Select the approach you prefer and follow the given instructions to install the Confluent Platform.

## Operation System
Right now, DataFibers runs on Linux Ubuntu system. You can install it locally or in virtual machines, such as [Oracle VirtualBox](https://www.virtualbox.org/wiki/Downloads).

><img src="image/information.jpg" width="45" height="45"/> To visualize multiple core OS, make sure your host machine's BIOS visualization features are enabled .

## Environment Setup - Docker
To be update
## Environment Setup - Vagrant
The pre-build scripts for vagrant setup is available in [DF_DEMO](https://github.com/datafibers-community/df_demo) repository. This pre-build VM has following main software installed automatically.
* Java 1.8
* Git 1.9.1
* Apache Maven 3.0.5
* Apache Hadoop 2.6
* Apache Hive 1.2.1
* Apache Flink 1.3.2
* Confluent 3.3.0 with Apache Kafka 0.11.0.0
* MongoDB 3.4

Please following steps below to get the VM up running.
* Make sure Vagrant is installed from [here](https://www.vagrantup.com/downloads.html) or [here](https://github.com/tknerr/bills-kitchen). 
* Run below commands either in Linux or [GitBash Console](https://git-for-windows.github.io/) in Windows to download the setup scripts

      git clone https://github.com/datafibers-community/df_demo.git
      cd df_demo/df-environment/df-env-vagrant

* To run default environment setup, run

      vagrant up
      
><img src="image/warning.jpg" width="45" height="45"/> Virtualbox v1.8.1 has issues working with Vagrant in Windows. Pls. refer [here](troubleshooting_area.html#Vagarant_Issues) to resolve.
    
><img src="image/information.jpg" width="45" height="45"/>
To customize the environment setup, run [installvm.sh](https://github.com/datafibers/df_demo/blob/master/df-environment/df-env-vagrant/installvm.sh) is used to generate different profiles for VM setup.  

><img src="image/information.jpg" width="45" height="45"/> Once the vagrant installation scripts run completely, you will see a DF_DEMO instance running in VirtualBox. You can login by using username\password as vagrant\vagrant. 

Below are commonly used folders in the VirtualBox Ubuntu.
* Dependency software, such as confluent/Kafka, Hive, Hadoop, Flink, are installed in the **/opt/** folder
* The config used for Dependency software are in **/mnt/etc** folder
* Logs are kept in **/mnt/logs** 
* Hadoop HDFS are mount to folder **/mnt/dfs**

## Install DF Packages
To install DataFibers packages as well as scripts tools, run the follow command in the folder where you want to setup as follows.

    curl -sL http://www.datafibers.com/install | bash -
    
After running above installation script, following folders and artifacts are installed where you run the installation.
* **conf/** folder: All configuration files are here.
* **lib/** folder: Where to keep DF connect and data service jars.
* **repo/** folder: Where to keep DF source code downloaded.
* **bin/** folder: Where to keep scripts for run and admin.

In addition, the installation folder is set as $DF_HOME variable. $DF_HOME/bin is added to the system PATH. The **df_ops** or **dfops** alias is also added to the .profile to be accessed anywhere. For more details regarding to **df_ops**, refer to this [section](/quick_start.html#Operate_DF_Service).

    
