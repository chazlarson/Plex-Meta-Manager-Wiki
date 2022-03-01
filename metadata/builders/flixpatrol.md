# FlixPatrol Builders

You can find items using the features of [FlixPatrol.com](https://flixpatrol.com/) (FlixPatrol).

No configuration is required for this builder.

| Name                                                | Attribute                 | Description                                                                                                                                                                                 | Works with Movies | Works with Shows | Works with Playlists and Custom Sort |
|:----------------------------------------------------|:--------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------:|:----------------:|:------------------------------------:|
| [FlixPatrol Top](#flixpatrol-top-platform)          | `flixpatrol_top`          | Finds every item from [FlixPatrol's Top Platform Lists](https://flixpatrol.com/top10/) based on the attributes provided.                                                                    |      &#9989;      |     &#9989;      |               &#9989;                |
| [FlixPatrol Popular](#flixpatrol-popular)           | `flixpatrol_popular`      | Finds every movie/show from FlixPatrol's Popular [Movies](https://flixpatrol.com/popular/movies/)/[Shows](https://flixpatrol.com/popular/tv-shows/) Lists based on the attributes provided. |      &#9989;      |     &#9989;      |               &#9989;                |
| [FlixPatrol Demographics](#flixpatrol-demographics) | `flixpatrol_demographics` | Finds every item from [FlixPatrol's Demographics Lists](https://flixpatrol.com/demographics/) based on the attributes provided.                                                             |      &#9989;      |     &#9989;      |               &#9989;                |
| [FlixPatrol URL](#flixpatrol-url)                   | `flixpatrol_url`          | Finds every item found at a FlixPatrol URL.                                                                                                                                                 |      &#9989;      |     &#9989;      |               &#9989;                |

## FlixPatrol Top Platform

Finds every item from [FlixPatrol's Top Platform Lists](https://flixpatrol.com/top10/) based on the attributes provided.

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

### Top Platform Attributes

| Attribute     | Description                      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            Options                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            | Required | Default  |
|:--------------|:---------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|:--------:|
| `platform`    | Streaming Platform to filter on. |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                `netflix`, `hbo`, `disney`, `amazon`, `itunes`, `google`, `paramount_plus`, `hulu`, `vudu`, `imdb`, `amazon_prime`, `star_plus`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                | &#9989;  | &#10060; |
| `location`    | Location to filter on.           | `world`, `albania`, `argentina`, `armenia`, `australia`, `austria`, `azerbaijan`, `bahamas`, `bahrain`, `bangladesh`, `belarus`, `belgium`, `belize`, `benin`, `bolivia`, `bosnia_and_herzegovina`, `botswana`, `brazil`, `bulgaria`, `burkina_faso`, `cambodia`, `canada`, `chile`, `colombia`, `costa_rica`, `croatia`, `cyprus`, `czech_republic`, `denmark`, `dominican_republic`, `ecuador`, `egypt`, `estonia`, `finland`, `france`, `gabon`, `germany`, `ghana`, `greece`, `guatemala`, `guinea_bissau`, `haiti`, `honduras`, `hong_kong`, `hungary`, `iceland`, `india`, `indonesia`, `ireland`, `israel`, `italy`, `ivory_coast`, `jamaica`, `japan`, `jordan`, `kazakhstan`, `kenya`, `kuwait`, `kyrgyzstan`, `laos`, `latvia`, `lebanon`, `lithuania`, `luxembourg`, `malaysia`, `maldives`, `mali`, `malta`, `mexico`, `moldova`, `mongolia`, `montenegro`, `morocco`, `mozambique`, `namibia`, `netherlands`, `new_zealand`, `nicaragua`, `niger`, `nigeria`, `north_macedonia`, `norway`, `oman`, `pakistan`, `panama`, `papua_new_guinea`, `paraguay`, `peru`, `philippines`, `poland`, `portugal`, `qatar`, `romania`, `russia`, `rwanda`, `salvador`, `saudi_arabia`, `senegal`, `serbia`, `singapore`, `slovakia`, `slovenia`, `south_africa`, `south_korea`, `spain`, `sri_lanka`, `sweden`, `switzerland`, `taiwan`, `tajikistan`, `tanzania`, `thailand`, `togo`, `trinidad_and_tobago`, `turkey`, `turkmenistan`, `uganda`, `ukraine`, `united_arab_emirates`, `united_kingdom`, `united_states`, `uruguay`, `uzbekistan`, `venezuela`, `vietnam`, `zambia`, `zimbabwe` | &#10060; | `world`  |
| `time_window` | Time window to filter on.        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              `today`, `yesterday`,`this_week`, `last_week`, `this_month`, `last_month`, `this_year`, `last_year`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | &#10060; | `today`  |
| `limit`       | Number of items to return.       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    Integer greater then 0                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     | &#10060; |    10    |

```yaml
collections:
  US Netflix Monthly Top 20:
    flixpatrol_top:
      platform: netflix
      location: united_states
      time_window: this_month
      limit: 20
    collection_order: custom
    sync_mode: sync
```

## FlixPatrol Popular

Dinds every movie/show from FlixPatrol's Popular [Movies](https://flixpatrol.com/popular/movies/)/[Shows](https://flixpatrol.com/popular/tv-shows/) Lists based on the attributes provided.

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

### Popular Attributes

| Attribute     | Description                |                                                                               Options                                                                               | Required | Default  |
|:--------------|:---------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------:|:--------:|:--------:|
| `source`      | Source to filter on.       | `movie_db`, `facebook`, `google`, `twitter`, `twitter_trends`, `instagram`, `instagram_trends`, `youtube`, `imdb`, `letterboxd`, `rotten_tomatoes`, `tmdb`, `trakt` | &#9989;  | &#10060; |
| `time_window` | Time window to filter on.  |                                 `today`, `yesterday`,`this_week`, `last_week`, `this_month`, `last_month`, `this_year`, `last_year`                                 | &#10060; | `today`  |
| `limit`       | Number of items to return. |                                                                       Integer greater then 0                                                                        | &#10060; |    10    |

```yaml
collections:
  Instagram Popular:
    flixpatrol_popular:
      source: instagram
      time_window: all
      limit: 20
    collection_order: custom
    sync_mode: sync
```

## FlixPatrol Demographics

Finds every item from [FlixPatrol's Demographics Lists](https://flixpatrol.com/demographics/) based on the attributes provided.

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

### Demographics Attribute

| Attribute    | Description                |                                                 Options                                                 | Required | Default  |
|:-------------|:---------------------------|:-------------------------------------------------------------------------------------------------------:|:--------:|:--------:|
| `generation` | Generation to filter on.   |                                     `all`, `boomers`, `x`, `y`, `z`                                     | &#9989;  | &#10060; |
| `gender`     | Gender to filter on.       |                                          `all`, `men`, `women`                                          | &#10060; |  `all`   |
| `location`   | Location to filter on.     | `world`, `brazil`, `canada`, `france`, `germany`, `india`, `mexico`,  `united_kingdom`, `united_states` | &#10060; | `world`  |
| `limit`      | Number of items to return. |                                         Integer greater then 0                                          | &#10060; |    10    |

```yaml
collections:
  Gen X Male US Demographic:
    flixpatrol_demographics:
      generation: x
      gender: men
      location: united_states 
      limit: 20
    collection_order: custom
    sync_mode: sync
```

## FlixPatrol URL

Finds every item found at a FlixPatrol URL.

The `sync_mode: sync` and `collection_order: custom` Details are recommended since the lists are continuously updated and in a specific order. 

```yaml
collections:
  US Netflix Monthly:
    flixpatrol_url: https://flixpatrol.com/top10/netflix/united-states/2021-11/full/
    collection_order: custom
    sync_mode: sync
  Instagram Monthly Popular:
    flixpatrol_url: https://flixpatrol.com/popular/movies/instagram/all-time/
    collection_order: custom
    sync_mode: sync
  Gen X Male US Demographic:
    flixpatrol_url: https://flixpatrol.com/demographics/generation-x/men/united-states/
    collection_order: custom
    sync_mode: sync
```
