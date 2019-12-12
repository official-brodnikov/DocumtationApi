# Categories

{% hint style="info" %}
error - string, optional
{% endhint %}

{% hint style="info" %}
result - array\[object\] or object, optional
{% endhint %}

#### Responses schema

| Variable | Type | Required |
| :--- | :--- | :--- |
| id | int | + |
| name | string | + |

## Read

{% api-method method="get" host="api" path="/categories" %}
{% api-method-summary %}
All Categories
{% endapi-method-summary %}

{% api-method-description %}
Получить все категории
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{  
    "result" : 
    [
        { 
            "id" : 1, 
            "name" : "Погода" 
        }, 
        { 
            "id" : 2, 
            "name" : "Информация" 
        }
    ], 
    "error" : null
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

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

{% api-method method="get" host="api" path="/categories/:id" %}
{% api-method-summary %}
Category
{% endapi-method-summary %}

{% api-method-description %}
Получить конкретную категорию
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="integer" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{ 
    "result" :
    {
        "id" : 1, 
        "name" : "Погода"
    },
    "error" : null
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

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

