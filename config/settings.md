# Settings Definition & Attributes

## Overview
The `settings:` definition and subsequent attributes can be used to command various aspects of the functions and actions that Plex Meta Manager performs. 

Examples of these attributes include the ability to:
* Cache each Plex GUID and IDs to increase performance
* Create asset folders for collections so that custom posters can be stored for upload.
* Use a custom repository as the base for all `git` Metadata files. 

The settings definition and attributes can be specified individually per library, or can be inhereted from the global value if it has been set. If an attribute is specified at both the library and global level, then the library level attribute will take priority.

There are some attributes which can be specified at the collection level using [Setting Details](../metadata/details/setting). Attributes set at the collection label will take priority over any library or global-level attribute.

## Attributes

The available setting attributes which can be set at each level are outlined below:


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
| [Show Unmanaged Collections](#show-unmanaged-collections)   | `show_unmanaged`              |   &#9989;    |    &#9989;    |         &#10060;          |
| [Show Filtered](#show-filtered)                             | `show_filtered`               |   &#9989;    |    &#9989;    |          &#9989;          |
| [Show Options](#show-options)                               | `show_options`                |   &#9989;    |    &#9989;    |          &#9989;          |
| [Show Missing](#show-missing)                               | `show_missing`                |   &#9989;    |    &#9989;    |          &#9989;          |
| [Only Filter Missing](#only-filter-missing)                 | `only_filter_missing`         |   &#9989;    |    &#9989;    |          &#9989;          |
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
Cache the Plex GUID and associated IDs for each library item for faster subsequent processing. The cache file is created in the same directory as the configuration file. 

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>true</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Cache Expiration
Set the number of days before each cache mapping expires and has to be re-cached.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>60</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td>any integer</td>
  </tr>
</table>

## Image Asset Directory
Specify the directory where assets are located.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>[Directory containing YAML config]/assets</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td>any directory</td>
  </tr>
</table>

## Image Asset Folders
Search the `asset_directory` for a dedicated folder. Set to true if each poster is within its own directory.<br>
i.e. `assets/Star Wars/poster.png` instead of `assets/Star Wars.png`

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>true</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Asset Depth
Specify how many folder levels to scan for an item within the asset directory<br>
* `asset_folders` must be set to `true` for this to take effect.
* increasing the amount of levels to scan will reduce performance


<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>0</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td>any integer</td>
  </tr>
</table>

## Create Asset Folders
Whilst searching for assets, if an asset folder cannot be found within the `asset_directory`, create one. This only applies to library items utilized in a Metadata/Playlist file (i.e. Star Wars Collection)

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>false</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>


## Dimensional Asset Rename
Whilst searching for assets, scan the folders within the `asset_directory` and if an asset poster (i.e. `/ASSET_NAME/poster.ext`) was not found , rename the first image found that has a height greater than or equal to its width to `poster.ext`. If an asset background (i.e. `/ASSET_NAME/background.ext`), rename the first image found that has a width greater than its height to `background.ext`,
* `asset_folders` must be set to `true` for this to take effect.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>false</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Download URL Assets
Whilst searching for assets, download images set within Metadata/Playlist files( i.e. images set by `url_poster` or `url_background`) into the asset folder if none are already present.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>false</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Show Missing Season Assets
Whilst searching for assets, when scanning for assets for a TV Show, if Season posters are found (i.e. `/ASSET_NAME/Season##.ext`, notify the user of any seasons which do not have an asset image.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>false</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Show Missing Episode Assets
Whilst searching for assets, when scanning for assets for a TV Show, if an Episode Title Card is found (i.e. `/ASSET_NAME/S##E##.ext`), notify the user of any episodes which do not have an asset image.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>false</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Show Asset Not Needed
Whilst searching for assets, show or hide the `update not needed` messages.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>false</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Sync Mode
Set the default `sync_mode` for collections. 

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>append</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>append</code> or <code>sync</code>
    </td>
  </tr>
</table>

## Default Collection Order
Set the default `collection_order` for every collection run by PMM.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>None</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>release</code>: Order Collection by Release Dates<br>
    <code>alpha</code>: Order Collection Alphabetically<br>
    <code>custom</code>: Order Collection Via the Builder Order<br>
    Any <code>plex_search</code> sort option<sup>1</sup><br>
    </td>
  </tr>
</table>

<sup>1</sup> `plex_search` sort options can be found [here](../metadata/builders/plex.md#sort-options)

## Minimum Items
Set the minimum number of items that must be found in order to update a collection/playlist.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>1</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td>any integer</td>
  </tr>
</table>

## Delete Below Minimum
When a collection is run, delete the collection if it is below the minimum number specified by `minimum_items`.
* Relies on `minimum_items` being set to the desired integer.
<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>false</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Delete Not Scheduled
If a collection is skipped due to it not being scheduled, delete the collection.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>false</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Run Again Delay
Set the number of minutes to delay running `run_again` collections after daily run is finished.
* A collection is a `run_again` collection if it has the `run_again` [Setting Detail](../metadata/details/setting) attribute set to true.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>1</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td>any integer</td>
  </tr>
</table>

## Missing Only Released
Whilst running a collection, all unreleased missing items will be filtered out from the [missing YAML file](../metadata/details/setting)

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>false</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Show Unmanaged Collections
List all collections not managed by Plex Meta Manager at the end of each run.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>true</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Show Filtered
List all items which have been filtered out of a collection (i.e. if it doesn't meet the filter criteria)

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>false</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Show Options
While `show_options` is true the available options for an attribute when using `plex_search`, `smart_filter` or `filters` will be shown.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>false</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>


## Show Missing
While `show_missing` is true items missing from collections will be displayed.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>true</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Only Filter Missing
Only items missing from a collection will be filtered
* this can be used to filter which missing media items get sent to Sonarr/Radarr

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>false</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Show Missing Assets
Display missing asset warnings

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>true</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## Save Missing
Save missing items from collections to a YAML file in the same directory as your Metadata file.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>true</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>

## TVDb Language
Specify the language to query TVDb in. 
* If no language is specified or the specified language is not found then the original language is used.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>None</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td>Any ISO 639-2 Language Code<sup>1</sup></td>
  </tr>
</table>

<sup>1</sup> Language Codes can be found [here](https://en.wikipedia.org/wiki/List_of_ISO_639-2_codes)

## Ignore IDs
Set a list or comma-separated string of TMDb/TVDb IDs to ignore in all collections.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>None</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td>List or comma-separated string of TMDb/TVDb IDs</td>
  </tr>
</table>

## Ignore IMDb IDs
Set alist or comma-separated string of IMDb IDs to ignore in all collections.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>None</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td>List or comma-separated string of IMDB IDs</td>
  </tr>
</table>

## Item Refresh Delay
Specify the amount of time to wait between each `item_refresh` of every movie/show in a collection/playlist.
* Useful if your Plex Media Server is having issues with high request levels.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>0</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td>any integer</td>
  </tr>
</table>

## Playlist Sync to Users
Set the default playlist `sync_to_users`. To Sync a playlist to only yourself leave `playlist_sync_to_users` blank.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>all</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>all</code>, list of users, or comma-separated string of users</td>
  </tr>
</table>

## Custom Repo
Specify where the `repo` attribute's base is when defining `metadata_paths` and `playlist_files`.
* Ensure you are using the raw GitHub link (i.e. https://github.com/meisnate12/Plex-Meta-Manager-Configs/tree/master/meisnate12 )
<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>None</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td>link to base repository</td>
  </tr>
</table>

## Verify SSL
Turn SSl Verification on or off.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Default Value</th>
    <td><code>true</code></td>
  </tr>
  <tr>
    <th>Allowed Values</th>
    <td><code>true</code> or <code>false</code>
    </td>
  </tr>
</table>