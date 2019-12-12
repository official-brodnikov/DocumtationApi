# Predict categories

{% hint style="info" %}
result - array\[object\] or object, optional
{% endhint %}

{% hint style="info" %}
error - string, optional
{% endhint %}

#### Responses schema

| Variable | Type | Requiered |
| :--- | :--- | :--- |
| id | int | + |
| name | string | + |

## Read

{% api-method method="get" host="api" path="/predict\_categories" %}
{% api-method-summary %}
Predict
{% endapi-method-summary %}

{% api-method-description %}
Получение спрогнозированных категорий
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="content" type="string" required=true %}
Содержимое запроса
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```
{
    "result" : 
    [
        {
            "id" : 4,
            "name" : "Финансы" 
        },
        {
            "id" : 20,
            "name" : "Валюта"
        }
    ],
    "error" : null
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Could not find a cake matching this query.
{% endapi-method-response-example-description %}

```
{
    "result" : null,
    "error" : "The request could not be processed due to a syntax error."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



