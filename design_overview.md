# Design Overview
Most DataFibers components support list, add, update, and delete operations. In short, we call it **LAUD** operation.
## Connect LAUD
The Connect follows LAUD operation as follows.

@startuml
actor Rest_Client

activate DF_Service
database MongoDB
activate Kafka_Connect
activate Flink_ResourceMgr

Rest_Client -> DF_Service : Request to LAUD Connect

DF_Service -> Kafka_Connect : Forward LAUD Connect Request

Kafka_Connect -> Kafka_Connect : LAUD Kafka Connect
DF_Service <-- Kafka_Connect : LAUD Kafka Connect Response
deactivate Kafka_Connect

DF_Service  -> MongoDB: Update Repository
MongoDB-> DF_Service: Update Response
Rest_Client <-- DF_Service : Response LAUD Connect

@enduml

