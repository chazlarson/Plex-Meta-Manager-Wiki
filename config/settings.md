# Settings Attributes

Configuring different options for Plex Meta Manager can be done in the Settings. These include enabling a cache to store each Plex GUID and its accompanying IDs to vastly speed up the execution of the script, defining the Image Asset Directory for local assets, setting a global Sync Mode, and many other display features.

A `settings` mapping can be either in the root of the config file as global mapping for all libraries or you can specify the `settings` mapping individually per library. Some settings can be individually set per collection using [Setting Details](../metadata/details/setting).

Below is a `settings` mapping example and the full set of attributes:
```yaml
settings:
  cache: true
  cache_expiration: 60
  asset_directory: config/assets
  asset_folders: true
  asset_depth: 0
  create_asset_folders: false
  dimensional_asset_rename: false
  download_url_assets: false
  show_missing_season_assets: false
  show_missing_episode_assets: false
  show_asset_not_needed: true
  sync_mode: append
  collection_minimum: 1
  delete_below_minimum: true
  delete_not_scheduled: false
  run_again_delay: 2
  missing_only_released: false
  only_filter_missing: false
  show_unmanaged: true
  show_filtered: false
  show_options: false
  show_missing: true
  show_missing_assets: true
  save_missing: true
  tvdb_language: eng
  ignore_ids:
  ignore_imdb_ids:
  item_refresh_delay: 0
  playlist_sync_to_users: all
  verify_ssl: true
```

| Name                                                        | Attribute                     | Global Level | Library Level | Collection/Playlist Level |
|:------------------------------------------------------------|:------------------------------|:------------:|:-------------:|:-------------------------:|
| [Cache](#cache)                                             | `cache`                       |   &#9989;    |   &#10060;    |         &#10060;          |
| [Cache Expiration](#cache-expiration)                       | `cache_expiration`            |   &#9989;    |   &#10060;    |         &#10060;          |
| [Image Asset Directory](#image-asset-directory)             | `asset_directory`             |   &#9989;    |    &#9989;    |         &#10060;          |
| [Image Asset Folders](#image-asset-folders)                 | `asset_folders`               |   &#9989;    |    &#9989;    |         &#10060;          |
| [Asset Depth](#asset-depth)                                 | `asset_depth`                 |   &#9989;    |    &#9989;    |         &#10060;          |
| [Create Asset Folders](#create-asset-folders)               | `create_asset_folders`        |   &#9989;    |    &#9989;    |         &#10060;          |
| [Dimensional Asset Rename](#dimensional-asset-rename)       | `dimensional_asset_rename`    |   &#9989;    |    &#9989;    |         &#10060;          |
| [Download URL Assets](#download-url-assets)                 | `download_url_assets`         |   &#9989;    |    &#9989;    |         &#10060;          |
| [Show Missing Season Assets](#show-missing-season-assets)   | `show_missing_season_assets`  |   &#9989;    |    &#9989;    |         &#10060;          |
| [Show Missing Episode Assets](#show-missing-episode-assets) | `show_missing_episode_assets` |   &#9989;    |    &#9989;    |         &#10060;          |
| [Show Asset Not Needed](#show-asset-not-needed)             | `show_asset_not_needed`       |   &#9989;    |    &#9989;    |         &#10060;          |
| [Sync Mode](#sync-mode)                                     | `sync_mode`                   |   &#9989;    |    &#9989;    |          &#9989;          |
| [Default Collection Order](#default-collection-order)       | `default_collection_order`    |   &#9989;    |    &#9989;    |         &#10060;          |
| [Minimum Items](#minimum-items)                             | `minimum_items`               |   &#9989;    |    &#9989;    |          &#9989;          |
| [Delete Below Minimum](#delete-below-minimum)               | `delete_below_minimum`        |   &#9989;    |    &#9989;    |          &#9989;          |
| [Delete Not Scheduled](#delete-not-scheduled)               | `delete_not_scheduled `       |   &#9989;    |    &#9989;    |          &#9989;          |
| [Run Again Delay](#run-again-delay)                         | `run_again_delay`             |   &#9989;    |   &#10060;    |         &#10060;          |
| [Missing Only Released](#missing-only-released)             | `missing_only_released`       |   &#9989;    |    &#9989;    |          &#9989;          |
| [Only Filter Missing](#only-filter-missing)                 | `only_filter_missing`         |   &#9989;    |    &#9989;    |          &#9989;          |
| [Show Unmanaged Collections](#show-unmanaged-collections)   | `show_unmanaged`              |   &#9989;    |    &#9989;    |         &#10060;          |
| [Show Filtered](#show-filtered)                             | `show_filtered`               |   &#9989;    |    &#9989;    |          &#9989;          |
| [Show Options](#show-options)                               | `show_options`                |   &#9989;    |    &#9989;    |          &#9989;          |
| [Show Missing](#show-missing)                               | `show_missing`                |   &#9989;    |    &#9989;    |          &#9989;          |
| [Show Missing Assets](#show-missing-assets)                 | `show_missing_assets`         |   &#9989;    |    &#9989;    |          &#9989;          |
| [Save Missing](#save-missing)                               | `save_missing`                |   &#9989;    |    &#9989;    |          &#9989;          |
| [TVDb Language](#tvdb-language)                             | `tvdb_language`               |   &#9989;    |   &#10060;    |         &#10060;          |
| [Ignore IDs](#ignore-ids)                                   | `ignore_ids`                  |   &#9989;    |    &#9989;    |          &#9989;          | 
| [Ignore IMDb IDs](#ignore-imdb-ids)                         | `ignore_imdb_ids`             |   &#9989;    |    &#9989;    |          &#9989;          |
| [Item Refresh Delay](#item-refresh-delay)                   | `item_refresh_delay`          |   &#9989;    |    &#9989;    |          &#9989;          |
| [Playlist Sync to Users](#playlist-sync-to-users)           | `playlist_sync_to_users`      |   &#9989;    |   &#10060;    |          &#9989;          |
| [Custom Repo](#custom-repo)                                 | `custom_repo`                 |   &#9989;    |   &#10060;    |         &#10060;          |
| [Verify SSL](#verify-ssl)                                   | `verify_ssl`                  |   &#9989;    |   &#10060;    |         &#10060;          |

## Cache
While `cache` is true a cached database will be created and used for faster processing. The cache file is created in the same location as your config file.

**Default Value:** `true`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Cache Expiration
You can change the number of `cache_expiration` to set the number of days before each cache mapping expires and has to be reloaded.

**Default Value:** `60`<br>
**Allowed Values:** `integer`

## Image Asset Directory
Use `asset_directory` to specify the folders where assets should be searched for.

**Default Value:**  [Directory containing YAML config]/assets<br>
**Allowed Values:** list of paths

## Image Asset Folders
While `asset_folders` is true search using named folders and while it's false search using named files<br>i.e. `assets/Star Wars.png` vs `assets/Star Wars/poster.png`.

**Default Value:** `true`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Asset Depth
`asset_depth` determines how many folder levels deep you want to search for an item in the asset directory higher values will take longer. 

**Default Value:** `0`<br>
**Allowed Values:** `integer`<br>
**Requires:** `asset_folders: true`

## Create Asset Folders
While `create_asset_folders` is true then whenever PMM looks for an asset folder and cannot find it then it will be created.

**Default Value:** `false`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Dimensional Asset Rename
While `dimensional_asset_rename` is true when scanning for assets PMM will scan the folder for image files and rename the first image found that has a height greater than or equal to its width to `poster.ext`, as long as an asset poster was not found, and the first image found that has a width greater than its height to `background.ext`, as long as an asset background was not found.

**Default Value:** `false`<br>
**Allowed Values:** `boolean`: `true` or `false`<br>
**Requires:** `asset_folders: true`

## Download URL Assets
While `download_url_assets` is true PMM will automatically download images in your collection config (Images set by `url_poster` or `url_background`) to your asset folder if no asset is found.

**Default Value:** `false`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Show Missing Season Assets
While `show_missing_season_assets` is true when searching for assets for a show if a Season poster is found then this will display all other missing Season posters.

**Default Value:** `false`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Show Missing Episode Assets
While `show_missing_episode_assets` is true when searching for assets for a show if an Episode Title Card is found then this will display all other missing Episode Title Cards.

**Default Value:** `false`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Show Asset Not Needed
While `show_asset_not_needed` is true when searching for assets show or hide the `update not needed` Messages.

**Default Value:** `false`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Sync Mode
Set the default `sync_mode` for collection. It can be either `append` when you want to add only and `sync` when you want to add and remove from collections.

**Default Value:** `append`<br>
**Allowed Values:** `append` or `sync`

## Default Collection Order
Use `default_collection_order` to set the default `collection_order` for every collection run by PMM. You can use any of these options:

**Default Value:** None<br>
**Allowed Values:** 
* `release`: Order Collection by Release Dates
* `alpha`: Order Collection Alphabetically
* `custom`: Order Collection Via the Builder Order
* [Any `plex_search` Sort Option](../metadata/builders/plex.md#sort-options)

## Minimum Items
Use `minimum_items` to set the minimum number of items that must be found in order to update a collection/playlist.

**Default Value:** `1`<br>
**Allowed Values:** `integer`

## Delete Below Minimum
While `delete_below_minimum` is true and a collection is run it will be deleted if it is below the minimum number specified by `minimum_items`.

**Default Value:** `false`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Delete Not Scheduled
While `delete_below_minimum` is true and a collection is skipped due to it not being scheduled then it is deleted.

**Default Value:** `false`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Run Again Delay
Use `run_again_delay` to set the number of minutes to delay running `run_again` collections after daily run is finished.

A collection is a `run_again` collection if it has the `run_again` [Setting Detail](../metadata/details/setting) attribute set to true.

**Default Value:** `1`<br>
**Allowed Values:** `integer`

## Missing Only Released
While `missing_only_released` is true then all unreleased missing items from a collection will be filtered out.

**Default Value:** `false`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Only Filter Missing
While `only_filter_missing` is true then only items missing from a collection will be filtered.

**Default Value:** `false`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Show Unmanaged Collections
While `show_unmanaged` is true all collections not managed by Plex Meta Manager will be listed at the end of each run.

**Default Value:** `true`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Show Filtered
While `show_filtered` is true all items filtered out from a collection will be displayed.

**Default Value:** `false`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Show Options
While `show_options` is true the available options for an attribute when using `plex_search`, `smart_filter` or `filters` will be shown.

**Default Value:** `false`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Show Missing
While `show_missing` is true items missing from collections will be displayed.

**Default Value:** `true`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Show Missing Assets
While `show_missing_assets` is true missing assets warnings will be displayed.

**Default Value:** `true`<br>
**Allowed Values:** `boolean`: `true` or `false`

## Save Missing
While `save_missing` is true missing items from collections will be saved to a file in the same directory as your Metadata file.

**Default Value:** `true`<br>
**Allowed Values:** `boolean`: `true` or `false`

## TVDb Language
Use `tvdb_language` to specify the language to query TVDb in. If no language is specified or the specified language is not found then the original language is used.

**Default Value:** None<br>
**Allowed Values:** [ISO 639-2 Language Code](https://en.wikipedia.org/wiki/List_of_ISO_639-2_codes)

## Ignore IDs
Use `ignore_ids` to set a list or comma-separated string of TMDb/TVDb IDs to ignore in all collections.

**Default Value:** None<br>
**Allowed Values:** List or comma-separated string of TMDb/TVDb IDs

## Ignore IMDb IDs
Use `ignore_imdb_ids` to set a list or comma-separated string of IMDb IDs to ignore in all collections.

**Default Value:** None<br>
**Allowed Values:** List or comma-separated string of IMDb IDs

## Item Refresh Delay
Use `item_refresh_delay` to specify the amount of time to wait between each `item_refresh` of every movie/show in a collection/playlist.

**Default Value:** `0`<br>
**Allowed Values:** `integer`

## Playlist Sync to Users
Use `playlist_sync_to_users` to set the default playlist `sync_to_users`. To Sync a playlist to only yourself leave `playlist_sync_to_users` blank.

**Default Value:** `all`<br>
**Allowed Values:** `all`, list of users, or comma-separated string of users

## Custom Repo
Use `custom_repo` to define where the `repo` attribute's base is when defining `metadata_paths` and `playlist_files`.

**Default Value:** None<br>
**Allowed Values:** Link to Repo Base

* If you want to link you're own GitHub make sure you're using the raw link like below.
  `https://raw.githubusercontent.com/zluckytraveler/Plex-Meta-Manager-Configs/master/zluckytraveler/`

## Verify SSL
Turn SSl Verification on or off.

**Default Value:** `true`<br>
**Allowed Values:** `boolean`: `true` or `false`
