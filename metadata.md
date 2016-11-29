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
| id | String |Unique number string which is generated from mongodb, used as job id. |
| taskId | String | Identify each task in a job. It is manually set now. |
| name | String | Name of the job. |
| connector | String | Name of the connector/task used. This maps to Kafka Connect name attribute. |
| connectorType | Enum | Identify proper connector type from enum. |
| connectorCategory | String | Indetify the category of task, connect or transform. |
| description | String | Task description as free text.|
| status | String | Indetify the task status, such as FAILED, RUNNING, etc. |
| udfUpload | String | Only used for UDF transform to identify the path of UDF Jar. |
| jobConfig | HashMap<String, String>  | Key-value pairs of job level configuration in details. |
| connectorConfig | HashMap<String, String>  | Key-value pairs of task level configuration in details. |


## Meta

## History