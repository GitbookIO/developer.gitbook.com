# Access Keys

Access keys allow non-collaborator to access a private book. Each access key can be converted to an unique read-only access url.

{% method %}
## Create an access key {#create}

Create a new book for the specified author.

{% sample lang="http" %}
```
POST /book/:author/:book/keys
```

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `label` | string | **Required:** Label to identify the key |
| `key` | string | Optional value of the key, if not provided it'll be set as a random string |
{% endmethod %}

{% method %}
## List access keys for a book {#list}

{% sample lang="http" %}
```
GET /book/:author/:book/keys/
```

##### Example Response

```js
{
    "list": [
        {
            "id": "564c97a917c24e09ddd8b765",
            "label": "For Aaron",
            "key": "aaron_private_key",
            "active": true,
            "dates": {
                "created": "2015-11-19T12:22:27.765Z",
                "updated": "2015-11-19T12:22:27.765Z"
            }
        }
        ...
    ],
    "total": 15,
    "limit": 10,
    "page": 0
}
```
{% endmethod %}
