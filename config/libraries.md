# Libraries Attributes

One of the two required configuration mappings is `libraries` which is where you set up a configuration for each Plex Library you want the program to interact with. 

Each library is defined by the mapping name which must be the same as the library name unless a different `library_name` is specified. You can either set attributes individually per library or you can let them be inherited from the global value. 

An advance example of multiple libraries with some using the global values and some having their own values is below:
```yaml
libraries:
  Movies:
    metadata_path:
      - file: config/Movies.yml
      - git: meisnate12/MovieCharts
      - git: meisnate12/Studios
      - git: meisnate12/IMDBGenres
      - git: meisnate12/People
    operations:
      mass_critic_rating_update: tmdb
      split_duplicates: true
  TV Shows:
    metadata_path:
      - file: config/TV Shows.yml
      - git: meisnate12/ShowCharts
      - git: meisnate12/Networks
  TV Shows On Second Plex:
    library_name: TV Shows
    plex:
      url: http://192.168.1.98:32400
      token: ####################
    metadata_path:
      - file: config/TV Shows.yml
      - git: meisnate12/ShowCharts
      - git: meisnate12/Networks
  Anime:
    metadata_path:
      - file: config/Anime.yml
      - git: meisnate12/AnimeCharts
    radarr:
      url: http://192.168.1.45:7878
      token: ################################
      root_folder_path: S:/Anime
    settings:
      asset_directory:
        config/assets/anime
plex:
  url: http://192.168.1.12:32400
  token: ####################
radarr:
  url: http://192.168.1.12:7878
  token: ################################
  add: true
  root_folder_path: S:/Movies
  monitor: true
  availability: announced
  quality_profile: HD-1080p
  tag: pmm
  search: false
```

The available attributes for each library are as follows

| Name                            | Attribute       | Allowed Values                                                                      |                Default                 |            Required             |
|:--------------------------------|:----------------|:------------------------------------------------------------------------------------|:--------------------------------------:|:-------------------------------:|
| [Library Name](#library-name)   | `library_name`  | Library name (Only needed when trying to use multiple libraries with the same name) |          Base Attribute Name           |            &#10060;             |
| [Metadata Path](#metadata-path) | `metadata_path` | Location for your Metadata YAML files                                               |     `/config/<<MAPPING_NAME>>.yml`     |            &#10060;             |
| [Missing Path](#missing-path)   | `missing_path`  | Path to missing YAML file for the library                                           | `/config/<<MAPPING_NAME>>_missing.yml` |            &#10060;             |
| [Operations](#operations)       | `operations`    | Library Operations to run                                                           |                  N/A                   |            &#10060;             |
| [Settings Mapping](settings)    | `settings`      | Any `setting` attribute you want different from global                              |                 global                 |            &#10060;             |
| [Plex Mapping](plex)            | `plex`          | Any `plex` attribute you want different from global                                 |                 global                 | &#9989; Either here or globally |
| [Radarr Mapping](radarr)        | `radarr`        | Any `radarr` attribute you want different from global                               |                 global                 |            &#10060;             |
| [Sonarr Mapping](sonarr)        | `sonarr`        | Any `sonarr` attribute you want different from global                               |                 global                 |            &#10060;             |
| [Tautulli Mapping](tautulli)    | `tautulli`      | Any `tautulli` attribute you want different from global                             |                 global                 |            &#10060;             |

* Library mappings must have a colon `:` placed after them

## Library Name

Each library must have a different name. If you want to use multiple libraries with the same name you can use the `library_name` attribute to specify the real Library Name and just have a placeholder as the library mapping name. A simple example is below:

```yaml
libraries:
  Movies01:
    library_name: Movies
  Movies02:
    library_name: Movies
    plex:
      url: http://192.168.1.35:32400
      token: ####################
  TV Shows:
  Anime:
plex:
  url: http://192.168.1.12:32400
  token: ####################
```

* Movies01, TV Shows, and Anime will all use the global plex server http://192.168.1.12:32400, defined using the global `plex` mapping. While the library, Movies02, will use the plex server http://192.168.1.35:32400 which is defined under its `plex` mapping over the global mapping.

## Metadata Path

You can define Metadata Files by using `metadata_path`. They can either be on the local system, online at an url, or directly from the [Plex Meta Manager Configs](https://github.com/meisnate12/Plex-Meta-Manager-Configs) repository.

By default, when `metadata_path` is missing the script will look in your config directory for `<MAPPING_NAME>.yml` so `Movies.yml` in the example below.
```yaml
libraries:
  Movies:
```
To use a local Metadata File add `file` under metadata set to the system path of the yaml file.
```yaml
libraries:
  Movies:
    metadata_path: 
      file: /config/My Movies.yml
```
To use all yaml files in a particular folder add `folder` under metadata set to the system path of the folder containing the yaml files.
```yaml
libraries:
  Movies:
    metadata_path: 
      folder: /config/Movie Configs/
```
To use a Metadata File online add `url` under metadata set to the url of the yaml file.
```yaml
libraries:
  Movies:
    metadata_path:
      url: http://somesite.com/metadata_file.yml
```
To use a Metadata File from the [Plex Meta Manager Configs](https://github.com/meisnate12/Plex-Meta-Manager-Configs) repository add `git` under metadata set to the path in the repository.
```yaml
libraries:
  Movies:
    metadata_path:
      git: meisnate12/Charts
```
To use a Playlist File from a `custom_repo` defined in the global Settings add `repo` under playlist_files set to the path in the repository.
* This loads the yaml file at `https://raw.githubusercontent.com/zluckytraveler/Plex-Meta-Manager-Configs/master/zluckytraveler/Collections/Movies/Movies.yml`
```yaml
settings:
  custom_repo: https://raw.githubusercontent.com/zluckytraveler/Plex-Meta-Manager-Configs/master/zluckytraveler/
playlist_files:
  repo: Collections/Movies/Movies
```
You can specify multiple paths of any type using a list like below.
```yaml
libraries:
  Movies:
    metadata_path:
      - file: /config/My Movies.yml
      - url: http://somesite.com/people_collections.yml
      - git: meisnate12/Charts
      - git: meisnate12/Studios
```

## Missing Path
Path where to save the missing YAML File. Default is `/config/<<MAPPING_NAME>>_missing.yml` where `<<MAPPING_NAME>>` is the mapping name for the library.

```yaml
libraries:
  Movies:
    missing_path: /config/Missing/Movies.yml
```

<hr/>

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
