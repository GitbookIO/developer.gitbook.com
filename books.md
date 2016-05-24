{% method -%}
### List books {#list}

List books from the authenticated user.

{% sample lang="js" -%}
```js
client.books()
.then(function(page) {
    // page.list: list of books
    // page.total: total count of books

    // Fetch next page
    return page.next();
}, function(err) {
    // Error occured
});
```

{% sample lang="go" -%}
```go
// Get list of books
books, err := api.Books.List()

// Print results
fmt.Printf("books = %q\n", books)
fmt.Printf("error = %q\n", err)
```
{% endmethod %}


{% method -%}
### Get a specific book {#get}

Get details about a book given its `id` in the form `<username>/<bookId>`.

{% sample lang="js" -%}
```js
var book = client.book("GitBookIO/javascript");
book.details().then(function(infos) { ... });
```

{% sample lang="go" -%}
```go
// Get book
book, err := api.Book.Get("GitBookIO/javascript")
```
{% endmethod %}
