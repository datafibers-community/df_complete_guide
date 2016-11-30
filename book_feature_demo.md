# Book Feature Demo

## Annotations
><i class="fa fa-info-circle"></i> This is for information.
>
><i class="fa fa-exclamation-circle" aria-hidden="true"></i> This is for pitfall
>
><i class="fa fa-cog" aria-hidden="true"></i> This is for tips.


{% chart %}
{
    "data": {
        "type": "bar",
        "columns": [
            ["data1", 30, 200, 100, 400, 150, 250],
            ["data2", 50, 20, 10, 40, 15, 25]
        ],
        "axes": {
            "data2": "y2"
        }
    },
    "axis": {
        "y2": {
            "show": true
        }
    }
}
{% endchart %}