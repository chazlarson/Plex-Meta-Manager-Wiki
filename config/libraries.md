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