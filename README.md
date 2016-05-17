# GitBook API clients

The different GitBook API clients let you easily communicate with the GitBook API ([https://www.gitbook.com](https://www.gitbook.com)) using Node or GoLang.


{% method -%}
## Install

The first thing is to get the GitBook API client.

{% sample lang="js" -%}
```bash
$ npm install gitbook-api
```

{% sample lang="go" -%}
```bash
$ go get github.com/GitbookIO/go-gitbook-api
```
{% endmethod %}


{% method -%}
## Load

Include the library.

{% sample lang="js" -%}
```js
var Gitbook = require('gitbook-api');
```

{% sample lang="go" -%}
```go
package main

import "github.com/GitbookIO/go-gitbook-api"
```
{% endmethod %}



## Examples

{% method -%}
### Create a client

To create a client, you can provide many options.

The default client will not use authentication and will point to the gitbook.com API endpoint [https://api.gitbook.com](https://api.gitbook.com).

To authenticate, you can either use your GitBook's username/password combination or provide only your oAuth token.

The clients are compatible with GitBook Enterprise by providing a different host for the API endpoint.

{% common -%}
Create a client with default options.

{% sample lang="js" -%}
```js
var client = new Gitbook();
```

{% sample lang="go" -%}
```go
api := gitbook.NewAPI(gitbook.APIOptions{})
```

{% common -%}
Create an API client with an authentified user:

{% sample lang="js" -%}
```js
var client = new GitBook({
    username: 'MyUsername',
    token: 'password'
});
```

{% sample lang="go" -%}
```go
api := gitbook.NewAPI(gitbook.APIOptions{
    Username: "username",
    Password: "password",
})
```

{% common -%}
Or using an oauth token:

{% sample lang="js" -%}
```js
var client = new GitBook({
    token: 'oauth token'
});
```

{% sample lang="go" -%}
```go
api := gitbook.NewAPI(gitbook.APIOptions{
    Password: "oauth token",
})
```

{% common -%}
You can use the API client with a GitBook Enterprise instance by simply adding a host option.

{% sample lang="js" -%}
```js
var client = new GitBook({
    host: 'http://gitbook.mycompany.com'
});
```

{% sample lang="go" -%}
```go
api := gitbook.NewAPI(gitbook.APIOptions{
    // Custom host instead of "https://api.gitbook.com"
    Host: "http://gitbook.mycompany.com",
})
```
{% endmethod %}


{% method -%}
### List books

{% common -%}
List books from the authenticated user:

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
### Get a specific book

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


{% method -%}
### Get details about an author

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