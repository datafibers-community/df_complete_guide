# Book Feature Demo

## Annotations
><i class="fa fa-info-circle"></i> This is for information.
>
><i class="fa fa-exclamation-circle" aria-hidden="true"></i> This is for pitfall
>
><i class="fa fa-cog" aria-hidden="true"></i> This is for tips.

{% plantuml %}
Bob->Alice : hello
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
