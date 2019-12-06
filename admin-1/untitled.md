# Categories

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
| name | string | + |

## Read

{% api-method method="get" host="api" path="/admin/categories" %}
{% api-method-summary %}
All Category
{% endapi-method-summary %}

{% api-method-description %}
Получить список категорий
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

{% api-method method="get" host="api" path="/admin/categories/:id" %}
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
ID категории
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

## Create

{% api-method method="post" host="api" path="/admin/categories" %}
{% api-method-summary %}
New Category
{% endapi-method-summary %}

{% api-method-description %}
Создание новой категории
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="name" type="string" required=true %}
Название категори
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
        "id" : 8, 
        "name" : "Кино" 
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

## Update

{% api-method method="put" host="api" path="/admin/categories/:id" %}
{% api-method-summary %}
Category Replacement
{% endapi-method-summary %}

{% api-method-description %}
Изменение имени категории
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="integer" required=true %}

{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-query-parameters %}
{% api-method-parameter name="name" type="string" required=true %}
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
        "id" : 1,
        "name" : "Спорт"
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

{% api-method method="delete" host="api" path="/admin/categories/:id" %}
{% api-method-summary %}
Category
{% endapi-method-summary %}

{% api-method-description %}
Удаление категории по id
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="integer" required=true %}

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

