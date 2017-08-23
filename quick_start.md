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

## Operate DF Applications
A command df_ops is added to the PATH environment variable to operate df data service in more convenient way. It has following command options.
    
    df_ops [operation] [service] [option]
    
|[operation]|Usage|
| ------------- | ------------- |
|start   || 
|stop   || 
|restart   || 
|status|| 
|format|| 
|install|| 
|upgrade| not support yet| 
|admin|not support yet| 

## Run A Demo