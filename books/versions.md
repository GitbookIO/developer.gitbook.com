# Versions

The versions API can be used to list available versions of a book (branches, tags or commits). The [Contents API](./contents.md#get-version) can then be used to fetch files for a specific version.

See [Format](#format) for details about the version object format.

The [Versions](https://plugins.gitbook.com/plugin/versions) plugins can be enabled to list versions of the book in the sidebar.

{% method %}
## List branches {#branches}

This method returns the list of active branches in the book's git repository.


{% sample lang="http" %}
```
GET /book/:author/:book/versions/branches
```
{% endmethod %}

{% method %}
## List tags {#tags}

This method returns the list of Git tags in the book's git repository.

{% sample lang="http" %}
```
GET /book/:author/:book/versions/tags
```
{% endmethod %}

{% method %}
## List languages {#languages}

For multilingual book, this method returns the list of languages.

{% sample lang="http" %}
```
GET /book/:author/:book/versions/languages
```
{% endmethod %}

{% method %}
## Version Format {#format}

Each version (Tag, Branch or Language) is represented by a version object.

The `current` is set to true when its represent the main version (current branch, current language, etc).

{% common %}
```js
{
    "name": "master",
    "urls": {
        "website": "https://samypesse.gitbooks.io/how-to-create-an-operating-system/content/",
        "epub":    "https://www.gitbook.com/download/epub/book/samypesse/how-to-create-an-operating-system/",
        "pdf":     "https://www.gitbook.com/download/pdf/book/samypesse/how-to-create-an-operating-system/",
        "mobi":    "https://www.gitbook.com/download/mobi/book/samypesse/how-to-create-an-operating-system/"
    },
    "current": true
}
```
{% endmethod %}
