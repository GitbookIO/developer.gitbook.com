# GitBook API Reference

This documentation is intended to get you up-and-running with the GitBook APIs. We’ll cover everything you need to know, from authentication, to manipulating results, to combining results with other services.

The REST APIs provide programmatic access to read and write GitBook data. List books, edit content, proofread text, and more. The REST API identifies users using basic auth; responses are available in JSON.

{% method %}
## Schema

All API access is over HTTPS, and accessed through `https://api.gitbook.com`. All data is sent and received as **JSON**.

{% sample lang="http" %}
```
$ curl -i https://api.gitbook.com/author/gitbookio

HTTP/1.1 200 OK
Server: GitBook.com
Connection: keep-alive
Content-Type: application/json; charset=utf-8
Content-Length: 275
Etag: W/"113-25d22777"
Date: Thu, 11 Jun 2015 14:49:26 GMT
Via: 1.1 vegur

{ ... }
```

{% endmethod %}

{% method %}
## Authentication

While the API provides multiple methods for authentication, we strongly recommend using [OAuth](./auth/oauth.md) for production applications. The other methods provided are intended to be used for scripts or testing (i.e., cases where full OAuth would be overkill).

Third party applications that rely on GitBook for authentication should not ask for or collect GitBook credentials. Instead, they should use the OAuth web flow.

All API requests must be made over HTTPS. Calls made over plain HTTP will fail.

The API supports Basic Authentication as defined in [RFC2617](http://www.ietf.org/rfc/rfc2617.txt) with a few slight differences.

Requests that require authentication will return `404 Not Found`, instead of `403 Forbidden`, in some places. This is to prevent the accidental leakage of private books to unauthorized users.


{% sample lang="http" %}

##### Via Username and Password

To use Basic Authentication with the GitBook API, simply send the username and password associated with the account.

For example, if you’re accessing the API via cURL, the following command would authenticate you if you replace with your GitBook username. (cURL will prompt you to enter the password.)

Alternatively, you can use personal access tokens or OAuth tokens instead of your password.

```bash
$ curl -u <username>:<password or token> https://api.gitbook.com/account
```

##### Via OAuth Tokens

The access token allows you to make requests to the API on a behalf of a user.

```bash
$ curl -H "Authorization: token OAUTH-TOKEN" https://api.gitbook.com/account
```

{% endmethod %}


{% method %}
## Errors

GitBook uses conventional HTTP response codes to indicate the success or failure of an API request.

In general, codes in the `2xx` range indicate success, codes in the `4xx` range indicate an error that failed given the information provided (e.g., a required parameter was omitted, a charge failed, etc.), and codes in the `5xx` range indicate an error with Stripe's servers (these are rare).

Not all errors map cleanly onto HTTP response codes, however.

{% sample lang="http" %}

##### HTTP status code summary

| Status | Description |
| ------ | ----------- |
| `200 - OK` | Everything worked as expected. |
| `400 - Bad Request` | The request was unacceptable, often due to missing a required parameter. |
| `404 - Not Found` | The requested resource doesn't exist. |

##### Example Response

```js
{
    "error": "A human-readable message providing more details about the error.",
    "code": 400
}
```
{% endmethod %}

{% method %}
### Pagination {#pagination}

Requests that return multiple items will be paginated to 50 items by default.

You can specify further pages with the `?page` parameter. For some resources, you can also set a custom page size up to 100 with the `?limit`.

{% sample lang="http" %}
Paginated results will be returned with information about the page context.

```js
{
    list: [ ... ],
    page: 0,
    limit: 50,
    total: 0
}
```
{% endmethod %}

### Enterprise

All API endpoints are prefixed with the following URL: `http(s)://hostname/api/`.
