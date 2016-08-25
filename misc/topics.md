# Topics

{% method %}
## List topics

List all topics in GitBook sorted by the count of books.

{% sample lang="http" %}
```
GET /topics
```

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `q` | `string` | The search keywords, as well as any qualifiers. |


##### Response

```js
{
    "list": [
        {
            "id": "programming",
            "name": "Programming",
            "books": 320
        }
        ...
    ],
    "total": 76,
    "limit": 10,
    "page": 0
}
```
{% endmethod %}

{% method %}
#### Get a single topic

{% sample lang="http" %}
```
GET /topic/:id
```
{% endmethod %}
