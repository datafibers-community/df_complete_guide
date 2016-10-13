# Transforms Configurations


## 1. Flink Stream SQL

### Configuration Samples

    {
        "group.id":"consumer3",
        "data.format.input":"json_string",
        "data.format.output":"json_string",
        "avro.schema.enabled":"false",
        "column.name.list":"symbol,name",
        "column.schema.list":"string,string",
        "topic.for.query":"finance",
        "topic.for.result":"stock",
        "trans.sql":"SELECT STREAM symbol, name FROM finance"
    }
### Configuration Details

| Config | Request | Default | Comments |
| -- | -- | -- | -- |
| **group.id** | Optional | df_trans_flink_group_id | Kafka consumer id.|
| **data.format.input** | Optional | json | Available value are "json_string" and "json". | 
| **data.format.output** |Optional | json | Available value are "json_string" and "json".**[*]**| 
| **avro.schema.enabled** |Optional | false | Whether AVRO schema is enabled in Kafka Connect. | 
| **column.name.list** |Yes | N/A | The list of column names output to Kafka topic. | 
| **column.schema.list** |Yes |N/A| The list of datatype to Kafka topic. | 
| **topic.for.query** |Yes | N/A | The Kafka topic to query data. | 
| **topic.for.result** |Yes | N/A | The Kafka topic to output data | 
| **trans.sql** |Yes | N/A | The Flink Stream SQL query. | 

Example of json and json string
* json: {"name":"BABA", "location":"China"}
* json string: "{\"name\":\"BABA\", \"location\":\"China\"}"
