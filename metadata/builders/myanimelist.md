# MyAnimeList Builders

You can find anime using the features of [MyAnimeList.net](https://myanimelist.net/) (MyAnimeList).

[Configuring MyAnimeList](../../config/myanimelist) in the config is required for any of these builders.

| Name                                                                  | Attribute       | Description                                                                                                                                                       | Works with Movies | Works with Shows | Works with Playlists and Custom Sort |
|:----------------------------------------------------------------------|:----------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------:|:----------------:|:------------------------------------:|
| [MyAnimeList Top All Anime](#myanimelist-top-all-anime)               | `mal_all`       | Finds every anime in MyAnimeList's [Top All Anime](https://myanimelist.net/topanime.php) list                                                                     |      &#9989;      |     &#9989;      |               &#9989;                | 
| [MyAnimeList Top Airing Anime](#myanimelist-top-airing-anime)         | `mal_airing`    | Finds every anime in MyAnimeList's [Top Airing Anime](https://myanimelist.net/topanime.php?type=airing) list                                                      |      &#9989;      |     &#9989;      |               &#9989;                |
| [MyAnimeList Top Upcoming Anime](#myanimelist-top-upcoming-anime)     | `mal_upcoming`  | Finds every anime in MyAnimeList's [Top Upcoming Anime](https://myanimelist.net/topanime.php?type=upcoming) list                                                  |      &#9989;      |     &#9989;      |               &#9989;                |
| [MyAnimeList Top Anime TV Series](#myanimelist-top-anime-tv-series)   | `mal_tv`        | Finds every anime in MyAnimeList's [Top Anime TV Series](https://myanimelist.net/topanime.php?type=tv) list                                                       |      &#9989;      |     &#9989;      |               &#9989;                |
| [MyAnimeList Top Anime Movies](#myanimelist-top-anime-movies)         | `mal_movie`     | Finds every anime in MyAnimeList's [Top Anime Movies](https://myanimelist.net/topanime.php?type=movie) list                                                       |      &#9989;      |     &#9989;      |               &#9989;                |
| [MyAnimeList Top Anime OVA Series](#myanimelist-top-anime-ova-series) | `mal_ova`       | Finds every anime in MyAnimeList's [Top Anime OVA Series](https://myanimelist.net/topanime.php?type=ova) list                                                     |      &#9989;      |     &#9989;      |               &#9989;                |
| [MyAnimeList Top Anime Specials](#myanimelist-top-anime-specials)     | `mal_special`   | Finds every anime in MyAnimeList's [Top Anime Specials](https://myanimelist.net/topanime.php?type=special) list                                                   |      &#9989;      |     &#9989;      |               &#9989;                |
| [MyAnimeList Most Popular Anime](#myanimelist-most-popular-anime)     | `mal_popular`   | Finds every anime in MyAnimeList's [Most Popular Anime](https://myanimelist.net/topanime.php?type=bypopularity) list                                              |      &#9989;      |     &#9989;      |               &#9989;                |
| [MyAnimeList Most Favorited Anime](#myanimelist-most-favorited-anime) | `mal_favorite`  | Finds every anime in MyAnimeList's [Most Favorited Anime](https://myanimelist.net/topanime.php?type=favorite) list                                                |      &#9989;      |     &#9989;      |               &#9989;                |
| [MyAnimeList Suggested Anime](#myanimelist-suggested-anime)           | `mal_suggested` | Finds the suggested anime in by MyAnimeList for the authorized user                                                                                               |      &#9989;      |     &#9989;      |               &#9989;                |
| [MyAnimeList ID](#myanimelist-id)                                     | `mal_id`        | Finds the anime specified by the MyAnimeList ID                                                                                                                   |      &#9989;      |     &#9989;      |               &#10060;               |
| [MyAnimeList User Anime List](#myanimelist-user-anime-list)           | `mal_userlist`  | Finds anime in MyAnimeList User's Anime list the options are detailed below                                                                                       |      &#9989;      |     &#9989;      |               &#9989;                |
| [MyAnimeList Seasonal Anime](#myanimelist-seasonal-anime)             | `mal_season`    | Finds anime in MyAnimeList's [Seasonal Anime](https://myanimelist.net/anime/season) list the options are detailed below                                           |      &#9989;      |     &#9989;      |               &#9989;                |
| [MyAnimeList Genre](#myanimelist-genre)                               | `mal_genre`     | Finds every anime tagged with the specified genre id. Genre options can be found on [MyAnimeList's Search](https://myanimelist.net/anime.php)                     |      &#9989;      |     &#9989;      |               &#9989;                |
| [MyAnimeList Studio](#myanimelist-studio)                             | `mal_studio`    | Finds every anime tagged with the specified studio/producer/licensor id. Studio options can be found on [MyAnimeList's Search](https://myanimelist.net/anime.php) |      &#9989;      |     &#9989;      |               &#9989;                |

## Expected Input

The builders below are expected to have a single integer value of how many movies/shows to query. 
* [MyAnimeList Top All Anime](#myanimelist-top-all-anime)
* [MyAnimeList Top Airing Anime](#myanimelist-top-airing-anime)
* [MyAnimeList Top Upcoming Anime](#myanimelist-top-upcoming-anime)
* [MyAnimeList Top Anime TV Series](#myanimelist-top-anime-tv-series)
* [MyAnimeList Top Anime Movies](#myanimelist-top-anime-movies)
* [MyAnimeList Top Anime OVA Series](#myanimelist-top-anime-ova-series)
* [MyAnimeList Top Anime Specials](#myanimelist-top-anime-specials)
* [MyAnimeList Most Popular Anime](#myanimelist-most-popular-anime)
* [MyAnimeList Most Favorited Anime](#myanimelist-most-favorited-anime)
* [MyAnimeList Suggested Anime](#myanimelist-suggested-anime)

The attributes of [MyAnimeList ID](#myanimelist-id), [MyAnimeList Seasonal Anime](#myanimelist-seasonal-anime), [MyAnimeList User Anime List](#myanimelist-user-anime-list), [MyAnimeList Genre](#myanimelist-genre), and [MyAnimeList Studio](#myanimelist-studio) are detailed in their sections below.


## MyAnimeList Top All Anime

Gets every anime in MyAnimeList's [Top Airing Anime](https://myanimelist.net/topanime.php?type=airing) list. (Maximum: 500)

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Top All Anime:
    mal_all: 30
    collection_order: custom
    sync_mode: sync
```

## MyAnimeList Top Airing Anime

Gets every anime in MyAnimeList's [Top Airing Anime](https://myanimelist.net/topanime.php?type=airing) list. (Maximum: 500)

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Top Airing Anime:
    mal_airing: 10
    collection_order: custom
    sync_mode: sync
```

## MyAnimeList Top Upcoming Anime

Gets every anime in MyAnimeList's [Top Upcoming Anime](https://myanimelist.net/topanime.php?type=upcoming) list. (Maximum: 500)

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Top Upcoming Anime:
    mal_upcoming: 10
    collection_order: custom
    sync_mode: sync
```

## MyAnimeList Top Anime TV Series

Gets every anime in MyAnimeList's [Top Anime TV Series](https://myanimelist.net/topanime.php?type=tv) list. (Maximum: 500)

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Top Anime TV Series:
    mal_tv: 20
    collection_order: custom
    sync_mode: sync
```

## MyAnimeList Top Anime Movies

Gets every anime in MyAnimeList's [Top Anime Movies](https://myanimelist.net/topanime.php?type=movie) list. (Maximum: 500)

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Top Anime Movies:
    mal_movie: 20
    collection_order: custom
    sync_mode: sync
```

## MyAnimeList Top Anime OVA Series

Gets every anime in MyAnimeList's [Top Anime OVA Series](https://myanimelist.net/topanime.php?type=ova) list. (Maximum: 500)

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Top Anime OVA Series:
    mal_ova: 20
    collection_order: custom
    sync_mode: sync
```

## MyAnimeList Top Anime Specials

Gets every anime in MyAnimeList's [Top Anime Specials](https://myanimelist.net/topanime.php?type=special) list. (Maximum: 500)

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Top Anime Specials:
    mal_special: 20
    collection_order: custom
    sync_mode: sync
```

## MyAnimeList Most Popular Anime

Gets every anime in MyAnimeList's [Most Popular Anime](https://myanimelist.net/topanime.php?type=bypopularity) list. (Maximum: 500)

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Most Popular Anime:
    mal_popular: 20
    collection_order: custom
    sync_mode: sync
```

## MyAnimeList Most Favorited Anime

Gets every anime in MyAnimeList's [Most Favorited Anime](https://myanimelist.net/topanime.php?type=favorite) list. (Maximum: 500)

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Most Favorited Anime:
    mal_favorite: 20
    collection_order: custom
    sync_mode: sync
```

## MyAnimeList Suggested Anime

Gets the suggested anime in by MyAnimeList for the authorized user. (Maximum: 100)

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  Suggested Anime:
    mal_suggested: 20
    collection_order: custom
    sync_mode: sync
```

## MyAnimeList ID

Gets the anime specified by the MyAnimeList ID.

The expected input is a MyAnimeList ID. Multiple values are supported as either a list or a comma-separated string.

```yaml
collections:
  Cowboy Bebop:
    mal_id: 23, 219
```

## MyAnimeList User Anime List

Gets anime in MyAnimeList User's Anime list. The different sub-attributes are detailed below.

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

| Attribute  | Description                                                                                                                                                                               | Required | Default |
|:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------:|:-------:|
| `username` | A user's MyAnimeList Username or `@me` for the authorized user                                                                                                                            | &#9989;  |   N/A   |
| `status`   | `all` (All Anime List)<br>`watching` (Currently Watching List)<br>`completed` (Completed List)<br>`on_hold` (On Hold List)<br>`dropped` (Dropped List)<br>`plan_to_watch` (Plan to Watch) | &#10060; |  `all`  |
| `sort_by`  | `score` (Sort by Score)<br>`last_updated` (Sort by Last Updated)<br>`title` (Sort by Anime Title)<br>`start_date` (Sort by Start Date)                                                    | &#10060; | `score` |
| `limit`    | Number of Anime to query from MyAnimeList (max: 1000)                                                                                                                                     | &#10060; |   100   |

```yaml
collections:
  Currently Watching Anime:
    mal_userlist:
      username: @me
      status: watching
      sort_by: score
      limit: 500
    collection_order: custom
    sync_mode: sync
```

## MyAnimeList Seasonal Anime

Gets anime in MyAnimeList's [Seasonal Anime](https://myanimelist.net/anime/season) list the options are detailed below. 

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

| Attribute | Description                                                                                                                                                                                                            | Required |    Default     |
|:----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------:|:--------------:|
| `season`  | `winter` (For winter season January, February, March)<br>`spring` (For spring season April, May, June)<br>`summer` (For summer season July, August, September)<br>`fall` (For fall season October, November, December) | &#10060; | Current Season |
| `year`    | 4 digit integer year between 1917-Current                                                                                                                                                                              | &#10060; |  Current Year  |
| `sort_by` | `members` (Sort by Most Members)<br>`score` (Sort by Score)                                                                                                                                                            | &#10060; |   `members`    |
| `limit`   | Number of Anime to query from MyAnimeList (max: 500)                                                                                                                                                                   | &#10060; |      100       |

```yaml
collections:
  Current Anime Season:
    mal_season:
      sort_by: members
      limit: 50
    collection_order: custom
    sync_mode: sync
```
```yaml
collections:
  Fall 2020 Anime:
    mal_season:
      season: fall
      year: 2020
      limit: 50
    collection_order: custom
    sync_mode: sync
```

## MyAnimeList Genre

Gets every anime tagged with the specified genre ID sorted by members the options are detailed below.

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

* Genre options can be found on [MyAnimeList's Search](https://myanimelist.net/anime.php) Page.
* To find the ID click on a Genre in the link above and there should be a number in the URL that's the `genre_id`.
* For example if the url is `https://myanimelist.net/anime/genre/1/Action` the `genre_id` would be `1`.

| Attribute  | Description                               | Required | Default |
|:-----------|:------------------------------------------|:--------:|:-------:|
| `genre_id` | The ID of Genre from MyAnimeList          | &#9989;  |   N/A   |
| `limit`    | Number of Anime to query from MyAnimeList | &#10060; | 0 (All) |

```yaml
collections:
  Sports Anime:
    mal_genre:
      genre_id: 30
    collection_order: custom
    sync_mode: sync
```

## MyAnimeList Studio 

Gets every anime tagged with the specified studio/producer/licensor ID sorted by members the options are detailed below.

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

* Studio options can be found on [MyAnimeList's Search](https://myanimelist.net/anime.php) Page.
* To find the ID click on a Studio in the link above and there should be a number in the URL that's the `studio_id`.
* For example if the url is `https://myanimelist.net/anime/producer/4/Bones` the `studio_id` would be `4`.

| Attribute   | Description                                         | Required | Default |
|:------------|:----------------------------------------------------|:--------:|:-------:|
| `studio_id` | The ID of Studio/Producer/Licensor from MyAnimeList | &#9989;  |   N/A   |
| `limit`     | Number of Anime to query from MyAnimeList           | &#10060; | 0 (All) |

```yaml
collections:
  Bones Studio Anime:
    mal_studio:
      studio_id: 4
    collection_order: custom
    sync_mode: sync
```
