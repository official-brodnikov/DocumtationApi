# Requests

{% hint style="warning" %}
error - string, optional
{% endhint %}

{% hint style="warning" %}
result - array\[object\] or object, optional
{% endhint %}

## Create

{% api-method method="post" host="api" path="/requests/:request\_content" %}
{% api-method-summary %}
Request
{% endapi-method-summary %}

{% api-method-description %}
Создать новый запрос
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="request\_content" type="string" required=true %}
Содержимое запроса
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

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
| request\_content | string | + |
| request\_id | int | + |

## Read

{% api-method method="get" host="api" path="/requests/:id" %}
{% api-method-summary %}
Marked Up
{% endapi-method-summary %}

{% api-method-description %}
Получить запрос и все его категории
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

{% api-method method="get" host="api" path="/requests?marked\_up=<<marked\_up>>" %}
{% api-method-summary %}
All not Marked Up Requests
{% endapi-method-summary %}

{% api-method-description %}
Получить все неразмеченные запросы
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="marked\_up" type="boolean" required=true %}

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
        },
        {
            "request_id" : 2, 
            "request_content" : "Закажи пиццу",  
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
| request\_content | string | + |
| request\_id | int | + |

{% api-method method="get" host="api" path="/requests?marked\_up=<<marked\_up>>" %}
{% api-method-summary %}
All Marked Up Requests
{% endapi-method-summary %}

{% api-method-description %}
Получить все размеченные запросы
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="marked\_up" type="boolean" required=true %}

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
            "categories" : 
            [
                { 
                    "category_id" : 3, 
                    "category_name" : "Заказ еды" 
                }, 
                { 
                    "category_id" : 4, 
                    "category_name" : "Медицина" 
                }
            ] 
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

{% api-method method="get" host="api" path="/requests" %}
{% api-method-summary %}
All Requests
{% endapi-method-summary %}

{% api-method-description %}
Получить все запросы
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
            "request_id" : 1,  
            "request_content" : "Успею ли я написать курсовую до начала декабря?",   
            "is_marked_up" : true
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
            "is_marked_up" : false
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

## Update

{% api-method method="put" host="api" path="/requests/:category\_id?request\_id=<<request\_id>>" %}
{% api-method-summary %}
Category of Requests
{% endapi-method-summary %}

{% api-method-description %}
Добавить категорию к неразмеченному запросу
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="category\_id" type="integer" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="request\_id" type="integer" required=true %}

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
          "request_content" : "Какая сейчас температура", 
          "categories" : 
          [
               {
                    "category_id" : 1,
                    "category_name" : "Погода" 
               }
          ]
     },
     "error" : null
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=302 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{ 
    "result" : {},
    "error" : "Request already marked up."
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

