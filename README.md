# GitBook API clients

The different GitBook API clients let you easily communicate with the GitBook API ([https://www.gitbook.com](https://www.gitbook.com)) using Node or GoLang.


{% method -%}
## Install {#install}

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
### Create a client {#create-client}

To create a client, you can provide many options.

To authenticate, you can either use your GitBook's username/password combination or provide only your oAuth token.

The default client will not use authentication and will point to the gitbook.com API endpoint [https://api.gitbook.com](https://api.gitbook.com).

The clients are compatible with GitBook Enterprise by providing a different host for the API endpoint.

{% common -%}
###### With default options

{% sample lang="js" -%}
```js
var Gitbook = require('gitbook-api');
var client = new Gitbook();
```

{% sample lang="go" -%}
```go
package main

import "github.com/GitbookIO/go-gitbook-api"

func main() {
    api := gitbook.NewAPI(gitbook.APIOptions{})
}
```

{% common -%}
###### With an authentified user

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
###### Using an oauth token

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
###### Pointing to a different host

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
