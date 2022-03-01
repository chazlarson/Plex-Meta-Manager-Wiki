# StevenLu Builders

You can find items using StevenLu's Popular Movies list on [StevenLu.com](https://movies.stevenlu.com/) (StevenLu). 

No configuration is required for this builder.

| Name                                                             | Attribute          | Description                                                                          | Works with Movies | Works with Shows | Works with Playlists and Custom Sort |
|:-----------------------------------------------------------------|:-------------------|:-------------------------------------------------------------------------------------|:-----------------:|:----------------:|:------------------------------------:|
| [StevenLu's Popular Movies List](#stevenlus-popular-movies-list) | `stevenlu_popular` | Finds every movie on [StevenLu's Popular Movies List](https://movies.stevenlu.com/). |      &#9989;      |     &#10060;     |               &#9989;                |

## StevenLu's Popular Movies List

Finds every movie on [StevenLu's Popular Movies List](https://movies.stevenlu.com/).

The expected input is `true`.

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  StevenLu's Popular Movies:
    stevenlu_popular: true
    collection_order: custom
    sync_mode: sync
```
