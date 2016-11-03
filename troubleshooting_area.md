# Troubleshooting Area
## Setup Issues
### Vagrant Issues
#### Mount folder failure
Vagrant is not able to mount /vagrant folder in version 1.8.0 for windows. 

**Solution**: 
Update the code windows_unc_path() in C:\HashiCorp\Vagrant\embedded\gems\gems\vagrant-1.8.1\lib\vagrant\util\platform.rb to:

        def windows_unc_path(path)
          path = path.gsub("/", "\\")

          # If the path is just a drive letter, then return that as-is
          return path if path =~ /^[a-zA-Z]:\\?$/

          # Convert to UNC path
          path
        end

### Elastic Issues
#### localhost unreachable
Elastic cannot access localhost:9200 from host machine. 

**Solution**, pls. do following two settings
* Set port forwording 9200 guest to 9200 host in virtualbox.
* In elasticsearch/config/elasticsearch.yml put 
    
      network.host: 0.0.0.0

### AngularJS Issue
#### Access-Control-Allow-Origin header access is not allowed
When doing NG-Admin local domain test. Browser has such error **"*XMLHttpRequest cannot load ??. No
'Access-Control-Allow-Origin' header is present on the requested Resource. Origin 'null' is therefore not allowed access.*"** 

**Solution**, since the browser is blocking it as it usually allows a request in the same origin for security reasons. The easy way is to just add this **[Browser Extension](https://chrome.google.com/webstore/detail/allow-control-allow-origi/nlfbmbojpeacfghkpbjhddihlkkiljbi?hl=en-US)** in google chrome to allow access using CORS.

### MongoDB Issue
#### Unable access mongodb from out side of VirtualBox
It compains "Network Connect Issue" when connecting MongoDB from tool, such as [robomongo](https://robomongo.org/download) outside of VirtualBox.

**Solution**, make sure in your ```/etc/mongodb.conf``` file you have the following line and restart the mongodb ```sudo service mongod restart```to make it work immediately.
    
      bind_ip = 0.0.0.0

### Kafka Connect Issue
#### Kafka Avro Console Consumer cannot consume message from producer
When we use regular Kafka producer/publisher, such as [code here](https://gist.github.com/datafibers/d063b255b50fa34515c0ac9e24d4485c), to send Avro message to Kafka, the regular avro console consumer like below will have exception reported.
    kafka-avro-console-consumer --zookeeper localhost:2181 --topic test --from-beginning

