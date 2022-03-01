# Arr Details

## Radarr Details

All the following attributes can override the global/library [Radarr](../../config/radarr) attributes which are the default unless otherwise specified.

| Name                                          | Attribute                | Description                                                                                              | Allowed Values                           | Works with Playlists |
|:----------------------------------------------|:-------------------------|:---------------------------------------------------------------------------------------------------------|:-----------------------------------------|:--------------------:|
| [Radarr Add Missing](#arr-add-missing)        | `radarr_add_missing`     | Override Radarr `add` attribute                                                                          | **boolean:** `true` or `false`           |       &#9989;        |
| [Radarr Add Existing](#arr-add-existing)      | `radarr_add_existing`    | Override Radarr `add_existing` attribute                                                                 | **boolean:** `true` or `false`           |       &#9989;        |
| [Radarr Root Folder](#radarr-add-details)     | `radarr_folder`          | Override Radarr `root_folder_path` attribute                                                             | Folder Path                              |       &#9989;        |
| [Radarr Monitor](#radarr-add-details)         | `radarr_monitor`         | Override Radarr `monitor` attribute                                                                      | **boolean:** `true` or `false`           |       &#9989;        |
| [Radarr Availability](#radarr-add-details)    | `radarr_availability`    | Override Radarr `availability` attribute                                                                 | `announced`, `cinemas`, `released`, `db` |       &#9989;        |
| [Radarr Quality Profile](#radarr-add-details) | `radarr_quality`         | Override Radarr `quality_profile` attribute                                                              | Radarr Quality Profile                   |       &#9989;        |
| [Radarr Tag](#radarr-add-details)             | `radarr_tag`             | Override Radarr `tag` attribute                                                                          | List or comma-separated string of tags   |       &#9989;        |
| [Radarr Search](#radarr-add-details)          | `radarr_search`          | Override Radarr `search` attribute                                                                       | **boolean:** `true` or `false`           |       &#9989;        |
| [Item Radarr Tag](#arr-edit-details)          | `item_radarr_tag`        | Used to append a tag in Radarr for every movie found by the builders that's in Radarr                    | List or comma-separated string of tags   |       &#9989;        |
| [Item Radarr Tag Remove](#arr-edit-details)   | `item_radarr_tag.remove` | Used to remove existing tags in Radarr for every movie found by the builders that's in Radarr            | List or comma-separated string of tags   |       &#9989;        |
| [Item Radarr Tag Sync](#arr-edit-details)     | `item_radarr_tag.sync`   | Matches the tags in Radarr for every movie found by the builders that's in Radarr with the provided tags | List or comma-separated string of tags   |       &#9989;        |

## Sonarr Details

All the following attributes can override the global/library [Sonarr](../../config/sonarr) attributes which are the default unless otherwise specified.

| Name                                           | Attribute                | Description                                                                                               | Allowed Values                                                             | Works with Playlists |
|:-----------------------------------------------|:-------------------------|:----------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------|:--------------------:|
| [Sonarr Add](#arr-add-missing)                 | `sonarr_add_missing`     | Override Sonarr `add` attribute                                                                           | **boolean:** `true` or `false`                                             |       &#9989;        |
| [Sonarr Add Existing](#arr-add-existing)       | `sonarr_add_existing`    | Override Sonarr `add_existing` attribute                                                                  | **boolean:** `true` or `false`                                             |       &#9989;        |
| [Sonarr Root Folder](#radarr-add-details)      | `sonarr_folder`          | Override Sonarr `root_folder_path` attribute                                                              | Folder Path                                                                |       &#9989;        |
| [Sonarr Monitor](#radarr-add-details)          | `sonarr_monitor`         | Override Sonarr `monitor` attribute                                                                       | `all`, `future`, `missing`, `existing`, `pilot`, `first`, `latest`, `none` |       &#9989;        |
| [Sonarr Quality Profile](#radarr-add-details)  | `sonarr_quality`         | Override Sonarr `quality_profile` attribute                                                               | Sonarr Quality Profile                                                     |       &#9989;        |
| [Sonarr Language Profile](#radarr-add-details) | `sonarr_language`        | Override Sonarr `language_profile` attribute                                                              | Sonarr Language Profile                                                    |       &#9989;        |
| [Sonarr Series Type](#radarr-add-details)      | `sonarr_series`          | Override Sonarr `series_type` attribute                                                                   | `standard`, `daily`, `anime`                                               |       &#9989;        |
| [Sonarr Season Folder](#radarr-add-details)    | `sonarr_season`          | Override Sonarr `season_folder` attribute                                                                 | **boolean:** `true` or `false`                                             |       &#9989;        |
| [Sonarr Tag](#radarr-add-details)              | `sonarr_tag`             | Override Sonarr `tag` attribute                                                                           | List or comma-separated string of tags                                     |       &#9989;        |
| [Sonarr Search](#radarr-add-details)           | `sonarr_search`          | Override Sonarr `search` attribute                                                                        | **boolean:** `true` or `false`                                             |       &#9989;        |
| [Sonarr Cutoff Search](#radarr-add-details)    | `sonarr_cutoff_search`   | Override Sonarr `cutoff_search` attribute                                                                 | **boolean:** `true` or `false`                                             |       &#9989;        |
| [Item Sonarr Tag](#arr-edit-details)           | `item_sonarr_tag`        | Used to append a tag in Sonarr for every series found by the builders that's in Sonarr                    | List or comma-separated string of tags                                     |       &#9989;        |
| [Item Sonarr Tag Remove](#arr-edit-details)    | `item_sonarr_tag.remove` | Used to remove existing tags in Sonarr for every series found by the builders that's in Sonarr            | List or comma-separated string of tags                                     |       &#9989;        |
| [Item Sonarr Tag Sync](#arr-edit-details)      | `item_sonarr_tag.sync`   | Matches the tags in Sonarr for every series found by the builders that's in Sonarr with the provided tags | List or comma-separated string of tags                                     |       &#9989;        |

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