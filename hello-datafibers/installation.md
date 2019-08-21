# Installation

## Requirements

The software requirement for DataFibers are

* Java 8
* Apache Kafka &gt;= 0.11.0
* Apache Flink &gt;= 1.3.0
* MongoDB

The Java runtime version is at least version 1.8. Java installation varies by platform, so please check the JRE installation version for your platform before installing the DataFibers using following command:

```text
$ java -version
```

Various installation options are listed in the sections below. Select the approach you prefer and follow the given instructions to install the Confluent Platform.

## Operation System

Right now, DataFibers runs on Linux Ubuntu system. You can install it locally or in virtual machines, such as [Oracle VirtualBox](https://www.virtualbox.org/wiki/Downloads).

> ![](../.gitbook/assets/information.jpg) To visualize multiple core OS, make sure your host machine's BIOS visualization features are enabled .

## Environment Setup - Docker

To be update

## Environment Setup - Vagrant

The pre-build scripts for vagrant setup is available in [DF\_DEMO](https://github.com/datafibers-community/df_demo) repository. This pre-build VM has following main software installed automatically.

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

  ```text
  git clone https://github.com/datafibers-community/df_demo.git
  cd df_demo/df-environment/df-env-vagrant
  ```

* To run default environment setup, run

  ```text
  vagrant up
  ```

> ![](../.gitbook/assets/warning.jpg) Virtualbox v1.8.1 has issues working with Vagrant in Windows. Pls. refer [here](https://github.com/datafibers-community/datafibers-complete-guide/tree/de0445ca4d80e881f015535480562ba3ba4d8169/troubleshooting_area.html#Vagarant_Issues) to resolve.
>
> ![](../.gitbook/assets/information.jpg) To customize the environment setup, run [installvm.sh](https://github.com/datafibers/df_demo/blob/master/df-environment/df-env-vagrant/installvm.sh) is used to generate different profiles for VM setup.
>
> ![](../.gitbook/assets/information.jpg) Once the vagrant installation scripts run completely, you will see a DF\_DEMO instance running in VirtualBox. You can login by using username\password as vagrant\vagrant.

Below are common folders used by the DataFibers package.

* **/opt** : Dependent software, such as confluent/Kafka, Hive, Hadoop, Flink, are installed here. 
* **/mnt/etc** : The config used for dependent software.
* **/mnt/logs** : Where to keep logs.
* **/mnt/dfs** : Hadoop file system are mount here.

## Install DF Packages

To install DataFibers packages as well as scripts tools, run the follow command in the folder where you want to setup as follows.

```text
curl -sL http://www.datafibers.com/install | bash -
```

After running above installation script, following folders and artifacts are installed in the current folder.

* **conf/** : All configuration files are here.
* **lib/** : Where to keep certified connect and service jars.
* **repo/** : Where to keep source code.
* **bin/** : Where to keep operation and administration scripts.

In addition, the installation folder \(current folder\) is set as $DF\_HOME variable in **~/.profile**. $DF\_HOME/bin is added to the system PATH. The **df\_ops** or **dfops** alias is also added to the **~/.profile** so the command can be accessed anywhere. For more details regarding to operation commands, please refer to this [section](https://github.com/datafibers-community/datafibers-complete-guide/tree/de0445ca4d80e881f015535480562ba3ba4d8169/quick_start.html#Operate_DF_Service).

