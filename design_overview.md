# Design Overview
DataFibers application supports operations, such as ***L***ist, ***A***dd, ***U***pdate, and ***D***elete operations, on DF Connects or Transforms. In short, we call it **LAUD** operation. Below are DataFibers sequence diagram for common LAUD operations.

* Connect LAUD: Sequence for connect operations.
* Transform LAUD: Sequence for transform operations.
* Schema Registry LAU: Sequence for schema operations. 
* Installed L: Sequence for list of installed connects/transforms.
* Status Sync.: Sequence for synchronizing status.

## Connect LAUD
The Connect performs LAUD operation as follows.

{% plantuml %}
actor Rest_Client

activate DF_Service
database MongoDB
activate Kafka_Connect

Rest_Client -> DF_Service : Request to LAUD Connect
DF_Service -> Kafka_Connect : Forward LAUD Connect Request
Kafka_Connect -> Kafka_Connect : LAUD Kafka Connect
DF_Service <-- Kafka_Connect : LAUD Kafka Connect Response
DF_Service  -> MongoDB: Update Repository
MongoDB --> DF_Service: Update Response
Rest_Client <-- DF_Service : Response LAUD Connect
{% endplantuml %}

## Transform LAUD
The Connect performs LAUD operation as follows.

{% plantuml %}
actor Rest_Client
activate DF_Service
database MongoDB
activate Flink_ResourceMgr

Rest_Client -> DF_Service : Request to LAUD Transform
DF_Service -> Flink_ResourceMgr : Forward LAUD Transform Request
Flink_ResourceMgr -> Flink_ResourceMgr : LAUD Transform
DF_Service <-- Flink_ResourceMgr: LAUD Transform Response
DF_Service  -> MongoDB: Repo. Update Request
MongoDB --> DF_Service: Repo. Update Response
Rest_Client <-- DF_Service : Response LAUD Transform
{% endplantuml %}

## Schema Registry LAU
Schema registry is only support ***list***, ***add***, and ***update*** operations because of Confluent API limitation.

{% plantuml %}
actor Rest_Client
activate DF_Service
activate Schema_Registry

Rest_Client -> DF_Service : Request to LAU Avro Schema 
DF_Service -> Schema_Registry : Forward LAU Avro Schema Request
Schema_Registry -> Schema_Registry : LAU Avro Schema
DF_Service <-- Schema_Registry: LAU Transform Response
Rest_Client <-- DF_Service : Response LAU Avro Schema
{% endplantuml %}

## Install L
Installed connect or transform view only supports a read-only ***list*** operation as follows.

{% plantuml %}
actor Rest_Client
activate DF_Service
activate Kafka_Connect

Rest_Client -> DF_Service : Request to list installed 
DF_Service -> Kafka_Connect : Forward list installed  Request
Kafka_Connect -> Kafka_Connect : Get list installed 
DF_Service <-- Kafka_Connect: list installed Response
Rest_Client <-- DF_Service : Response list installed 
{% endplantuml %}

## Status Sync.
There are following functions to get status update regularly.

### Connect Sync.
DataFibers application launches a background daemon for regular synchronizing the Kafka connect status with what's in the repository (MongoDB).

{% plantuml %}
activate DF_Service
database MongoDB
activate Kafka_Connect

DF_Service -> MongoDB : Request list of active Connect
note right: Use vertx.setPeriodic to \ncheck every 10 sec.
DF_Service <-- MongoDB : Response list of active Connect
DF_Service -> Kafka_Connect: Loop to request status for each active Connect
Kafka_Connect --> DF_Service : Response status for each active Connect
MongoDB <- DF_Service : Request to check/update Connect status
note right: if the status has no change, \ngo to next Connect
MongoDB --> DF_Service : Response Connect status updated
{% endplantuml %}

### Metadata Sync.
DataFibers application does not involve into the metadata sync path directly, except launching the MongoDBSink and creating a Avro schema for the metadata.

{% plantuml %}
activate Connect
activate Kafka
activate Kafka_Connect
database MongoDB

Connect -> Kafka: Send metadata
note right: Send to df_meta topic
Kafka <- Kafka_Connect : Fetch data form df_meta
note left: MongoDBSink Daemon
Kafka --> Kafka_Connect : Response metadata from the topic
Kafka_Connect -> MongoDB: Sink metadata
Kafka_Connect <-- MongoDB: Response sink done
{% endplantuml %}


### Transform Sync.

### Startup Sync.
When DF starts, it first imports all available connect from repository and synchronize their status with Kafka connect.

{% plantuml %}
activate DF_Service
database MongoDB
activate Kafka_Connect

DF_Service -> MongoDB: Request list of connect
DF_Service <- MongoDB : Response list active connect name
DF_Service -> Kafka_Connect : Request status from the connect
note left: Foreach connect returned
Kafka_Connect -> Kafka_Connect: Get connect status 
DF_Service <-- Kafka_Connect: Response connect status
DF_Service -> MongoDB: Request compare/update the connect status
DF_Service <-- MongoDB : Response status updated
{% endplantuml %}
