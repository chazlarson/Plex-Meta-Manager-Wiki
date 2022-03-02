# Radarr/Sonarr Details

## Radarr Details

All the following attributes can override the global/library [Radarr](../../config/radarr) attributes which are the default unless otherwise specified.

| Attribute                | Description & Values                                                                                                                                           |
|:-------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `radarr_add_missing`     | Override Radarr `add` attribute<hr>**Values:** `true` or `false`                                                                                               |
| `radarr_add_existing`    | Override Radarr `add_existing` attribute<hr>**Values:** `true` or `false`                                                                                      |
| `radarr_folder`          | Override Radarr `root_folder_path` attribute<hr>**Values:** Folder Path                                                                                        |
| `radarr_monitor`         | Override Radarr `monitor` attribute<hr>**Values:** `true` or `false`                                                                                           |
| `radarr_availability`    | Override Radarr `availability` attribute<hr>**Values:** `announced`, `cinemas`, `released`, `db`                                                               |
| `radarr_quality`         | Override Radarr `quality_profile` attribute<hr>**Values:** Radarr Quality Profile                                                                              |
| `radarr_tag`             | Override Radarr `tag` attribute<hr>**Values:** List or comma-separated string of tags                                                                          |
| `radarr_search`          | Override Radarr `search` attribute<hr>**Values:** `true` or `false`                                                                                            |
| `item_radarr_tag`        | Used to append a tag in Radarr for every movie found by the builders that's in Radarr<hr>**Values:** List or comma-separated string of tags                    |
| `item_radarr_tag.remove` | Used to remove existing tags in Radarr for every movie found by the builders that's in Radarr<hr>**Values:** List or comma-separated string of tags            |
| `item_radarr_tag.sync`   | Matches the tags in Radarr for every movie found by the builders that's in Radarr with the provided tags<hr>**Values:** List or comma-separated string of tags |

## Sonarr Details

All the following attributes can override the global/library [Sonarr](../../config/sonarr) attributes which are the default unless otherwise specified.

| Attribute                | Description & Values                                                                                                                                            |
|:-------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sonarr_add_missing`     | Override Sonarr `add` attribute<hr>**Values:** `true` or `false`                                                                                                |
| `sonarr_add_existing`    | Override Sonarr `add_existing` attribute<hr>**Values:** `true` or `false`                                                                                       |
| `sonarr_folder`          | Override Sonarr `root_folder_path` attribute<hr>**Values:** Folder Path                                                                                         |
| `sonarr_monitor`         | Override Sonarr `monitor` attribute<hr>**Values:** `all`, `future`, `missing`, `existing`, `pilot`, `first`, `latest`, `none`                                   |
| `sonarr_quality`         | Override Sonarr `quality_profile` attribute<hr>**Values:** Sonarr Quality Profile                                                                               |
| `sonarr_language`        | Override Sonarr `language_profile` attribute<hr>**Values:** Sonarr Language Profile                                                                             |
| `sonarr_series`          | Override Sonarr `series_type` attribute<hr>**Values:** `standard`, `daily`, `anime`                                                                             |
| `sonarr_season`          | Override Sonarr `season_folder` attribute<hr>**Values:** `true` or `false`                                                                                      |
| `sonarr_tag`             | Override Sonarr `tag` attribute<hr>**Values:** List or comma-separated string of tags                                                                           |
| `sonarr_search`          | Override Sonarr `search` attribute<hr>**Values:** `true` or `false`                                                                                             |
| `sonarr_cutoff_search`   | Override Sonarr `cutoff_search` attribute<hr>**Values:** `true` or `false`                                                                                      |
| `item_sonarr_tag`        | Used to append a tag in Sonarr for every series found by the builders that's in Sonarr<hr>**Values:** List or comma-separated string of tags                    |
| `item_sonarr_tag.remove` | Used to remove existing tags in Sonarr for every series found by the builders that's in Sonarr<hr>**Values:** List or comma-separated string of tags            |
| `item_sonarr_tag.sync`   | Matches the tags in Sonarr for every series found by the builders that's in Sonarr with the provided tags<hr>**Values:** List or comma-separated string of tags |

## Adding to Arr
You can add items to Radarr/Sonarr in two different ways.
  1. Items found by PMM that are missing from your collections/playlists.
  2. Items found by PMM that already exist in Plex but are not in Radarr/Sonarr.

### Arr Add Missing

When `radarr_add_missing`/`sonarr_add_missing` are true the items missing from the collection/playlist will be added to Radarr/Sonarr.

### Arr Add Existing

When `radarr_add_existing`/`sonarr_add_existing` are true the items that exist in the collection/playlist will be added to Radarr/Sonarr. 

If your Radarr/Sonarr has different file system mappings from your plex use `radarr_path`/`sonarr_path` along with `plex_path` from your [Radarr](../../config/radarr)/[Sonarr](../../config/sonarr) global config settings.

### Radarr Add Details

When adding a movie in Radarr you get the screen below to set these options use `radarr_folder`, `radarr_monitor`, `radarr_availability`, `radarr_quality`, `radarr_tag`, and `radarr_search`.

![Radarr Details](radarr.png)

### Sonarr Add Details

When adding a movie in Sonarr you get the screen below to set these options use `sonarr_folder`, `sonarr_monitor`, `sonarr_quality`, `sonarr_language`, `sonarr_series`, `sonarr_season`, `sonarr_tag`, `sonarr_search`, and `sonarr_cutoff_search`.

![Sonarr Details](sonarr.png)

## Arr Edit Details

When editing the details of items that exist in the collection/playlist and in Radarr/Sonarr use `item_radarr_tag` and `item_sonarr_tag`