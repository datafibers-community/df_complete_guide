# Quick Start
## Start DF Dependencies
Once installed through install_df.sh, there are following scripts to launch different DF running dependency environment.

| Environment Setup Shell Script  | Functions |
| ------------- | ------------- |
| df_env_distributed_start.sh  | Launch distributed connect service only |
| df_env_distributed_start_avro.sh  | Launch distributed connect service with schema validation  |
| df_env_distributed_start_avro_flink.sh | Launch distributed connect service with schema validation and Flink |
| df_env_distributed_start_avro_hdp_hive_flink.sh | Launch distributed connect service with schema validation, Hadoop, Hive, and Flink|
| df_env_standalone_start.sh | Launch standalone connect service only |

## Start DF Applications
To start the DF application, you can ```java -jar``` command launcher, such as 

    java -jar df-data-service-1.1-SNAPSHOT-fat.jar
After this, DF will launch DataFiber data service at 8080 and web console service at 8000. Then, you can open the web console page at your browser http://localhost:8000/admin/. You'll need to install [proper browser plugin](troubleshooting_area.html#Access-Control-Allow-Origin_header_access_is_not_allowed) when you host in local VM.

><img src="image/tip.jpg" width="45" height="45"/> DF application has couple of command line options. You can use -h or --help options to see more details ```java -jar datafiber_jar_file.jar -h```

## Operate DF Service
A command alias **df_ops** or **dfops** is available to operate df data service in more convenient way. By using this command, both environment and data service can be operated easily. This command has following options.
    
    df_ops [operation] [service] [option]
    
|[operation]|Usage|
| ------------- | ------------- |
|start   |start all environment and df services| 
|stop   |stop all environment and df services| 
|restart   |restart all environment and df services| 
|status|show status of all environment and df services| 
|format|format Hadoop, remove all logs and data| 
|install|install df packages| 
|help| show command help menu| 
|admin|perform df admin operations| 
|||
|**[service]**|**Usage**|
|default   |start df services with Confluent, Flink environment. This is by default.| 
|min   |start df services with Confluent environment.| 
|max   |start df services with Confluent, Flink, Hadoop environment.| 
|||
|**[option]**|**Usage**|
|d|run df services in debug mode. This is by default.| 
|other|run df services in normal mode|  


## Run A Demo