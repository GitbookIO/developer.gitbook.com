# Authors

The Authors API let you access details of users and organizations.

{% method %}
## Get a single author {#get}

This method returns the details about a specific author.

See [Format](#format) for details about the output.

{% sample lang="http" %}
```
GET /authors/:username
```
{% endmethod %}

{% method %}
## List user organizations {#list-orgs}

This [paginated](../README.md#pagination) method list public organization memberships for the specified user.

{% sample lang="http" %}
```
GET /authors/:username/orgs
```
{% endmethod %}
