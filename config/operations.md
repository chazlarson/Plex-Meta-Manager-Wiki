## Operations
There are multiple different Library Operations you can have preformed on each of your libraries.

You can define which operations you want to run under the `operations` attribute you can define per library.

A simple example of using some operations is below:
```yaml
libraries:
  Movies:
    metadata_path:
      - git: meisnate12/MovieCharts
    operations:
      mass_critic_rating_update: tmdb
      split_duplicates: true
```

The available operations attributes for each library are as follows

| Name                                    | Attribute                      | Description                                                                                                | Allowed Values                                                                                                                                           |
|:----------------------------------------|:-------------------------------|:-----------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------|
| [Genre Mapper](#genre-mapper)           | `genre_mapper`                 | Will check every item in your library and changed mapped genres                                            | [`genre_mapper` mapping details](#genre-mapper)                                                                                                          |
| Image Assets For All                    | `assets_for_all`               | Search in assets for images for every item in your library                                                 | `true` or `false`                                                                                                                                        |
| Delete Collections With Less            | `delete_collections_with_less` | Deletes every collection with less then the given number                                                   | number greater then 0                                                                                                                                    |
| Delete Unmanaged Collections            | `delete_unmanaged_collections` | Deletes every unmanaged collection                                                                         | `true` or `false`                                                                                                                                        |
| Mass Genre Update                       | `mass_genre_update`            | Updates every item's genres in the library to the chosen site's genres                                     | `tmdb`: Use TMDb for Genres<br>`tvdb`: Use TVDb for Genres<br>`omdb`: Use IMDb through OMDb for Genres                                                   |
| Mass Audience Rating Update             | `mass_audience_rating_update`  | Updates every item's audience rating in the library to the chosen site's rating                            | `tmdb`: Use TMDb for Rating<br>`omdb`: Use IMDb through OMDb for Rating                                                                                  |
| Mass Critic Rating Update               | `mass_critic_rating_update`    | Updates every item's critic rating in the library to the chosen site's rating                              | `tmdb`: Use TMDb for Rating<br>`omdb`: Use IMDb through OMDb for Rating                                                                                  |
| Mass Trakt Rating Update                | `mass_trakt_rating_update`     | Updates every movie/show's user rating in the library to match your custom rating on Trakt if there is one | `true` or `false`                                                                                                                                        |
| Mass Collection Mode                    | `mass_collection_mode`         | Updates every Collection in your library to the specified Collection Mode                                  | `default`: Library default<br>`hide`: Hide Collection<br>`hide_items`: Hide Items in this Collection<br>`show_items`: Show this Collection and its Items |
| Split Duplicates                        | `split_duplicates`             | Splits all duplicate movies/shows found in this library                                                    | `true` or `false`                                                                                                                                        |
| Radarr Add All                          | `radarr_add_all`               | Adds every item in the library to Radarr                                                                   | `true` or `false`                                                                                                                                        |
| Radarr Remove By Tag                    | `radarr_remove_by_tag`         | Removes every item from Radarr with the Tags given                                                         | List or comma separated string of tags                                                                                                                   |
| Sonarr Add All                          | `sonarr_add_all`               | Adds every item in the library to Sonarr                                                                   | `true` or `false`                                                                                                                                        |
| Sonarr Remove By Tag                    | `sonarr_remove_by_tag`         | Removes every item from Sonarr with the Tags given                                                         | List or comma separated string of tags                                                                                                                   |

* When using `radarr_add_all` or `sonarr_add_all` the existing paths in plex will be used as the root folder of each item.
* If the paths in Plex are not the same as your Radarr/Sonarr paths you can use the `plex_path` and `radarr_path`/`sonarr_path` [Radarr](radarr)/[Sonarr](sonarr) details to convert the paths


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