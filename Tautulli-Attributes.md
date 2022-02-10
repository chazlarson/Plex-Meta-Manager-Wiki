Configuring [Tautulli](https://tautulli.com/) is optional but can allow you to create Collections based on Tautulli's Watch Statistics.

A `tautulli` mapping can be either in the root of the config file as global mapping for all libraries or you can specify the `tautulli` mapping individually per library.

Below is a `tautulli` mapping example and the full set of attributes:
```yaml
tautulli:
  url: http://192.168.1.12:8659
  apikey: ################################
```

| Name         | Attribute | Allowed Values                                        | Default |      Required      |
|:-------------|:----------|:------------------------------------------------------|:-------:|:------------------:|
| Tautulli URL | `url`     | Tautulli URL<br>**Example:** http://192.168.1.12:8659 |   N/A   | :heavy_check_mark: |
| API Key      | `apikey`  | Tautulli API Key                                      |   N/A   | :heavy_check_mark: |

* The apikey can be found by going to Tautulli > Settings > Web Interface > API > API Key