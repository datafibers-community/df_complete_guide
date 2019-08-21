# Architecture Design

DataFibers application supports operations, such as _**L**_ist, _**A**_dd, _**U**_pdate, and _**D**_elete operations, on DF Connects or Transforms. In short, we call it **LAUD** operation. Below are DataFibers sequence diagram for common LAUD operations.

* Connect LAUD: Sequence for connect operations.
* Transform LAUD: Sequence for transform operations.
* Schema Registry LAU: Sequence for schema operations. 
* Installed L: Sequence for list of installed connects/transforms.
* Status Sync.: Sequence for synchronizing status.
* Stream Back: Sequence to stream back the batch result to queue.

## Connect LAUD

The Connect performs LAUD operation as follows.

## Transform LAUD

The Connect performs LAUD operation as follows.

## Schema Registry LAU

Schema registry is only support _**list**_, _**add**_, and _**update**_ operations because of Confluent API limitation.

## Install L

Installed connect or transform view only supports a read-only _**list**_ operation as follows.

## Status Sync.

There are following functions to get status update regularly.

### Connect\|Transform Sync.

DataFibers application launches a background daemon for regular synchronizing the connect/transform status in the repository \(MongoDB\) against Kafka/Flink **R**est **A**pi **S**ervices \(RAS\).

### Metadata Sync.

DataFibers application does not involve into the metadata, which keeps track of files processed by connects or transforms, synchronize path directly. For instead, it creates the metadata schema, and then launches the MongoDBSink to ship data into repository.

### Startup Sync.

When DF starts, it first imports all available connect from repository and synchronize their status with Kafka connect.

> ![](../.gitbook/assets/information.jpg) We do not create start-up synchronize for transforms since we are not able to rebuilt the task configurations if we import the active transforms from Flink.

## Stream Back.

When batch processing is complete, DF supports to stream back the result set to the queue for further consuming or transformation. It first exports the result set to a json file. Then, it leverages file connector to send the file content to the queue when df status sync. daemon detects the batch file export is done. Once succeeded, the stream back connector will be deleted.

