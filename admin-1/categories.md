# Requests

{% hint style="warning" %}
error - string, optional
{% endhint %}

{% hint style="warning" %}
result - array\[object\] or object, optional
{% endhint %}

#### Responses schema

| Variable | Type | Required |
| :--- | :--- | :--- |
| id | int | + |
| content | string | + |
| is\_marked\_up | bool | + |
| categories | array\[object\] | - |
| category\_id | int | + |
| category\_name | string | + |

## Read

{% api-method method="get" host="api" path="/admin/requests" %}
{% api-method-summary %}
All Requests
{% endapi-method-summary %}

{% api-method-description %}
Получение списка запросов
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="marked\_up" type="boolean" required=false %}
true - размеченные, false - неразмеченные, иначе все запросы
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
    [
        { 
            "id" : 1,  
            "content" : "Успею ли я написать курсовую до начала декабря?",   
            "is_marked_up" : true,
            "categories" : 
            [
                { 
                    "category_id" : 5, 
                    "category_name" : "Образование"
                }, 
                { 
                    "category_id" : 2, 
                    "category_name" : "Поиск работы" 
                }
            ] 
        },
        {
            "id" : 2, 
            "content" : "Закажи пиццу",  
            "is_marked_up" : false,
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

{% api-method method="get" host="api" path="/admin/requests/:request\_id" %}
{% api-method-summary %}
Request
{% endapi-method-summary %}

{% api-method-description %}
Получение конкретного запроса
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="request\_id" type="integer" required=true %}
ID запроса
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
        "content" : "Сколько сейчас градусов",  
        "is_marked_up" : true,
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

## Create

{% api-method method="post" host="api" path="/admin/requests" %}
{% api-method-summary %}
Request
{% endapi-method-summary %}

{% api-method-description %}
Создает новый запрос
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="request\_content" type="string" required=true %}
Содержимое запроса
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}
Cake successfully retrieved.
{% endapi-method-response-example-description %}

```
{  
    "result" :
    {
        "request_id" : 1, 
        "request_content" : "Какая погода сейчас",
        "is_marked_up" : false,
        "categories" : null 
    },
    "erorr" : null
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Could not find a cake matching this query
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

## Update

{% api-method method="put" host="api" path="/admin/requests/:request\_id" %}
{% api-method-summary %}
Request is not Marked up
{% endapi-method-summary %}

{% api-method-description %}
Делает запрос неразмеченным
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="request\_id" type="integer" required=true %}
ID запроса
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "result" : 
    { 
        "id" : 14, 
        "content" : "Подскажите курс валюты",
        "is_marked_up" : false
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

## Delete

{% api-method method="delete" host="api" path="/admin/requests/:request\_id" %}
{% api-method-summary %}
Request
{% endapi-method-summary %}

{% api-method-description %}
Удаляет выбранный запрос
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="request\_id" type="integer" required=true %}
ID запроса
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=204 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "result" : null,
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



