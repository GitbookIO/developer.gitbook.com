# Books

{% method %}
## List your books {#list}

List books that are accessible to the authenticated user.

This includes books owned by the authenticated user, books where the authenticated user is a collaborator, and books that the authenticated user has access to through an organization membership.

{% sample lang="http" %}
```
GET /books
```

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| page | number | Index of current page |
{% endmethod %}


{% method %}
## List author books {#list-author}

List public books for the specified user/organization.

{% sample lang="http" %}
```
GET /authors/:username/books
```

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| page | number | Index of current page |
{% endmethod %}

{% method %}
## List all public books {#list-all}

This provides a dump of every public repository, in the order that they were created.

{% sample lang="http" %}
```
GET /books/all
```

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| page | number | Index of current page |
{% endmethod %}

{% method %}
## Create a book {#create}

Create a new book for the specified author.

{% sample lang="http" %}
```
POST /books
```

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `author` | string | **Required:** Username of the owner |
| `title` | string | **Required:** The title of the book |
| `description` | string | The description of the book |
{% endmethod %}


{% method %}
## Get a book {#get}

Get details about a book.

{% sample lang="http" %}
```
GET /book/:username/:name
```

##### Example Response

```js
{
    "id": "johndoe/mybook",
    "title": "My Book"
}
```
{% endmethod %}
