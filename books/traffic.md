# Traffic

The Traffic API lets you fetch statistics about views and downloads.

{% method %}
## Get summary {#summary}

This methods returns a summary of traffic statistics.

{% sample lang="http" %}
```
GET /book/:author/:book/traffic
```

##### Response

```js
{
    views: 100,
    unique: 10,
    downloads: {
        pdf: 3,
        epub: 3,
        mobi: 1
    }
}
```

{% endmethod %}

{% method %}
## Get visits per countries {#countries}

This method returns the count of visits per countries.

{% sample lang="http" %}
```
GET /book/:author/:book/traffic/countries
```
{% endmethod %}

{% method %}
## Get visits per platforms {#platforms}

This method returns the count of visits per platforms.

{% sample lang="http" %}
```
GET /book/:author/:book/traffic/platforms
```
{% endmethod %}
