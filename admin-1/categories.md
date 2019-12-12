# Requests

{% hint style="info" %}
result - array\[object\] or object, optional
{% endhint %}

{% hint style="info" %}
pagination - object, optional
{% endhint %}

{% hint style="info" %}
error - string, optional
{% endhint %}

#### Responses schema

| Variable | Type | Required |
| :--- | :--- | :--- |
| id | int | + |
| content | string | + |
| is\_marked\_up | bool | + |
| categories | array\[object\] | - |
| categories\[i\].id | int | + |
| categories\[i\].name | string | + |
| total\_pages | int | + |
| total\_count | int | + |
| next\_page | int | - |

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
{% api-method-parameter name="is\_marked\_up" type="boolean" required=false %}
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
                    "id" : 5, 
                    "name" : "Образование"
                }, 
                { 
                    "id" : 2, 
                    "name" : "Поиск работы" 
                }
            ] 
        },
        {
            "id" : 2, 
            "content" : "Закажи пиццу",  
            "is_marked_up" : false,
            "categories" : []
        }
    ],
    "pagination" :
    {
        "total_page" : 6,
        "total_count": 3,
        "next_page": 7
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
    "pagination" : null,
    "error" : "The request could not be processed due to a syntax error."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="api" path="/admin/requests/:id" %}
{% api-method-summary %}
Request
{% endapi-method-summary %}

{% api-method-description %}
Получение конкретного запроса
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="integer" required=true %}
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
                "id" : 1, 
                "name" : "Погода" 
            }, 
            { 
                "id" : 2, 
                "name" : "Информация" 
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
{% api-method-parameter name="category\_ids" type="array" required=false %}
Массив id категорий
{% endapi-method-parameter %}

{% api-method-parameter name="content" type="string" required=true %}
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
        "id" : 1, 
        "content" : "Какая погода сейчас",
        "is_marked_up" : false,
        "categories" : []
    },
    "error" : null
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

{% api-method method="put" host="api" path="/admin/requests/:id" %}
{% api-method-summary %}
Request Replasement
{% endapi-method-summary %}

{% api-method-description %}
Изменение запроса
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="integer" required=true %}
ID запроса
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="category\_ids" type="array" required=false %}
Массив id категорий для изменения
{% endapi-method-parameter %}

{% api-method-parameter name="content" type="string" required=false %}
Содержимое запроса
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
        "id" : 14, 
        "content" : "Подскажите курс валюты",
        "is_marked_up" : false,
        "categories" : null
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

{% api-method method="delete" host="api" path="/admin/requests/:id" %}
{% api-method-summary %}
Request
{% endapi-method-summary %}

{% api-method-description %}
Удаляет выбранный запрос
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="integer" required=true %}
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



