# Relations

{% hint style="warning" %}
error - string, optional
{% endhint %}

{% hint style="warning" %}
result - array\[object\] or object, optional
{% endhint %}

## Read

{% api-method method="get" host="api" path="/admin/relations/:request\_id" %}
{% api-method-summary %}
Relations
{% endapi-method-summary %}

{% api-method-description %}
Получить список связей запроса
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="request\_id" type="integer" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```
{  
    "result" : 
    {
        "request_id" : 1,  
        "request_content" : "Сколько сейчас градусов",  
        "categories" : 
        [
            { 
                "category_id" : 1, 
                "category_name" : "Погода" 
            }, 
            { 
                "category_id" : 2, 
                "category_name" : "Информация" 
            }
        ] 
    },
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

#### 

#### Responses schema

| Variable | Type | Required |
| :--- | :--- | :--- |
| category\_name | string | + |
| category\_id | int | + |
| request\_content | string | + |
| request\_id | int | + |

## Create

{% api-method method="post" host="api" path="/admin/relations/:request\_id" %}
{% api-method-summary %}

{% endapi-method-summary %}

{% api-method-description %}
Создание связей, добавление категорий к запросу
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="request\_id" type="integer" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="category\_id" type="array" required=true %}
массив id категорий, которые хотим добавить к запросу
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{  
    "result" : 
    {
        "request_id" : 1,  
        "request_content" : "Сколько сейчас градусов",  
        "categories" : 
        [
            { 
                "category_id" : 1, 
                "category_name" : "Погода" 
            }, 
            { 
                "category_id" : 2, 
                "category_name" : "Информация" 
            }
        ] 
    },
    "error" : null
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

## 

