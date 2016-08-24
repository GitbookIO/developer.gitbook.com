# Discussions

The Discussion API lets you create, list and comment discussions in books.

{% method %}
## List discussions for a book {#list}

List all opened discussions in a book, all or closed discussions can be listed using the `state` parameter.

This method is [paginated](../README.md#pagination).

{% sample lang="http" %}
```
GET /book/:author/:book/discussions
```

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `state` | string | State of the discussions (`open`, `closed` or `all`), default is `open` |
| `filename` | string | Optional file to filter discussions |
{% endmethod %}

{% method %}
## Create a new discussion {#create}

Any user with read access can create a discussion.

{% sample lang="http" %}
```
POST /book/:author/:book/discussions
```

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `title` | string | **Required**. Title of the discussion. |
| `body` | string | The contents of the discussion. |
{% endmethod %}
