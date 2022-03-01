# MdbList Builders

You can find items using the features of [MdbList.com](https://mdblist.com/) (MdbList).

| Name                          | Attribute      | Description                                                               | Works with Movies | Works with Shows | Works with Playlists and Custom Sort |
|:------------------------------|:---------------|:--------------------------------------------------------------------------|:-----------------:|:----------------:|:------------------------------------:|
| [MdbList List](#mdblist-list) | `mdblist_list` | Gets every movie/show in a [MdbList List](https://mdblist.com/toplists/). |      &#9989;      |     &#9989;      |               &#9989;                |

## MdbList List

Finds every item in a [MdbList List](https://mdblist.com/toplists/).

The expected input is an MdbList List URL. Multiple values are supported as a list only a comma-separated string will not work.

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order.

```yaml
collections:
  Top Movies of The Week:
    mdblist_list: https://mdblist.com/lists/linaspurinis/top-watched-movies-of-the-week
    collection_order: custom
    sync_mode: sync
```
You can also limit the number of items to search for by using the `limit` and `url` parameters under `mdblist_list`.

```yaml
collections:
  Top 10 Movies of The Week:
    mdblist_list: 
      url: https://mdblist.com/lists/linaspurinis/top-watched-movies-of-the-week
      limit: 10
    collection_order: custom
    sync_mode: sync
```