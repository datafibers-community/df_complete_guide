# Connects Configurations

## File Streaming Source

File streaming source connect is used for streaming data in files to DataFibers' Kafka backbone \(to one Kafka topic\). This connect is compatible with official Kafka file source connect. The data in DF is quoted as String.

### Configuration Samples

```text
{
    "connector.class": "org.apache.kafka.connect.file.FileStreamSourceConnector",
    "file": "openrecipes.json",
    "tasks.max": "1",
    "name": "local-file-source",
    "topic": "finance"
}
```

### Configuration Details

| Config | Request | Default | Comments |
| :--- | :--- | :--- | :--- |
| **connector.class** | Yes | N/A | Kafka Connect Class Name. |
| **file** | Yes | N/A | File name for streaming to Kafka. |
| **tasks.max** | Yes | N/A | Number of tasks in parallel. |
| **name** | Optional | **Connector** Name in WebUI | Kafka Connect name. |
| **topic** | Yes | N/A | The single Kafka topic name having data streamed. |

## File Streaming Sink

File streaming sink connect is used for streaming data into files from DataFibers' Kafka backbone \(from topics\). This connect is compatible with official Kafka file sink connect. The data streamed out from DF has to be quoted as String.

### Configuration Samples

```text
{
    "connector.class": "org.apache.kafka.connect.file.FileStreamSinkConnector",
    "file": "openrecipes_sink.json",
    "tasks.max": "1",
    "name": "local-file-sink",
    "topics": "finance"
}
```

### Configuration Details

| Config | Request | Default | Comments |
| :--- | :--- | :--- | :--- |
| **connector.class** | Yes | N/A | Kafka Connect Class Name. |
| **file** | Yes | N/A | File name for exporting from Kafka. |
| **tasks.max** | Yes | N/A | Number of tasks in parallel. |
| **name** | Optional | **Connector** Name in WebUI | Kafka Connect name. |
| **topics** | Yes | N/A | List of Kafka topics having data streamed out. |

