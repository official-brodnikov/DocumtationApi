# Categories

{% hint style="warning" %}
error - string, optional
{% endhint %}

{% hint style="warning" %}
result - array\[object\] or object, optional
{% endhint %}

## Create

## Read

{% api-method method="get" host="api" path="/requests?category\_id=<<category\_id>>" %}
{% api-method-summary %}
All Requests by Category
{% endapi-method-summary %}

{% api-method-description %}
Получить все запросы, принадлежащие к заданной категории
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="category\_id" type="integer" required=true %}

{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{ 
    "result" :
    {
        "category_name" : "Погода",
        "category_id" : 1, 
        "requests" :
        [
            {
                 "request_id" : 1, 
                 "request_content" : "Сколько сейчас градусов" 
            }, 
            { 
                "request_id" : 2,
                "request_content" : "Какая погода завтра в Москве"
            }
        ]
    },
    "erorr" : null
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{ 
    "result" : {},
    "error" : "The request could not be processed due to a syntax error."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Responses schema

| Variable | Type | Required |
| :--- | :--- | :--- |
| category\_name | string | + |
| category\_id | int | + |
| request\_content | string | + |
| request\_id | int | + |

## Update

