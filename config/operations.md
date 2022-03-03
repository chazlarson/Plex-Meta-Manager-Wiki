## Operations
There are a variety of Library Operations that can be utilized in a library.

Within each library definition, operations can be defined by using the `operations` definition, as demonstrated below.

```yaml
libraries:
  Movies:
    metadata_path:
      - git: meisnate12/MovieCharts
    operations:
      mass_critic_rating_update: tmdb
      split_duplicates: true
```

The available attributes for the operations definition are as follows

| Attribute                      | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|:-------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `genre_mapper`                 | Will check every item in your library and changed mapped genres<hr>**Values:** [key mapper and value mapper](#genre-mapper)                                                                                                                                                                                                                                                                                                                                                                                                      |
| `assets_for_all`               | Search in assets for images for every item in your library<hr>**Values:** `true` or `false`                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `delete_collections_with_less` | Deletes every collection with less then the given number<hr>**Values:** number greater then 0                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `delete_unmanaged_collections` | Deletes every unmanaged collection<hr>**Values:** `true` or `false`                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `mass_genre_update`            | Updates every item's genres in the library to the chosen site's genres<hr>**Values:** <table class="clearTable"><tr><td>`tmdb`</td><td>Use TMDb for Genres</td></tr><tr><td>`tvdb`</td><td>Use TVDb for Genres</td></tr><tr><td>`omdb`</td><td>Use IMDb through OMDb for Genres</td></tr></table>                                                                                                                                                                                                                                   |
| `mass_audience_rating_update`  | Updates every item's audience rating in the library to the chosen site's rating<hr>**Values:** <table class="clearTable"><tr><td>`tmdb`</td><td>Use TMDb for Rating</td></tr><tr><td>`omdb`</td><td>Use IMDb through OMDb for Rating</td></tr></table>                                                                                                                                                                                                                                                                              |
| `mass_critic_rating_update`    | Updates every item's critic rating in the library to the chosen site's rating<hr>**Values:** <table class="clearTable"><tr><td>`tmdb`</td><td>Use TMDb for Rating</td></tr><tr><td>`omdb`</td><td>Use IMDb through OMDb for Rating</td></tr></table>                                                                                                                                                                                                                                                                                |
| `mass_trakt_rating_update`     | Updates every movie/show's user rating in the library to match your custom rating on Trakt if there is one<hr>**Values:** `true` or `false`                                                                                                                                                                                                                                                                                                                                                                                         |
| `mass_collection_mode`         | Updates every Collection in your library to the specified Collection Mode<hr>**Values:** `default`: Library default<br>`hide`: Hide Collection<br>`hide_items`: Hide Items in this Collection<br>`show_items`: Show this Collection and its Items<table class="clearTable"><tr><td>`default`</td><td>Library default</td></tr><tr><td>`hide`</td><td>Hide Collection</td></tr><tr><td>`hide_items`</td><td>Hide Items in this Collection</td></tr><tr><td>`show_items`</td><td>Show this Collection and its Items</td></tr></table> |
| `split_duplicates`             | Splits all duplicate movies/shows found in this library<hr>**Values:** `true` or `false`                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `radarr_add_all`               | Adds every item in the library to Radarr. The existing paths in plex will be used as the root folder of each item, if the paths in Plex are not the same as your Radarr paths you can use the `plex_path` and `radarr_path` [Radarr](radarr) details to convert the paths.<hr>**Values:** `true` or `false`                                                                                                                                                                                                                         |
| `radarr_remove_by_tag`         | Removes every item from Radarr with the Tags given<hr>**Values:** List or comma separated string of tags                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `sonarr_add_all`               | Adds every item in the library to Sonarr. The existing paths in plex will be used as the root folder of each item, if the paths in Plex are not the same as your Sonarr paths you can use the `plex_path` and `sonarr_path` [Sonarr](sonarr) details to convert the paths.<hr>**Values:** `true` or `false`                                                                                                                                                                                                                         |
| `sonarr_remove_by_tag`         | Removes every item from Sonarr with the Tags given<hr>**Values:** List or comma separated string of tags                                                                                                                                                                                                                                                                                                                                                                                                                            |



### Genre Mapper
You can use the `genre_mapper` operation to map genres in your library.

Each attribute under `genre_mapper` is a separate mapping and has two parts. 
* The key (`Action` in the example below) is what the genres will end up as.
* The value( `Action/Adventure, Action & Adventure` in the example below) is what genres you want mapped to the key.

So this example will change go through every item in your library and change the genre `Action/Adventure` or `Action & Adventure` to `Action` and `Romantic Comedy` to `Comedy`.

```yaml
library:
  Movies:
    operations:
      genre_mapper:
        Action: Action/Adventure, Action & Adventure
        Comedy: Romantic Comedy
```

you can also use a list:

```yaml
library:
  Movies:
    operations:
      genre_mapper:
        Action: 
         - Action/Adventure
         - Action & Adventure
        Comedy: Romantic Comedy
```

To just Remove a Genre without replacing it just set the Genre to nothing like this.

```yaml
library:
  Movies:
    operations:
      genre_mapper:
        Action: Action/Adventure, Action & Adventure
        Romantic Comedy:
```

This example will change go through every item in your library and change the genre `Action/Adventure` or `Action & Adventure` to `Action` and remove every instance of the Genre `Romantic Comedy`.