# Book Feature Demo

## Reference
1. [PlantUML Viewer](https://www.planttext.com/)
2. [PlantUML Cheatsheet](http://ogom.github.io/draw_uml/plantuml/)

## Annotations

><img src="image/information.png"> This is for information.

><img src="image/warning.png"> This is for pitfall.

><img src="image/tip.png"> This is for tips.

## PlantUML
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

## EnChart
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
