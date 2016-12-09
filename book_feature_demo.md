# Book Feature Demo

## Reference
1. [PlantUML Viewer](https://www.planttext.com/)
2. [PlantUML Cheatsheet](http://ogom.github.io/draw_uml/plantuml/)
3. 




## Annotations
><i class="fa fa-info-circle"></i> This is for information.
>
><i class="fa fa-exclamation-circle" aria-hidden="true"></i> This is for pitfall
>
><i class="fa fa-cog" aria-hidden="true"></i> This is for tips.

{% plantuml %}
actor Rest_Client

Rest_Client -> DF_Service : Request to ACID Connect

activate DF_Service
DF_Service -> Kafka_Connect : ACID Connect Request

activate Kafka_Connect
Kafka_Connect -> Kafka_Connect : ACID Kafka Connect
DF_Service <-- Kafka_Connect : ACID Kafka Connect Response
deactivate Kafka_Connect

Ticket -> DF_Service : ACID Repository - MongoDB
Rest_Client <-- DF_Service : Response ACID Connect
deactivate DF_Service
{% endplantuml %}

```chart
{
    "title": {
        "text": "Fruits number"
    },
    "tooltip": {},
    "legend": {
        "data":["Number"]
    },
    "xAxis": {
        "data": ["Apple","Banana","Peach","Pear","Grape","Kiwi"]
    },
    "yAxis": {},
    "series": [{
        "name": "Number",
        "type": "bar",
        "data": [5, 20, 36, 10, 10, 20]
    }]
}
```
