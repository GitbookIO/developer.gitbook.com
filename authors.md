{% method -%}
### Get details about an author {#get}

Get details about an author given its username.

{% sample lang="js" -%}
```js
var author = client.author("GitBookIO");
author.then(function(infos) { ... });
```

{% sample lang="go" -%}
```go
// Get author
author, err := api.Author.Get("GitBookIO")
```
{% endmethod %}