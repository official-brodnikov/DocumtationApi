# Requests

{% hint style="warning" %}
error - string, optional
{% endhint %}

{% hint style="warning" %}
result - array\[object\] or object, optional
{% endhint %}

## Read

{% api-method method="get" host="api" path="/requests" %}
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
если true, то размеченные,  false неразмеченные, иначе все
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
    "result" : null,
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

{% api-method method="get" host="api" path="/requests/:id" %}
{% api-method-summary %}
Request
{% endapi-method-summary %}

{% api-method-description %}
Получить конкретный запрос
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

#### Responses schema

| Variable | Type | Required |
| :--- | :--- | :--- |
| category\_name | string | + |
| category\_id | int | + |
| request\_content | string | + |
| request\_id | int | + |

## Update

{% api-method method="put" host="api" path="/requests/:request\_id" %}
{% api-method-summary %}
Category of Requests
{% endapi-method-summary %}

{% api-method-description %}
Разметить запрос
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="request\_id" type="string" required=true %}
id запроса, который будем размечать
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="category\_id" type="array" required=true %}
массив id категорий, к которым мы хотим добавить запрос
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
          "request_id" : 1,
          "request_content" : "Какая сейчас температура",
          "is_marked_up" : true, 
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
    "result" : null,
    "error" : "Request already marked up."
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

#### Responses schema

| Variable | Type | Required |
| :--- | :--- | :--- |
| category\_name | string | + |
| category\_id | int | + |
| request\_content | string | + |
| request\_id | int | + |
| is\_marked\_up | bool | + |

