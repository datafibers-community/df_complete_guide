# Quick Start
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

><img src="image/tip.jpg" width="45" height="45"/> DF application has couple of command line options. You can use -h or --help options to see more details ```java -jar datafiber_jar_file.jar -h```

## Run A Demo
Once DF started at default port 8080, a web admin console is available at http://localhost:8000/admin/.

