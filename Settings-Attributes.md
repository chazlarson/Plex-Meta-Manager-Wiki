Configuring different options for Plex Meta Manager can be done in the Settings. These include enabling a cache to store each Plex GUID and its accompanying IDs to vastly speed up the execution of the script, defining the Image Asset Directory for local assets, setting a global Sync Mode, and many other display features.

A `settings` mapping can be either in the root of the config file as global mapping for all libraries or you can specify the `settings` mapping individually per library. Some settings can be individually set per collection using [Collection Details](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Collection-Details).

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
  playlist_sync_to_user: all
  verify_ssl: true
```

| Name | Attribute | Allowed Values | Global Level | Library Level | Collection/Playlist Level |
| :--- | :--- | :--- | :---: | :---: | :---: |
| [Cache](#cache) | `cache` | **boolean:** true or false<br>**default: true** | :heavy_check_mark: | :x: | :x: |
| [Cache Expiration](#cache) | `cache_expiration` | **integer**<br>**default: 60** | :heavy_check_mark: | :x: | :x: |
| [Image Asset Directory](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Image-Asset-Directory) | `asset_directory` | **list of paths**<br>**default: [Directory containing YAML config]/assets** | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Image Asset Folders](#image-asset-folders) | `asset_folders` | **boolean:** true or false<br>**default: true** | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Asset Depth](#asset-depth) | `asset_depth` | **integer**<br>**default: 0** | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Create Asset Folders](#create-asset-folders) | `create_asset_folders` | **boolean:** true or false<br>**default: false** | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Dimensional Asset Rename](#dimensional-asset-rename) | `dimensional_asset_rename` | **boolean:** true or false<br>**default: false** | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Download URL Assets](#download-url-assets) | `download_url_assets` | **boolean:** true or false<br>**default: false** | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Show Missing Season Assets](#show-missing-season-assets) | `show_missing_season_assets` | **boolean:** true or false<br>**default: false** | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Sync Mode](#sync-mode) | `sync_mode` | `append` or `sync`<br>**default: append** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Default Collection Order](#default-collection-order) | `default_collection_order` | `release`: Order Collection by Release Dates<br>`alpha`: Order Collection Alphabetically<br>`custom`: Order Collection Via the Builder Order<br>[Any `plex_search` Sort Option](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Plex-Builders#sort-options) | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Minimum Items](#minimum-items) | `minimum_items` | **integer**<br>**default: 1** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Delete Below Minimum](#delete-below-minimum) | `delete_below_minimum` | **boolean:** true or false<br>**default: false** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Delete Not Scheduled](#delete-not-scheduled ) | `delete_not_scheduled ` | **boolean:** true or false<br>**default: false** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Run Again Delay](#run-again-delay) | `run_again_delay` | **integer**<br>**default: 0** | :heavy_check_mark: | :x: | :x: |
| [Missing Only Released](#missing-only-released) | `missing_only_released` | **boolean:** true or false<br>**default: false** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Only Filter Missing](#only-filter-missing) | `only_filter_missing` | **boolean:** true or false<br>**default: false** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Show Unmanaged Collections](#show-unmanaged-collections) | `show_unmanaged` | **boolean:** true or false<br>**default: true** | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Show Filtered](#show-filtered) | `show_filtered` | **boolean:** true or false<br>**default: false** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Show Missing](#show-missing) | `show_missing` | **boolean:** true or false<br>**default: true** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Show Missing Assets](#show-missing-assets) | `show_missing_assets` | **boolean:** true or false<br>**default: true** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Save Missing](#save-missing) | `save_missing` | **boolean:** true or false<br>**default: true** | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [TVDb Language](#tvdb-language) | `tvdb_language` | [ISO 639-2 Language Code](https://en.wikipedia.org/wiki/List_of_ISO_639-2_codes) or Blank for original Language<br>**default:**  | :heavy_check_mark: | :x: | :x: |
| [Ignore IDs](#ignore-ids) | `ignore_ids` | List or comma-separated String of TMDb/TVDb IDs | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | 
| [Ignore IMDb IDs](#ignore-imdb-ids) | `ignore_imdb_ids` | List or comma-separated String of IMDb IDs | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| [Playlist Sync to User](#playlist-sync-to-user) | `playlist_sync_to_user` | `all` or List or comma-separated String of Users to sync the playlist to.<br>**default: `all`** | :heavy_check_mark: | :x: | :heavy_check_mark: |
| [Verify SSL](#verify-ssl) | `verify_ssl` | Turn SSL Verification on or off. | :heavy_check_mark: | :x: | :x: |
| [Missing Path](#missing-path) | `missing_path` | Path to missing YAML file for the library | :x: | :heavy_check_mark: | :x: |

## Cache
Will use a cached database for faster processing. The cache file is created in the same location as your config file.

You can change the number of `cache_expiration` to set the number of days before each cache mapping expires and has to be reloaded

## Image Asset Folders
When searching [Image Asset Directories](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Image-Asset-Directory) search for named folders vs named files<br>i.e. `assets/Star Wars.png` vs `assets/Star Wars/poster.png`.

## Asset Depth
When using `asset_folders` this determines how many folder levels deep you want to search for an item.

## Create Asset Folders
When using the `assets_for_all` [Library Operation](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Operations-Attributes) folders will be created for each Item in your library for assets to be placed in.

## Dimensional Asset Rename
When using `asset_folders` this will scan the folder for image files and rename the first image found that has a height greater than its width to `poster.ext` as long as an asset poster was not found and the first image found that has a width greater than its height to `background.ext` as long as an asset background was not found.

## Download URL Assets
When using `download_url_assets` if you are using `url_poster` or `url_background` in your collection config this will download the image to your asset folder if no image is found.

## Show Missing Season Assets
When searching for assets for a show if a Season poster is found then this will display all other missing Season posters.

## Sync Mode
Set the default `sync_mode`. It can be either `append` when you want to add only and `sync` when you want to add and remove from collections.

## Default Collection Order
Sets the `collection_order` for every collection run You can use any of these options:

* `release`: Order Collection by Release Dates
* `alpha`: Order Collection Alphabetically
* `custom`: Order Collection Via the Builder Order
* [Any `plex_search` Sort Option](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Plex-Builders#sort-options)

## Minimum Items
Minimum number of items that must be found in order to update a collection/playlist.

## Delete Below Minimum
When a collection is run it will be deleted if it is below the minimum specified by `minimum_items`.

## Delete Not Scheduled
When a collection is skipped due to it not being scheduled delete it.

## Run Again Delay
Number of minutes to run `run_again` collections after daily run is finished.

A collection is a `run_again` collection if it has the `run_again` [Collection Detail](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Collection-Details#setting-details) attribute set to true.

## Missing Only Released
Library Level toggle to filter missing items from a collection that has yet to be released.

## Only Filter Missing
Library Level toggle to only filter missing items from a collection.

## Show Unmanaged Collections
Show collections not managed by Plex Meta Manager at the end of each run.

## Show Filtered
Library Level toggle to show items filtered from collections.

## Show Missing
Library Level toggle to show items missing from collections

## Show Missing Assets
Library Level toggle to silence missing assets warnings.

## Save Missing
Library Level toggle to save items missing from collections to a filein the same directory as your Metadata file.

## TVDb Language
Use an [ISO 639-2 Language Code](https://en.wikipedia.org/wiki/List_of_ISO_639-2_codes) to specify the language to query TVDb in.

If no language is specified or the specified language is not found then the original language is used.

## Ignore IDs
List or comma-separated String of TMDb/TVDb IDs to ignore in all collections

## Ignore IMDb IDs
List or comma-separated String of IMDb IDs to ignore in all collections

## Playlist Sync to User
`all` or List or comma-separated String of Users to sync the playlist to in addition to yourself. To Sync a playlist to only yourself leave `sync_to_user` blank. Defaults to `all`.

## Verify SSL
Turn SSl Verification on or off.

## Missing Path
Path where to save the missing YAML File. Default is `/config/<<library_name>>_missing.yml` where `<<library_name>>` is your library name.

* This setting can only be set under setting for each particular library.

```yaml
libraries:
  Movies:
    settings:
      missing_path: /config/Missing/Movies.yml
```
