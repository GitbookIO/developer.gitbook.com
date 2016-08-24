# Contents

These API methods let you retrieve the contents of pages within a book.

It can be used to programmatically integrate your documentation content into your application.

{% method %}
## Get contents {#get}

This method returns the contents of a page in a book. All pages are ending with a `.json` extension.

See [Format](#format) for details about the output.

{% sample lang="http" %}
```
GET /book/:author/:book/contents/:file
```

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `file` | string | **Required:** Path of the file to retrieve (with .json extension) |
{% endmethod %}

{% method %}
## Get contents for a specific version {#get-version}

The Contents API can also serve other versions than the main one.

It can be used to retrieve contents for a specific Git tag, branch or commit.

See the [Versions API](./versions.md) for details on how to list versions.

{% sample lang="http" %}
```
GET /book/:author/:book/contents/v/:version/:file
```

##### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `version` | string | **Required:** SHA, Branch name or Tag |
| `file` | string | **Required:** Path of the file to retrieve (with .json extension) |
{% endmethod %}

## File format {#format}

The GitBook Contents API serve content of `JSON` build from the GitBook Toolchain. The format may vary between GitBook version being used to generate your book.

{% method %}
#### Version 2

Currently the default version, but soon to be deprecated.

{% sample lang="http" %}
##### Example

```js
{
    "progress": {
        ...
    },
    "sections": [
        {
            "type": "normal",
            "content": "<h1>My Awesome book</h1>"
        }
    ],
    "langs": []
}
```
{% endmethod %}

{% method %}
#### Version 3

This format is generated since GitBook `>=3.0.0`. It is a modern and easier format to work with.

Contents API can output all books with this format when the client accepts `application/vnd.gitbook.format.v3`:

{% sample lang="http" %}
```
curl -H "Accept: application/json;application/vnd.gitbook.format.v3" \
    "https://api.gitbook.com/book/you/your-book/contents/README.json"
```

##### Example

```js
{
    "page": {
        "title": "Introduction",
        "level": "1.1",
        "depth": 1,
        "next": {
            "title": "OAuth",
            "level": "1.2",
            "depth": 1,
            "path": "overview/oauth.md",
            "ref": "overview/oauth.md",
            "articles": []
        },
        "content": "<h1>....</h1> ..."
    },
    "file": {
        "path": "README.md",
        "mtime": "2016-08-22T21:58:34.000Z",
        "type": "markdown"
    },
    "version": "3"
}
```
{% endmethod %}
