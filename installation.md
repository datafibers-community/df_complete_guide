# Installation

## Requirements
The software requirement for DataFibers are
* Java 8
* Apache Kafka >= 3.0.0
* Apache Flink >= 1.1.0
* MongoDB

The Java runtime version is at least version 1.8. Java installation varies by platform, so please check the JRE installation version for your platform before installing the DataFibers using following command: 

    $ java -version
    
Various installation options are listed in the sections below. Select the approach you prefer and follow the given instructions to install the Confluent Platform.

## Operation System
Right now, DataFibers runs on Linux system. You can install various distribution, such as Ubuntu, Redhat, etc locally or in virtual machines, such as [Oracle VirtualBox](https://www.virtualbox.org/wiki/Downloads).

><i class="fa fa-info-circle"></i> To visualize multiple core OS, make sure your host machine's BIOS visualization features are enabled .

## Environment Setup - Docker
## Environment Setup - Vagrant
The pre-build scripts for vagrant setup is available in [DF_DEMO](https://github.com/datafibers-community/df_demo) repository. This pre-build VM has following softs installed.
* Java 1.8
* Apache Maven 3.0.5
* Git 1.9.1
* Apache Hadoop v2.5
* Apache Hive 1.2.1
* Confluent 3.0.1 with Apache Kafka 0.10.0.1
* Apache Flink 1.1.3

Please following steps below to get the VM up running.
* Make sure Vagrant is installed from [here](https://www.vagrantup.com/downloads.html) or [here](https://github.com/tknerr/bills-kitchen). Run below commands either in Linux or [GitBash Console](https://git-for-windows.github.io/) in Windows.
* Get the setup scripts
      git clone https://github.com/datafibers-community/df_demo.git
      cd df_demo/df-environment/df-env-vagrant

* To run default environment setup, run
      vagrant up
><i class="fa fa-info-circle"></i> To visualize multiple core OS, make sure your host machine's BIOS visualization features are enabled .
    
* To customize the environment setup, run [installvm.sh](https://github.com/datafibers/df_demo/blob/master/df-environment/df-env-vagrant/installvm.sh) is used to generate different profiles for VM setup.  
      ./installvm.sh

## Environment Setup - Manually Installation

### Backbone Software
Backbone software are basic components which DataFibers leverage for big data processing. 

#### Flink
#### Kafka
#### Mongo


### Developer Tools
Developer software packages are optional for general DataFibers' users. This packages are generally needed for self compile or code contribution.
#### IDE
#### Git
#### Maven

## Install DF Packages
