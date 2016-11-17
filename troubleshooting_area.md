# Troubleshooting Area
## Setup Issues
### AngularJS Issue
#### Access-Control-Allow-Origin header access is not allowed
When doing NG-Admin local domain test. Browser has such error **"*XMLHttpRequest cannot load ??. No
'Access-Control-Allow-Origin' header is present on the requested Resource. Origin 'null' is therefore not allowed access.*"** 

**Solution**, since the browser is blocking it as it usually allows a request in the same origin for security reasons. The easy way is to just add this **[Browser Extension](https://chrome.google.com/webstore/detail/allow-control-allow-origi/nlfbmbojpeacfghkpbjhddihlkkiljbi?hl=en-US)** in google chrome to allow access using CORS.

### Elastic Issues
#### localhost unreachable
Elastic cannot access localhost:9200 from host machine. 

**Solution**, pls. do following two settings
* Set port forwording 9200 guest to 9200 host in virtualbox.
* In elasticsearch/config/elasticsearch.yml put 
    
      network.host: 0.0.0.0

### MongoDB Issue
#### Unable access mongodb from out side of VirtualBox
It compains "Network Connect Issue" when connecting MongoDB from tool, such as [robomongo](https://robomongo.org/download) outside of VirtualBox.

**Solution**, make sure in your ```/etc/mongod.conf``` file you have the following line and restart the mongodb ```sudo service mongod restart```to make it work immediately.
    
    bind_ip = 0.0.0.0
    
If it still does not work, comment above line and try it again.    

### Kafka Issue
#### Cannot connect Kafka in VirtualBox from outside IDE, such as IDEA
When we need to debug the code, we prefer to use IDE outside of the VirtualBox to connect to the Kafka Service in the VirtalBox. We need to ensure following settings are in place.

**Solution**, add following settings in the the **server.property** file for Kafka.

    host.name=localhost
    advertised.host.name=127.0.0.1

#### Kafka Avro Console Consumer cannot consume message from producer
When we use regular Kafka producer/publisher, such as [code here](https://gist.github.com/datafibers/d063b255b50fa34515c0ac9e24d4485c), to send Avro message to Kafka, the regular avro console consumer like below will have exception reported.

    kafka-avro-console-consumer --zookeeper localhost:2181 --topic test --from-beginning

**Solution**, every avro message inside of Confluent Platform has following structure:

    <magic byte 0x0 1 byte> <schema id (4 bytes)> <Avro blob>    
Therefore, we need to manually add these extra bytes before each Avro message.

### Vagrant Issues
#### Mount folder failure
Vagrant is not able to mount /vagrant folder in version 1.8.0 for windows. 

**Solution**: 
Update the code windows_unc_path() in C:\HashiCorp\Vagrant\embedded\gems\gems\vagrant-1.8.1\lib\vagrant\util\platform.rb to:

    def windows_unc_path(path)
      path = path.gsub("/", "\\")
      return path if path =~ /^[a-zA-Z]:\\?$/
      path
    end

Or you can copy and replace using file [here](https://raw.githubusercontent.com/datafibers-community/df_demo/master/df-environment/df-env-vagrant/vagrant_patch/platform.rb).


### Zeppelin Issue
#### Hive Driver Not Found
When using hive interpreter in Zeppelin, it reports "org.apache.hive.jdbc.HiveDriver class java.lang.ClassNotFoundExceptionClassNotFoundException"

**Solution**: Copy proper hadoop and hive jar to the Zeppelin interpreter folder and restart Zeppelin.

    cp /opt/hive/lib/hive-jdbc-1.2.1-standalone.jar /opt/zeppelin/interpreter/jdbc/
    cp /opt/hadoop/share/hadoop/common/hadoop-common-2.6.0.jar /opt/zeppelin/interpreter/jdbc/
    /opt/zeppelin/bin/zeppelin-daemon.sh reload
