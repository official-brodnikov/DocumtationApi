# Requests

{% hint style="info" %}
result - array\[object\] or object, optional
{% endhint %}

{% hint style="info" %}
error - string, optional
{% endhint %}

#### Responses schema

| Variable | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| id | int | + | Идентификатор запроса |
| content | string | + | Содержимое запроса |
| is\_marked\_up | bool | + | Размечен ли запрос \(default - false\) |
| categories | array\[object\] | - | Список категорий |
| categories\[i\].id | int | + | Идентификатор категории |
| categories\[i\].name | string | + | Название категории |

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
{% api-method-parameter name="per" type="integer" required=true %}
Количество элементов на странице \(по умолчанию - 25\)
{% endapi-method-parameter %}

{% api-method-parameter name="page" type="integer" required=true %}
Номер страницы пагинации \(по умолчанию - 1\)
{% endapi-method-parameter %}

{% api-method-parameter name="is\_marked\_up" type="boolean" required=false %}
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
    "result": [
        { 
            "id": 1,  
            "content": "Успею ли я написать курсовую до начала декабря?",   
            "is_marked_up": true,
            "categories": [
                { 
                    "id": 5, 
                    "name": "Образование"
                }, 
                { 
                    "id": 2, 
                    "name": "Поиск работы" 
                }
            ] 
        },
        {
            "id": 2, 
            "content": "Закажи пиццу",  
            "is_marked_up": false,
            "categories": []
        }
    ],
    "pagination": {
        "total_pages" : 3,
        "total_count": 100,
        "next_page": 2
    },
    "error": null 
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{ 
    "result": null,
    "pagination": null,
    "error": "The request could not be processed due to a syntax error."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

#### Responses schema

| Variable | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| result | object | - | Результат запроса |
| id | int | + | Идентификатор запроса |
| content | string | + | Содержимое запроса |
| is\_marked\_up | bool | + | Размечен ли запрос \(default - false\) |
| categories | array\[object\] | - | Список категорий |
| categories\[i\].id | int | + | Идентификатор категории |
| categories\[i\].name | string | + | Название категории |
| pagination | object | - | Пагинация |
| pagination.total\_pages | int | + | Колиество страниц |
| pagination.total\_count | int | + | Количество записей |
| pagination.next\_page | int | - | Следующая страница |
| error | string | - | Информация об ошибке |

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
    "result": {
        "id": 1,
        "content": "Сколько сейчас градусов",
        "is_marked_up": true,  
        "categories": [
            { 
                "id": 1, 
                "name": "Погода" 
            }, 
            { 
                "id": 2, 
                "name": "Информация" 
            }
        ] 
    },  
    "error": null
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{ 
    "result": null,
    "error": "The request could not be processed due to a syntax error."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

## Update

{% api-method method="put" host="api" path="/requests/:id" %}
{% api-method-summary %}
Category of Requests
{% endapi-method-summary %}

{% api-method-description %}
Разметить запрос
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
ID запроса, который будем размечать
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="category\_ids" type="array" required=true %}
Массив ID категорий, к которым мы хотим добавить запрос
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{  
     "result": {
          "id": 1,
          "content": "Какая сейчас температура",
          "is_marked_up": true, 
          "categories": [
               {
                    "id": 1,
                    "name": "Погода" 
               }
          ]
     },
     "error": null
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=302 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{ 
    "result": null,
    "error": "Request already marked up."
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{ 
    "result": null,
    "error": "The request could not be processed due to a syntax error."
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

