Configuring [Sonarr](https://sonarr.tv/) is optional but will allow you to send shows to a Sonarr instance when they're found missing while updating a library's collections.

Sonarr V2 may work, but it is not supported please upgrade to V3 if you can.

A `sonarr` mapping can be either in the root of the config file as global mapping for all libraries or you can specify the `sonarr` mapping individually per library.

Below is a `sonarr` mapping example and the full set of attributes:
```YAML
sonarr:
  url: http://192.168.1.12:32789
  token: ################################
  add: true
  root_folder_path: S:/Shows
  monitor: all
  quality_profile: HD-1080p
  language_profile: English
  series_type: standard
  season_folder: true
  tag: pmm
  search: false
  cutoff_search: false
  sonarr_path: /media
  plex_path: /share/CACHEDEV1_DATA/Multimedia
```

| Name | Attribute | Allowed Values| Default | Required |
| :--- | :--- | :--- | :---: | :---: |
| Sonarr URL | `url` | Sonarr URL (Including URL Base if set)<br>**Example:** http://192.168.1.12:32788 | N/A | :heavy_check_mark: |
| API Token | `token` | Sonarr API Token | N/A | :heavy_check_mark: |
| Add | `add` | Add missing shows found to Sonarr<br>**boolean:** true or false | false | :x: |
| Add Existing | `add_existing` | Add shows existing in this collection to Sonarr<br>**boolean:** true or false | false | :x: |
| Root Folder Path | `root_folder_path` | Sonarr Root Folder Path To Use | N/A | :heavy_check_mark: |
| Monitor | `monitor` | `all`: Monitor all episodes except specials<br>`future`: Monitor episodes that have not aired yet<br>`missing`: Monitor episodes that do not have files or have not aired yet<br>`existing`: Monitor episodes that have files or have not aired yet<br>`pilot`: Monitor the first episode. All other episodes will be ignored<br>`first`: Monitor all episodes of the first season. All other seasons will be ignored<br>`latest`: Monitor all episodes of the latest season and future seasons<br>`none`: No episodes will be monitored | `all` | :x: |
| Quality Profile | `quality_profile` | Quality Profile To Use | N/A | :heavy_check_mark: |
| Language Profile | `language_profile` | Language Profile To Use (v3 Only) | First Profile | :x: |
| Series Type | `series_type` | `standard`: Episodes released with SxxEyy pattern<br>`daily`: Episodes released daily or less frequently that use year-month-day (2017-05-25)<br>`anime`: Episodes released using an absolute episode number | `standard` | :x: |
| Season Folder | `season_folder` | Use the Season Folder Option when adding to Sonarr<br>**boolean:** true or false | true | :x: |
| Tag | `tag` | Add this list or comma-separated string of tags to every show added to Sonarr | ` ` | :x: |
| Search | `search` | Start search for missing episodes<br>**boolean:** true or false | false | :x: |
| Cutoff Search | `cutoff_search` | Start search for cutoff unmet episodes<br>**boolean:** true or false | false | :x: |
| Plex Path | `plex_path` | When using `add_existing` or `sonarr_add_all` Convert this part of the path to `sonarr_path` | ` ` | :x: |
| Sonarr Path | `sonarr_path` | When using `add_existing` or `sonarr_add_all` Convert the `plex_path` part of the path to this | ` ` | :x: |

* The `token` can be found by going to `Sonarr > Settings > General > Security > API Key`

* The `quality_profile` and `language_profile` must be the exact name of the desired quality profile, including all spaces and capitalization.

* You can set most attributes per collection by using the [Sonarr Collection Detail](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Collection-Details#sonarr-attributes)
 
![Sonarr Details](https://raw.githubusercontent.com/wiki/meisnate12/Plex-Meta-Manager/sonarr1.png)
