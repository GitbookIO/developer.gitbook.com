# OAuth

OAuth2 is a protocol that lets external applications request authorization to private details in a user's GitBook account without getting their password. This is preferred over Basic Authentication because tokens can be limited to specific types of data, and can be revoked by users at any time.

All developers need to [register their application](https://www.gitbook.com/@samypesse/settings/developers) before getting started. A registered OAuth application is assigned a unique Client ID and Client Secret. The Client Secret should not be shared.

You may create a personal access token for your own use or implement the web flow below to allow other users to authorize your application.

## Web Application Flow

This is a description of the OAuth2 flow from 3rd party web sites.

{% method %}
### 1. Redirect users to request GitBook access

The first step is to redirect the user to the authorization dialog, this dialog will ask user to grant access to your application.

{% sample lang="http" %}
```
GET https://api.gitbook.com/oauth/authorize
```

| Parameter | Type | Description |
| --------- | ---- | ----------- |
| `client_id` | `string` | **Required**. The client ID you received from GitBook when you registered. |
| `redirect_uri` | `string` | **Required**. The URL in your application where users will be sent after authorization. |
| `response_type` | `string` | Type of response expected, currently only valid value is `code` |

{% endmethod %}


{% method %}
### 2. GitBook redirects back to your site

If the user accepts your request, GitBook redirects back to your site with a temporary `code` in a code parameter as well as the `state` you provided in the previous step in a state parameter. If the states don't match, the request has been created by a third party and the process should be aborted.

You can exchange this code for an access token.

{% sample lang="http" %}
```
POST https://api.gitbook.com/oauth/access_token
```

###### Parameters

| Name | Type | Description |
| ---- | ---- | ----------- |
| `client_id` | `string` | **Required**. The client ID you received from GitBook when you registered. |
| `client_secret` | `string` | **Required**. The client secret you received from GitBook when you registered. |
| `code` | `string` | **Required**. The code you received as a response to Step 1. |
| `grant_type` | `string` | **Required**. `authorization_code` to exchange an oauth code |

###### Response

By default, the response will take the following form:

```
access_token=e72e16c7e42f292c6912e7710c838347ae178b4a&token_type=bearer
```

`access_token` can also be returned as JSON.
{% endmethod %}

{% method %}
### 3. Use the access token to access the API

The access token allows you to make requests to the API on a behalf of a user.

{% sample lang="http" %}
Include it in the Authorization header

```
Authorization: Bearer OAUTH-TOKEN
```

For example, in cUrl you can set the Authorization header like this:

```
$ curl -H "Authorization: Bearer OAUTH-TOKEN" https://api.gitbook.com/account
```
{% endmethod %}
