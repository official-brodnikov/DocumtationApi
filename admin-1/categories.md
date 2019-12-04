# Requests

{% hint style="warning" %}
error - string, optional
{% endhint %}

{% hint style="warning" %}
result - array\[object\] or object, optional
{% endhint %}

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
            "request_id" : 1,  
            "request_content" : "Успею ли я написать курсовую до начала декабря?",   
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
            "request_id" : 2, 
            "request_content" : "Закажи пиццу",  
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
| is\_marked\_up | bool | + |

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
        "request_content" : "Какая погода сейчас" 
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
| request\_content | string | + |
| request\_id | int | + |

## Update

{% api-method method="put" host="api" path="/admin/requests/marked\_up/:request\_id" %}
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
        "request_id" : 14, 
        "request_content" : "Подскажите курс валюты"
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
    "result" : {},
    "error" : "The request could not be processed due to a syntax error." 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Responses schema

| Variable | Type | Requiered |
| :--- | :--- | :--- |
| request\_id | int | + |
| request\_content | string | + |

{% api-method method="put" host="api" path="/admin/requests/:request\_id/category" %}
{% api-method-summary %}
Category of request
{% endapi-method-summary %}

{% api-method-description %}
Удаляет выбранную категорию у запроса
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="request\_id" type="integer" required=true %}
ID запроса
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="category\_id" type="integer" required=false %}
 ID категории
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "result" : 
    { 
        "request_id" : 13, 
        "request_content" : "Какого числа празднуется День Матери", 
        "categories" : 
        [
            { 
                "category_id" : 6, 
                "category_name" : "Праздники"
            },
            {
                "category_id" : 19, 
                "category_name" : "Родители"
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
    "result" : {},
    "error" : "The request could not be processed due to a syntax error." 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Responses schema

| Variable | Type | Requiered |
| :--- | :--- | :--- |
| request\_id | int | + |
| request\_content | string | + |
| categories | array\[object\] | - |
| category\_id | integer | + |
| category\_name | string | + |

{% api-method method="put" host="api" path="/admin/requests/:request\_id/new\_category" %}
{% api-method-summary %}
New category for requests
{% endapi-method-summary %}

{% api-method-description %}
Добавляет новую категорию к запросу
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="request\_id" type="integer" required=true %}
ID запроса
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="category\_id" type="integer" required=false %}
ID категории
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "result" : 
    { 
        "request_id" : 13, 
        "request_content" : "Какого числа празднуется День Матери", 
        "categories" : 
        [
            { 
                "category_id" : 6, 
                "category_name" : "Праздники"
            },
            {
                "category_id" : 19, 
                "category_name" : "Родители"
            },
            {
                "category_id" : 15, 
                "category_name" : "Выходные"    
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
    "result" : {},
    "error" : "The request could not be processed due to a syntax error." 
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Responses schema

| Variable | Type | Requiered |
| :--- | :--- | :--- |
| request\_id | int | + |
| request\_content | string | + |
| categories | array\[object\] | - |
| category\_id | integer | + |
| category\_name | string | + |

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
    "result" : "Request completed successfully.",
    "error" : null
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "result" : "",
    "error" : "The request could not be processed due to a syntax error."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}



