# Troubleshooting Area

## Setup Issues

### AngularJS Issue

#### Access-Control-Allow-Origin header access is not allowed

When doing NG-Admin local domain test. Browser has such error **"**_**XMLHttpRequest cannot load ??. No  
'Access-Control-Allow-Origin' header is present on the requested Resource. Origin 'null' is therefore not allowed access.**_**"**

**Solution**, since the browser is blocking it as it usually allows a request in the same origin for security reasons. The easy way is to just add this [**Browser Extension**](https://chrome.google.com/webstore/detail/allow-control-allow-origi/nlfbmbojpeacfghkpbjhddihlkkiljbi?hl=en-US) in google chrome to allow access using CORS.

### Elastic Issues

#### localhost unreachable

Elastic cannot access localhost:9200 from host machine.

**Solution**, please do following two settings

* Set port forwarding 9200 guest to 9200 host in virtualbox.
* In elasticsearch/config/elasticsearch.yml put

  ```text
  network.host: 0.0.0.0
  ```

### MongoDB Issue

#### Unable access mongodb from out side of VirtualBox

It complains "Network Connect Issue" when connecting MongoDB from tool, such as [robomongo](https://robomongo.org/download) outside of VirtualBox.

**Solution**, make sure in your `/etc/mongod.conf` file you have the following line and restart the mongodb `sudo service mongod restart`to make it work immediately.

```text
net:
   bindIp: 0.0.0.0
```

If it still does not work, comment above line and try it again.

#### How to setup an oplog on a single MongoDB instance

[MongoDB Connect Source](https://github.com/DataReply/kafka-connect-mongodb) uses Mongodb oplog to fetch data. The MongoDB oplog allows you to keep track of changes that have happened on your database in real-time. This is a very useful tool that isn’t offered out of the box with a single server instance. You can follow these steps to enable to oplog on a standalone MongoDB instance.

1. Add following lines in your /etc/mongodb.conf file

   ```text
   replication:
       replSetName: rs0
       oplogSizeMB: 1024
   ```

   This will give your MongoDB server a replica set identity of rs0 and will allow your oplog to grow upto 1024mb.

2. Restart mongo

   ```text
   sudo service mongod restart
   ```

3. Go to Mongo shell and issue rs.initiate\(\) on the local database. You'll see **oplog.rs** created.

   ```text
   ~$ mongo
   MongoDB shell version: 3.0.14
   > use local
   switched to db local
   > rs.initiate()
   {
     "info2" : "no configuration explicitly specified -- making one",
     "me" : "mongo:27017",
     "info" : "Config now saved locally.  Should come online in about a minute.",
     "ok" : 1
   }
   > show collections
   oplog.rs
   ```

#### Unable start MongoDB automatically after reboot in Ubuntu 16

In the Ubuntu 16 with MongoDB cannot auto start after reboot. Use following command to fix this.

```text
sudo systemctl enable mongod.service
sudo systemctl daemon-reload
```

### Kafka Issue

#### Cannot connect Kafka in VirtualBox from outside IDE, such as IDEA

When we need to debug the code, we prefer to use IDE outside of the VirtualBox to connect to the Kafka Service in the VirtalBox. We need to ensure following settings are in place.

**Solution**, add following settings in the the **server.property** file for Kafka.

```text
host.name=localhost
advertised.host.name=127.0.0.1
```

#### Kafka Avro Console Consumer cannot consume message from producer

When we use regular Kafka producer/publisher, such as [code here](https://gist.github.com/datafibers/d063b255b50fa34515c0ac9e24d4485c), to send Avro message to Kafka, the regular avro console consumer like below will have exception reported.

```text
kafka-avro-console-consumer --zookeeper localhost:2181 --topic test --from-beginning
```

**Solution**, every avro message inside of Confluent Platform has following structure:

```text
<magic byte 0x0 1 byte> <schema id (4 bytes)> <Avro blob>
```

Therefore, we need to manually add these extra bytes before each Avro message.

### Spark Issues

#### Password less login with start-all.sh

Start spark cluster using start-all.sh requires password. We need to setup password less login in to bypass this. This is also applied to the Hadoop settings. Password-less ssh should be enabled on all nodes:

```text
ssh-keygen -t rsa -P ''

cat ~/.ssh/id_rsa.pub >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```

Check that ssh works locally without password:

```text
ssh localhost
```

Copy public key from the master node to worker node if you are in real cluster. Ignore this step in standalone machine.

```text
ssh-copy-id -i ~/.ssh/id_rsa.pub username@worker_node_hostname
```

### Vagrant Issues

#### Mount folder failure

Vagrant is not able to mount /vagrant folder in version 1.8.0 for windows.

**Solution**:  
Update the code windows\_unc\_path\(\) in C:\HashiCorp\Vagrant\embedded\gems\gems\vagrant-1.8.1\lib\vagrant\util\platform.rb to:

```text
def windows_unc_path(path)
  path = path.gsub("/", "\\")
  return path if path =~ /^[a-zA-Z]:\\?$/
  path
end
```

Or you can copy and replace using file [here](https://raw.githubusercontent.com/datafibers-community/df_demo/master/df-environment/df-env-vagrant/vagrant_patch/platform.rb).

### VM Issues

#### Mount a local shared folder with VM

1. Create a folder on the Host computer that you would like to share, for example~/share
2. Boot the Guest operating system in virtualbox
3. Select Devices -&gt; Shared Folders.
4. Choose the 'Add' button.
5. Select~/share and 'Make permanent' option
6. Mount the folder in the ubuntu in VM `sudo mount -t vboxsf -o uid=$UID,gid=$(id -g) share /mnt/share`

### Zeppelin Issue

#### Hive Driver Not Found

When using hive interpreter in Zeppelin, it reports "org.apache.hive.jdbc.HiveDriver class java.lang.ClassNotFoundExceptionClassNotFoundException"

**Solution**: Copy proper hadoop and hive jar to the Zeppelin interpreter folder and restart Zeppelin.

```text
cp /opt/hive/lib/hive-jdbc-1.2.1-standalone.jar /opt/zeppelin/interpreter/jdbc/
cp /opt/hadoop/share/hadoop/common/hadoop-common-2.6.0.jar /opt/zeppelin/interpreter/jdbc/
/opt/zeppelin/bin/zeppelin-daemon.sh reload
```

### OS Issue

#### Ubuntu Default Date is UTC, prefer to set to Local Time

DataFiber meta data use local OS time. If you want to see the meta data in local time, we need to change the OS time from default UTC to local time by following command.

```text
sudo dpkg-reconfigure tzdata
```

