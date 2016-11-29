# Meta Data
DataFibers define three type of meta data model for data structuring and serializing as follows. There are defined in the ```package com.datafibers.model```.
## JOB
The purpose of Job model is to keep all information for task/job either for connects or transforms type of tasks in DataFibers.

    public class DFJobPOPJ {
        private String id; 
        private String taskId;
        private String name;
        private String connector; 
        private ConstantApp.DF_CONNECT_TYPE connectorType; 
        private String connectorCategory;
        private String description; 
        private String status; 
        private String udfUpload;
        private HashMap<String, String> jobConfig; 
        private HashMap<String, String> connectorConfig; 
        ...

| Attribute | Data Type| Usage |
| -- | -- | -- |
| id | String | Unique number string which is generated from mongodb, used as job id. |
| taskId | String | Identify each task in a job. It is manually set now. |
| name | String | Name of the job. |
| connector | String | Name of the connector/task used. This maps to Kafka Connect name attribute. |
| connectorType | Enum | Identify proper connector type from enum. |
| connectorCategory | String | Identify the category of task, connect or transform. |
| description | String | Task description as free text.|
| status | String | Identify the task status, such as FAILED, RUNNING, etc. |
| udfUpload | String | Only used for UDF transform to identify the path of UDF Jar. |
| jobConfig | HashMap<String, String>  | Key-value pairs of job level configuration in details. |
| connectorConfig | HashMap<String, String>  | Key-value pairs of task level configuration in details. |


## Meta
Meta view will be a read-only view in DataFibers web console.

| Attribute | Data Type| Usage |
| -- | -- | -- |
| topicId | String | Unique number string which is generated from mongodb, used as job id. |
| topic | String | Identify subject of data. It is now Kafka topic. |
| schemaID | String | Identify the schema in schema registry. |
| schemaName | String | Identify the schema name in schema registry. |
| schemaVersion | int | Identify the schema version associated with the topic in schema registry. |
| sourceList | HashMap<String, String> | Identify the list of source as <type, path> where we ingest to this topic. |
| targetList | HashMap<String, String> | Identify the list of target as <type, path> where we extract from this topic. |
| consumeList | [String] | Identify the list of consumer group of Kafka. |
| volumn | String | Identify the volumn of data in this topic in terms of MB/GB/TB. |
| namespace | String | java package/maven like namespace for topic category and permission. |
| topicCreateDate | String  | Datetime when the topic is created. |
| dataCreateDate | String  | Datetime when the topic is firstly populated data. |
| dataUpdateDate | String  | Datetime when the latest data is been written. |
| topicStatus | String  | Identify whether the topic is being used or not, such as ACTIVE, DEACTIVE, DELETED, etc. |
| permissions | String  | Reserved for future permission control on the row. |

## History
History view will be a read-only view in DataFibers web console.