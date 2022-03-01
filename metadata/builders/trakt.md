# Trakt Builders

You can find items using the features of [Trakt.tv](https://trakt.tv/) (Trakt). 

[Configuring Trakt](../../config/trakt) in the config is required for any of these builders.

| Name                                             | Attribute                   | Description                                                                                                                                                          | Works with Movies | Works with Shows | Works with Playlists and Custom Sort |
|:-------------------------------------------------|:----------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------:|:----------------:|:------------------------------------:|
| [Trakt List](#trakt-list)                        | `trakt_list`                | Finds every item in the Trakt List                                                                                                                                   |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt List Details](#trakt-list)                | `trakt_list_details`        | Finds every item in the Trakt List and updates the collection summary with the list description                                                                      |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt User Watchlist](#trakt-user-watchlist)    | `trakt_watchlist`           | Finds every item in a Users Watchlist                                                                                                                                |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt User Collection](#trakt-user-collection)  | `trakt_collection`          | Finds every item in a Users Collection                                                                                                                               |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Trending](#trakt-trending)                | `trakt_trending`            | Finds the movies/shows in Trakt's Trending [Movies](https://trakt.tv/movies/trending)/[Shows](https://trakt.tv/shows/trending) list                                  |      &#9989;      |     &#9989;      |               &#9989;                | 
| [Trakt Popular](#trakt-popular)                  | `trakt_popular`             | Finds the movies/shows in Trakt's Popular [Movies](https://trakt.tv/movies/popular)/[Shows](https://trakt.tv/shows/popular) list                                     |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Recommended Daily](#trakt-recommended)    | `trakt_recommended_daily`   | Finds the movies/shows in Trakt's Daily Recommended [Movies](https://trakt.tv/movies/recommended/daily)/[Shows](https://trakt.tv/shows/recommended/daily) list       |      &#9989;      |     &#9989;      |               &#9989;                | 
| [Trakt Recommended Weekly](#trakt-recommended)   | `trakt_recommended_weekly`  | Finds the movies/shows in Trakt's Weekly Recommended [Movies](https://trakt.tv/movies/recommended/weekly)/[Shows](https://trakt.tv/shows/recommended/weekly) list    |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Recommended Monthly](#trakt-recommended)  | `trakt_recommended_monthly` | Finds the movies/shows in Trakt's Monthly Recommended [Movies](https://trakt.tv/movies/recommended/monthly)/[Shows](https://trakt.tv/shows/recommended/monthly) list |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Recommended Yearly](#trakt-recommended)   | `trakt_recommended_yearly`  | Finds the movies/shows in Trakt's Yearly Recommended [Movies](https://trakt.tv/movies/recommended/yearly)/[Shows](https://trakt.tv/shows/recommended/yearly) list    |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Recommended All-Time](#trakt-recommended) | `trakt_recommended_all`     | Finds the movies/shows in Trakt's All-Time Recommended [Movies](https://trakt.tv/movies/recommended/all)/[Shows](https://trakt.tv/shows/recommended/all) list        |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Watched Daily](#trakt-watched)            | `trakt_watched_daily`       | Finds the movies/shows in Trakt's Daily Watched [Movies](https://trakt.tv/movies/watched/daily)/[Shows](https://trakt.tv/shows/watched/daily) list                   |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Watched Weekly](#trakt-watched)           | `trakt_watched_weekly`      | Finds the movies/shows in Trakt's Weekly Watched [Movies](https://trakt.tv/movies/watched/weekly)/[Shows](https://trakt.tv/shows/watched/weekly) list                |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Watched Monthly](#trakt-watched)          | `trakt_watched_monthly`     | Finds the movies/shows in Trakt's Monthly Watched [Movies](https://trakt.tv/movies/watched/monthly)/[Shows](https://trakt.tv/shows/watched/monthly) list             |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Watched Yearly](#trakt-watched)           | `trakt_watched_yearly`      | Finds the movies/shows in Trakt's Yearly Watched [Movies](https://trakt.tv/movies/watched/yearly)/[Shows](https://trakt.tv/shows/watched/yearly) list                |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Watched All-Time](#trakt-watched)         | `trakt_watched_all`         | Finds the movies/shows in Trakt's All-Time Watched [Movies](https://trakt.tv/movies/watched/all)/[Shows](https://trakt.tv/shows/watched/all) list                    |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Collected Daily](#trakt-collected)        | `trakt_collected_daily`     | Finds the movies/shows in Trakt's Daily Collected [Movies](https://trakt.tv/movies/collected/daily)/[Shows](https://trakt.tv/shows/collected/daily) list             |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Collected Weekly](#trakt-collected)       | `trakt_collected_weekly`    | Finds the movies/shows in Trakt's Weekly Collected [Movies](https://trakt.tv/movies/collected/weekly)/[Shows](https://trakt.tv/shows/collected/weekly) list          |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Collected Monthly](#trakt-collected)      | `trakt_collected_monthly`   | Finds the movies/shows in Trakt's Monthly Collected [Movies](https://trakt.tv/movies/collected/monthly)/[Shows](https://trakt.tv/shows/collected/monthly) list       |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Collected Yearly](#trakt-collected)       | `trakt_collected_yearly`    | Finds the movies/shows in Trakt's Yearly Collected [Movies](https://trakt.tv/movies/collected/yearly)/[Shows](https://trakt.tv/shows/collected/yearly) list          |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Collected All-Time](#trakt-collected)     | `trakt_collected_all`       | Finds the movies/shows in Trakt's All-Time Collected [Movies](https://trakt.tv/movies/collected/all)/[Shows](https://trakt.tv/shows/collected/all) list              |      &#9989;      |     &#9989;      |               &#9989;                |
| [Trakt Box Office](#trakt-box-office)            | `trakt_boxoffice`           | Finds the 10 movies in Trakt's Top Box Office [Movies](https://trakt.tv/movies/boxoffice) list                                                                       |      &#9989;      |     &#10060;     |               &#9989;                |

## Trakt List

Finds every item in the Trakt List.

The expected input is a Trakt List URL. Multiple values are supported as either a list or a comma-separated string.

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Christmas:
    trakt_list:
      - https://trakt.tv/users/movistapp/lists/christmas-movies
      - https://trakt.tv/users/2borno2b/lists/christmas-movies-extravanganza
    sync_mode: sync
```
```yaml
collections:
  Reddit Top 250:
    trakt_list: https://trakt.tv/users/jay-greene/lists/reddit-top-250-2019-edition
    collection_order: custom
    sync_mode: sync
```

* You can update the collection details with the Trakt List's description by using `trakt_list_details`.
* You can specify multiple collections in `trakt_list_details` but it will only use the first one to update the collection summary.

```yaml
collections:
  Reddit Top 250:
    trakt_list_details: https://trakt.tv/users/jay-greene/lists/reddit-top-250-2019-edition
    collection_order: custom
    sync_mode: sync
```

## Trakt User Watchlist

Finds every item in a Users Watchlist.

The expected input is a user's Trakt Username or `me`. Multiple values are supported as either a list or a comma-separated string.

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Trakt Watchlist:
    trakt_watchlist: me
    collection_order: custom
    sync_mode: sync
```

## Trakt User Collection

Finds every item in a Users Collection.

The expected input is a user's Trakt Username or `me`. Multiple values are supported as either a list or a comma-separated string.

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Trakt Collection:
    trakt_collection:
      - me
      - traktbuddy
    sync_mode: sync
```

## Trakt Trending

Finds the movies/shows in Trakt's Trending [Movies](https://trakt.tv/movies/trending)/[Shows](https://trakt.tv/shows/trending) list.

The expected input is a single integer value of how many movies/shows to query. 

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Trakt Trending:
    trakt_trending: 30
    collection_order: custom
    sync_mode: sync
```

## Trakt Popular

Finds the movies/shows in Trakt's Popular [Movies](https://trakt.tv/movies/popular)/[Shows](https://trakt.tv/shows/popular) list.

The expected input is a single integer value of how many movies/shows to query. 

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Trakt Popular:
    trakt_popular: 30
    collection_order: custom
    sync_mode: sync
```

## Trakt Recommended

Finds the movies/shows in Trakt's Recommended lists.

| Builder                     |  Period  |                          Movie List                           |                          Show List                          |
|:----------------------------|:--------:|:-------------------------------------------------------------:|:-----------------------------------------------------------:|
| `trakt_recommended_daily`   |  Daily   |   [Daily Movies](https://trakt.tv/movies/recommended/daily)   |   [Daily Shows](https://trakt.tv/shows/recommended/daily)   |
| `trakt_recommended_weekly`  |  Weekly  |  [Weekly Movies](https://trakt.tv/movies/recommended/weekly)  |  [Weekly Shows](https://trakt.tv/shows/recommended/weekly)  |
| `trakt_recommended_monthly` | Monthly  | [Monthly Movies](https://trakt.tv/movies/recommended/monthly) | [Monthly Shows](https://trakt.tv/shows/recommended/monthly) |
| `trakt_recommended_yearly`  |  Yearly  |  [Yearly Movies](https://trakt.tv/movies/recommended/yearly)  |  [Yearly Shows](https://trakt.tv/shows/recommended/yearly)  |
| `trakt_recommended_all`     | All-Time |  [All-Time Movies](https://trakt.tv/movies/recommended/all)   |  [All-Time Shows](https://trakt.tv/shows/recommended/all)   | 

The expected input is a single integer value of how many movies/shows to query. 

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Trakt Recommended:
    trakt_recommended_weekly: 30
    collection_order: custom
    sync_mode: sync
```

## Trakt Watched

Finds the movies/shows in Trakt's Watched lists.

| Builder                 |  Period  |                        Movie List                         |                        Show List                        |
|:------------------------|:--------:|:---------------------------------------------------------:|:-------------------------------------------------------:|
| `trakt_watched_daily`   |  Daily   |   [Daily Movies](https://trakt.tv/movies/watched/daily)   |   [Daily Shows](https://trakt.tv/shows/watched/daily)   |
| `trakt_watched_weekly`  |  Weekly  |  [Weekly Movies](https://trakt.tv/movies/watched/weekly)  |  [Weekly Shows](https://trakt.tv/shows/watched/weekly)  |
| `trakt_watched_monthly` | Monthly  | [Monthly Movies](https://trakt.tv/movies/watched/monthly) | [Monthly Shows](https://trakt.tv/shows/watched/monthly) |
| `trakt_watched_yearly`  |  Yearly  |  [Yearly Movies](https://trakt.tv/movies/watched/yearly)  |  [Yearly Shows](https://trakt.tv/shows/watched/yearly)  |
| `trakt_watched_all`     | All-Time |  [All-Time Movies](https://trakt.tv/movies/watched/all)   |  [All-Time Shows](https://trakt.tv/shows/watched/all)   | 

The expected input is a single integer value of how many movies/shows to query. 

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Trakt Watched:
    trakt_watched_weekly: 30
    collection_order: custom
    sync_mode: sync
```

## Trakt Collected

Finds the movies/shows in Trakt's Collected [Movies](https://trakt.tv/movies/collected/weekly)/[Shows](https://trakt.tv/shows/collected/weekly) list.

| Builder                   |  Period  |                         Movie List                          |                         Show List                         |
|:--------------------------|:--------:|:-----------------------------------------------------------:|:---------------------------------------------------------:|
| `trakt_collected_daily`   |  Daily   |   [Daily Movies](https://trakt.tv/movies/collected/daily)   |   [Daily Shows](https://trakt.tv/shows/collected/daily)   |
| `trakt_collected_weekly`  |  Weekly  |  [Weekly Movies](https://trakt.tv/movies/collected/weekly)  |  [Weekly Shows](https://trakt.tv/shows/collected/weekly)  |
| `trakt_collected_monthly` | Monthly  | [Monthly Movies](https://trakt.tv/movies/collected/monthly) | [Monthly Shows](https://trakt.tv/shows/collected/monthly) |
| `trakt_collected_yearly`  |  Yearly  |  [Yearly Movies](https://trakt.tv/movies/collected/yearly)  |  [Yearly Shows](https://trakt.tv/shows/collected/yearly)  |
| `trakt_collected_all`     | All-Time |  [All-Time Movies](https://trakt.tv/movies/collected/all)   |  [All-Time Shows](https://trakt.tv/shows/collected/all)   |

The expected input is a single integer value of how many movies/shows to query. 

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Trakt Collected:
    trakt_collected_weekly: 30
    collection_order: custom
    sync_mode: sync
```

## Trakt Box Office

Finds the 10 movies in Trakt's Top Box Office [Movies](https://trakt.tv/movies/boxoffice) list.

The expected input is true. 

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Trakt Collected:
    trakt_boxoffice: true
    collection_order: custom
    sync_mode: sync
```
