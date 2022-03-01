# Notifiarr Attributes

Configuring [Notifiarr](https://notifiarr.com) is optional but can allow you to send the webhooks straight to notifiarr.

A `notifiarr` mapping is in the root of the config file.

Below is a `notifiarr` mapping example and the full set of attributes:
```yaml
notifiarr:
  apikey: ####################################
```

| Name    | Attribute | Allowed Values    | Default | Required |
|:--------|:----------|:------------------|:-------:|:--------:|
| API Key | `apikey`  | Notifiarr API Key |   N/A   | &#9989;  |

Once you have added the apikey your config.yml you have to add `notifiarr` to any webhook to send that notification to Notifiarr.

```yaml
webhooks:
  error: notifiarr
  run_start: notifiarr
  run_end: notifiarr
  collection_changes: notifiarr
```
