# OMDb Attributes

Configuring [OMDb](https://www.omdbapi.com/) is optional but can allow you to mass edit metadata using IMDb.

A `omdb` mapping is in the root of the config file.

Below is a `omdb` mapping example and the full set of attributes:
```yaml
omdb:
  apikey: ########
```

| Name    | Attribute | Allowed Values | Default | Required |
|:--------|:----------|:---------------|:-------:|:--------:|
| API Key | `apikey`  | OMDb API Key   |   N/A   | &#9989;  |

* The OMDb apikey can be generated [here](http://www.omdbapi.com/apikey.aspx).

* The free apikey is limited to 1000 requests per day so if you hit your limit the program should be able to pick up where it left off the next day as long as the `cache` option is enabled 
