# Quick Start

## Operate DF Service

A command alias **df\_ops** or **dfops** is available to operate DataFibers service in more convenient way. By using this command, both environment and data service can be operated easily. This command has following syntax and options.

```text
dfops [operation] [service] [option]
```

| \[operation\] | Usage |
| :--- | :--- |
| start | start all environment and df services |
| stop | stop all environment and df services |
| restart | restart all environment and df services |
| status | show status of all environment and df services |
| format | format Hadoop, remove all logs and data |
| install | install df packages from master or branch |
| update | fetch df update packages |
| help | show command help menu |
| admin | perform df admin operations |
|  |  |
| **\[service\]** | **Usage** |
| default | start df services with Confluent, Flink environment. This is by default. |
| min | start df services with Confluent environment. |
| max | start df services with Confluent, Flink, Hadoop environment. |
|  |  |
| **\[option\]** | **Usage** |
| d | run df services in debug mode. This is by default. |
| other | run df services in normal mode |

> ![](../.gitbook/assets/tip.jpg) DF jar also has couple of command line options. You can use -h or --help options to see more details `java -jar datafiber_jar_file.jar -h`

## Run A Demo

Once DF started at default port 8080, a web admin console is available at [http://localhost:8000/admin/](http://localhost:8000/admin/).

There is a short demo using DataFibers to process NetCDF as follows.

{% embed url="https://youtu.be/S1CsAf5qCBQ" %}



