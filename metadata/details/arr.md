# Arr Details

## Radarr Details

All the following attributes can override the global/library [Radarr](../../config/radarr) attributes which are the default unless otherwise specified.

| Attribute                                     | Description & Values                                                                                                                                           |
|:----------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [`radarr_add_missing`](#arr-add-missing)      | Override Radarr `add` attribute<hr>**Values:** `true` or `false`                                                                                               |
| [`radarr_add_existing`](#arr-add-existing)    | Override Radarr `add_existing` attribute<hr>**Values:** `true` or `false`                                                                                      |
| [`radarr_folder`](#radarr-add-details)        | Override Radarr `root_folder_path` attribute<hr>**Values:** Folder Path                                                                                        |
| [`radarr_monitor`](#radarr-add-details)       | Override Radarr `monitor` attribute<hr>**Values:** `true` or `false`                                                                                           |
| [`radarr_availability`](#radarr-add-details)  | Override Radarr `availability` attribute<hr>**Values:** `announced`, `cinemas`, `released`, `db`                                                               |
| [`radarr_quality`](#radarr-add-details)       | Override Radarr `quality_profile` attribute<hr>**Values:** Radarr Quality Profile                                                                              |
| [`radarr_tag`](#radarr-add-details)           | Override Radarr `tag` attribute<hr>**Values:** List or comma-separated string of tags                                                                          |
| [`radarr_search`](#radarr-add-details)        | Override Radarr `search` attribute<hr>**Values:** `true` or `false`                                                                                            |
| [`item_radarr_tag`](#arr-edit-details)        | Used to append a tag in Radarr for every movie found by the builders that's in Radarr<hr>**Values:** List or comma-separated string of tags                    |
| [`item_radarr_tag.remove`](#arr-edit-details) | Used to remove existing tags in Radarr for every movie found by the builders that's in Radarr<hr>**Values:** List or comma-separated string of tags            |
| [`item_radarr_tag.sync`](#arr-edit-details)   | Matches the tags in Radarr for every movie found by the builders that's in Radarr with the provided tags<hr>**Values:** List or comma-separated string of tags |

## Sonarr Details

All the following attributes can override the global/library [Sonarr](../../config/sonarr) attributes which are the default unless otherwise specified.

| Attribute                                     | Description & Values                                                                                                                                            |
|:----------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [`sonarr_add_missing`](#arr-add-missing)      | Override Sonarr `add` attribute<hr>**Values:** `true` or `false`                                                                                                |
| [`sonarr_add_existing`](#arr-add-existing)    | Override Sonarr `add_existing` attribute<hr>**Values:** `true` or `false`                                                                                       |
| [`sonarr_folder`](#radarr-add-details)        | Override Sonarr `root_folder_path` attribute<hr>**Values:** Folder Path                                                                                         |
| [`sonarr_monitor`](#radarr-add-details)       | Override Sonarr `monitor` attribute<hr>**Values:** `all`, `future`, `missing`, `existing`, `pilot`, `first`, `latest`, `none`                                   |
| [`sonarr_quality`](#radarr-add-details)       | Override Sonarr `quality_profile` attribute<hr>**Values:** Sonarr Quality Profile                                                                               |
| [`sonarr_language`](#radarr-add-details)      | Override Sonarr `language_profile` attribute<hr>**Values:** Sonarr Language Profile                                                                             |
| [`sonarr_series`](#radarr-add-details)        | Override Sonarr `series_type` attribute<hr>**Values:** `standard`, `daily`, `anime`                                                                             |
| [`sonarr_season`](#radarr-add-details)        | Override Sonarr `season_folder` attribute<hr>**Values:** `true` or `false`                                                                                      |
| [`sonarr_tag`](#radarr-add-details)           | Override Sonarr `tag` attribute<hr>**Values:** List or comma-separated string of tags                                                                           |
| [`sonarr_search`](#radarr-add-details)        | Override Sonarr `search` attribute<hr>**Values:** `true` or `false`                                                                                             |
| [`sonarr_cutoff_search`](#radarr-add-details) | Override Sonarr `cutoff_search` attribute<hr>**Values:** `true` or `false`                                                                                      |
| [`item_sonarr_tag`](#arr-edit-details)        | Used to append a tag in Sonarr for every series found by the builders that's in Sonarr<hr>**Values:** List or comma-separated string of tags                    |
| [`item_sonarr_tag.remove`](#arr-edit-details) | Used to remove existing tags in Sonarr for every series found by the builders that's in Sonarr<hr>**Values:** List or comma-separated string of tags            |
| [`item_sonarr_tag.sync`](#arr-edit-details)   | Matches the tags in Sonarr for every series found by the builders that's in Sonarr with the provided tags<hr>**Values:** List or comma-separated string of tags |

### Arr Add Missing

When `radarr_add_missing`/`sonarr_add_missing` are true the items missing from the collection/playlist will be added to Radarr/Sonarr.

### Arr Add Existing

When `radarr_add_existing`/`sonarr_add_existing` are true the items that exist in the collection/playlist will be added to Radarr/Sonarr.

### Radarr Add Details

When adding a movie in Radarr you get the screen below to set these options use `radarr_folder`, `radarr_monitor`, `radarr_availability`, `radarr_quality`, `radarr_tag`, and `radarr_search`.

![Radarr Details](radarr.png)

### Sonarr Add Details

When adding a movie in Sonarr you get the screen below to set these options use `sonarr_folder`, `sonarr_monitor`, `sonarr_quality`, `sonarr_language`, `sonarr_series`, `sonarr_season`, `sonarr_tag`, `sonarr_search`, and `sonarr_cutoff_search`.

![Sonarr Details](sonarr.png)

### Arr Edit Details

When editing the details of items that exist in the collection/playlist and in Radarr/Sonarr use `item_radarr_tag` and `item_sonarr_tag`