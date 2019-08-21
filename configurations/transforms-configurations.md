# Transforms Configurations

## Flink Stream SQL Generic

### Configuration Samples

```text
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
```

### Configuration Details

| Config | Request | Default | Comments |
| :--- | :--- | :--- | :--- |
| **group.id** | Optional | df\_trans\_flink\_group\_id | Kafka consumer id. |
| **data.format.input** | Optional | json | Available value are "json\_string" and "json". |
| **data.format.output** | Optional | json | Available value are "json\_string" and "json".**\[\*\]** |
| **avro.schema.enabled** | Optional | false | Whether AVRO schema is enabled in Kafka Connect. |
| **column.name.list** | Yes | N/A | The list of column names output to Kafka topic. |
| **column.schema.list** | Yes | N/A | The list of datatype to Kafka topic. |
| **topic.for.query** | Yes | N/A | The Kafka topic to query data. |
| **topic.for.result** | Yes | N/A | The Kafka topic to output data |
| **trans.sql** | Yes | N/A | The Flink Stream SQL query. |

Example of json and json string

* json: {"name":"BABA", "location":"China"}
* json string: "{\"name\":\"BABA\", \"location\":\"China\"}"

## Flink Stream SQL A2J

Below is the configuration for Flink stream SQL from Avro data to Json data.

### Configuration Samples

```text
{
    "topic.for.query":"test",
    "topic.for.result":"stock",
    "schema.subject":"test-value"
    "trans.sql":"SELECT STREAM symbol, name FROM test"
}
```

### Configuration Details

| Config | Request | Default | Comments |
| :--- | :--- | :--- | :--- |
| **group.id** | Optional | df\_trans\_flink\_group\_id | Kafka consumer id. |
| **static.avro.schema** | Optional | N/A | The AVRO schema string. |
| **schema.subject** | Optional | N/A | The AVRO schema subject in schema registry. |
| **schema.version** | Optional | 'latest' | Specified version of schema to use |
| **schema.registry** | Optional | localhost:8081 | The host and port for schema registry. |
| **topic.for.query** | Yes | N/A | The Kafka topic to query data. |
| **topic.for.result** | Yes | N/A | The Kafka topic to output data |
| **trans.sql** | Yes | N/A | The Flink Stream SQL query. |

**Note**, you must specify Avro schema either by **schema.subject** or **static.avro.schema**.

