# Admin

{% hint style="warning" %}
error - string, optional

result - array\[object\] or object, optional
{% endhint %}

## Categories

### Create

{% api-method method="post" host="api" path="/admin/requests?category\_name=<<category\_name>>" %}
{% api-method-summary %}
 New Category
{% endapi-method-summary %}

{% api-method-description %}
Создает новую категорию
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="category\_name" type="string" required=true %}
Название категории
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
        "category_id" : 1, 
        "category_name" : "Кино" 
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
| category\_id | integer | + |
| category\_name | string | + |

### Update

{% api-method method="put" host="api" path="/admin/requests/:category\_id?category\_name=<<category\_name>>" %}
{% api-method-summary %}
Category Replacement
{% endapi-method-summary %}

{% api-method-description %}
Изменение категории
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="category\_id" type="integer" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="category\_name" type="string" required=true %}
Новое название категории
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
        "category_id" : 15,
        "category_name" : "Спорт"
    },
    "error" : null
}
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=201 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{
    "result" :
    {
        "category_id" : 1,
        "category_name" : "Спорт"
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
| category\_id | integer | + |
| category\_name | string | + |

### Delete

{% api-method method="delete" host="api" path="/admin/requests/:category\_id" %}
{% api-method-summary %}
Category
{% endapi-method-summary %}

{% api-method-description %}
Удаление категории по идентификатору
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="category\_id" type="integer" required=true %}
Идентификатор нужной категории
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

#### Responses schema

| Variable | Type | Requiered |
| :--- | :--- | :--- |
| result | string | - |
| error | string | - |

## Requests

### Update

{% api-method method="put" host="api" path="/admin/requests/:request\_id" %}
{% api-method-summary %}
Request is not Marked Up
{% endapi-method-summary %}

{% api-method-description %}
Сделать выбранный запрос неразмеченным
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

{% api-method method="put" host="api" path="/admin/requests/:request\_id?category\_id=<<categoty\_id>>" %}
{% api-method-summary %}
Request Category
{% endapi-method-summary %}

{% api-method-description %}
Удаляет выбранную категорию у запроса
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="request\_id" type="integer" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="category\_id" type="integer" required=false %}
Идентификаторы категорий
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

{% api-method method="put" host="api" path="/admin/requests/:request\_id?category\_id=<<category\_id>>" %}
{% api-method-summary %}
New Category for Marked Up Request
{% endapi-method-summary %}

{% api-method-description %}
Добавление категорий размеченному запросу
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="request\_id" type="integer" required=false %}
Индентификатор запроса 
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="category\_id" type="integer" required=false %}
Идентификаторы категорий для добавления
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

### Delete

{% api-method method="delete" host="api" path="/admin/requests/:request\_id" %}
{% api-method-summary %}
Request
{% endapi-method-summary %}

{% api-method-description %}
Удаляет запрос по его идентификатору
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="request\_id" type="object" required=true %}
Идентификатор запроса
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

#### Responses schema

| Variable | Type | Requiered |
| :--- | :--- | :--- |
| result | string | - |
| error | string | - |



 

