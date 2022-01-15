## Metadata Details
All the following attributes update various details of the collection/playlist's Metadata.

| Name | Attribute | Description | Allowed Values | Works with Playlists |
| :--- | :--- | :--- | :--- | :---: |
| TMDb Person | `tmdb_person` | Used to change the collection/playlist's summary and poster to a TMDb Person's biography and profile as well as allow the people specified to be used in [Plex Searches](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Plex-Builders#plex-search) | TMDb Person ID (List or Comma-separated string) | :heavy_check_mark: |
| Sort Title | `sort_title` | Used to change the collection's sort title | Text to change Sort Title | :x: |
| Content Rating | `content_rating` | Used to change the collection's content rating | Text to change Content Rating | :x: |
| Label | `label` | Used to append new labels to the collection | Comma-separated string of labels to append | :x: |
| Label Remove | `label.remove` | Used to remove existing labels from the collection | Comma-separated string of labels to remove | :x: |
| Label Sync | `label.sync` | Matches the labels of the collection to the labels provided (Leave blank to remove all labels) | Comma-separated string of labels to sync | :x: |
| Collection Mode | `collection_mode` | Used to change the Collection Mode | `default`: Library default<br>`hide`: Hide Collection<br>`hide_items`: Hide Items in this Collection<br>`show_items`: Show this Collection and its Items | :x: |
| Collection Order | `collection_order` | Used to change the Collection Order | `release`: Order Collection by Release Dates<br>`alpha`: Order Collection Alphabetically<br>`custom`: Order Collection Via the Builder Order<br>[Any `plex_search` Sort Option](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Plex-Builders#sort-options) | :heavy_check_mark: | :heavy_check_mark: | :x: |
| Collection Level | `collection_level` | Used to make season, episode, album or track collections from `plex_all`, `plex_search`, `trakt_list`, or `imdb_list` Builders and Filters | `season`: Collection contains seasons<br>`episode`: Collection contains episodes<br>`album`: Collection contains albums<br>`track`: Collection contains tracks | :x: |
| Visible on Library | `visible_library` | Used to change collection visible on Library (Only works with Plex Pass) | `true`: Visible<br>`false`: Not Visible<br>Any [`schedule`](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Schedule-Detail) | :x: |
| Visible on Home | `visible_home` | Used to change collection visible on Home (Only works with Plex Pass) | `true`: Visible<br>`false`: Not Visible<br>Any [`schedule`](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Schedule-Detail) | :x: |
| Visible on Shared | `visible_shared` | Used to change collection visible on Shared Users' Home (Only works with Plex Pass) | `true`: Visible<br>`false`: Not Visible<br>Any [`schedule`](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Schedule-Detail) | :x: |

* **Sort Title:** You can use `sort_title` to "promote" certain collections to the top of a library by creating a sort title starting with a `+` or "demote" certain collections to the bottom of a library by creating a sort title starting with a `~`.
* **Custom Collection Order:** When using `collection_order: custom` you can only have a single builder in the collection.

* Here's an example of how the collections can look on the Home Page.

![Display](https://raw.githubusercontent.com/wiki/meisnate12/Plex-Meta-Manager/display.png)

## Item Metadata Details
All the following attributes update various details of the metadata for every item in the collection/playlist.

| Name | Attribute | Description | Allowed Values | Works with Movies | Works with Shows | Works with Playlists |
| :--- | :--- | :--- | :--- | :---: | :---: | :---: |
| Label | `item_label` | Used to append new labels to every movie/show in the collection | Comma-separated string of labels to append | :heavy_check_mark: | :heavy_check_mark: | :x: |
| Label Remove | `item_label.remove` | Used to remove existing labels from every movie/show in the collection | Comma-separated string of labels to remove | :heavy_check_mark: | :heavy_check_mark: | :x: |
| Label Sync | `item_label.sync` | Matches the labels of every movie/show in the collection to the labels provided (Leave blank to remove all labels) | Comma-separated string of labels to sync | :heavy_check_mark: | :heavy_check_mark: | :x: |
| Lock Posters | `item_lock_poster` | Locks the poster of every movie/show in the collection | `true` or `false`<br>**Default:** false | :heavy_check_mark: | :heavy_check_mark: | :x: |
| Lock Backgrounds | `item_lock_background` | Locks the background of every movie/show in the collection | `true` or `false`<br>**Default:** false | :heavy_check_mark: | :heavy_check_mark: | :x: |
| Lock Titles | `item_lock_title` | Locks the title of every movie/show in the collection | `true` or `false`<br>**Default:** false | :heavy_check_mark: | :heavy_check_mark: | :x: |
| Image Overlay | `item_overlay` | Adds and overlay image to the poster of every movie/show in the collection | [`item_overlay` details](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Image-Overlay-Attribute) | :heavy_check_mark: | :heavy_check_mark: | :x: |
| Check For Assets | `item_assets` | Checks your assets folders for assets of every movie/show in the collection | `true` or `false`<br>**Default:** false | :heavy_check_mark: | :heavy_check_mark: | :x: |
| Refresh Item | `item_refresh` | Refreshes the metadata of every movie/show in the collection | `true` or `false`<br>**Default:** false | :heavy_check_mark: | :heavy_check_mark: | :x: |
| TMDb Season Titles | `item_tmdb_season_titles` | Changes the season titles of every show in the collection to match TMDb | `true` or `false`<br>**Default:** false | :x: | :heavy_check_mark: | :x: |
| Episode Sorting | `item_episode_sorting` | Changes the episode sorting of every show in the collection | `default`: Library default<br>`oldest`: Oldest first<br>`newest`: Newest first | :x: | :heavy_check_mark: | :x: |
| Keep Episodes | `item_keep_episodes` | Changes the keep episodes of every show in the collection | `all`: All episodes<br>`5_latest`: 5 latest episodes<br>`3_latest`: 3 latest episodes<br>`latest`: Latest episodes<br>`past_3`: Episodes added in the past 3 days<br>`past_7`: Episodes added in the past 7 days<br>`past_30`: Episodes added in the past 30 days | :x: | :heavy_check_mark: | :x: |
| Delete Episodes | `item_delete_episodes` | Changes the delete episodes of every show in the collection | `never`: Never<br>`day`: After a day<br>`week`: After a week<br>`refresh`: On next refresh | :x: | :heavy_check_mark: | :x: |
| Season Display | `item_season_display` | Changes the season display of every show in the collection | `default`: Library default<br>`show`: Show<br>`hide`: Hide | :x: | :heavy_check_mark: | :x: |
| Episode Ordering | `item_episode_ordering` | Changes the episode ordering of every show in the collection | `default`: Library default<br>`tmdb_aired`*: The Movie Database (Aired)<br>`tvdb_aired`: TheTVDB (Aired)<br>`tvdb_dvd`: TheTVDB (DVD)<br>`tvdb_absolute`: TheTVDB (Absolute) | :x: | :heavy_check_mark: | :x: |
| Metadata Language* | `item_metadata_language` | Changes the metadata language of every movie/show in the collection | `default`, `ar-SA`, `ca-ES`, `cs-CZ`, `da-DK`, `de-DE`, `el-GR`, `en-AU`, `en-CA`, `en-GB`, `en-US`, `es-ES`, `es-MX`, `et-EE`, `fa-IR`, `fi-FI`, `fr-CA`, `fr-FR`, `he-IL`, `hi-IN`, `hu-HU`, `id-ID`, `it-IT`, `ja-JP`, `ko-KR`, `lt-LT`, `lv-LV`, `nb-NO`, `nl-NL`, `pl-PL`, `pt-BR`, `pt-PT`, `ro-RO`, `ru-RU`, `sk-SK`, `sv-SE`, `th-TH`, `tr-TR`, `uk-UA`, `vi-VN`, `zh-CN`, `zh-HK`, `zh-TW` | :heavy_check_mark: | :heavy_check_mark: | :x: |
| Use Original Title* | `item_use_original_title` | Changes the use original title of every movie/show in the collection | `default`: Library default<br>`no`: No<br>`yes`: Yes | :heavy_check_mark: | :heavy_check_mark: | :x: |

\* Must be using the **New Plex Movie Agent** or the **New Plex TV Agent** 

## Summary Details
All the following attributes update the summary of the collection/playlist from various sources.

| Name | Attribute | Description | Allowed Values | Works with Playlists |
| :--- | :--- | :--- | :--- | :---: |
| Summary | `summary` | Used to change the collection/playlist's summary | Text to change Summary | :heavy_check_mark: |
| TMDb Summary | `tmdb_summary` | Used to change the collection/playlist's summary to the TMDb Movie/Collection summary for a movie library or the TMDb Show summary for a show library  | TMDb Movie/Show/Collection ID | :heavy_check_mark: |
| TMDb Description | `tmdb_description` | Used to change the collection/playlist's summary to the TMDb List Description | TMDb List ID | :heavy_check_mark: |
| TMDb Biography | `tmdb_biography` | Used to change the collection/playlist's summary to the TMDb Person's biography | TMDb Person ID | :heavy_check_mark: |
| TVDb Summary | `tvdb_summary` | Used to change the collection/playlist's summary to the TVDb Movie summary for a movie library or the TVDb Show summary for a show library  | TVDb Movie/Show ID or URL | :heavy_check_mark: |
| TVDb Description | `tvdb_description` | Used to change the collection/playlist's summary to the TVDb List Description | TVDb List URL | :heavy_check_mark: |
| Trakt Description | `trakt_description` | Used to change the collection/playlist's summary to the Trakt List Description | Trakt List URL | :heavy_check_mark: |
| Letterboxd Description | `letterboxd_description` | Used to change the collection/playlist's summary to the Letterboxd List Description | Letterboxd List URL | :heavy_check_mark: |

## Poster Details
All the following attributes update the poster of the collection/playlist from various sources.

| Name | Attribute | Description | Allowed Values | Works with Playlists |
| :--- | :--- | :--- | :--- | :---: |
| URL Poster<sup>2</sup> | `url_poster` | Used to change the collection/playlist's poster to the URL | URL of image publicly available on the internet | :heavy_check_mark: |
| TMDb Poster<sup>2</sup> | `tmdb_poster` | Used to change the collection/playlist's poster to the TMDb Movie/Collection poster for a movie library or the TMDb Show poster for a show library | TMDb Movie/Show/Collection ID | :heavy_check_mark: |
| TMDb List Poster<sup>2</sup> | `tmdb_list_poster` | Used to change the collection/playlist's poster to the TMDb List poster | TMDb List ID | :heavy_check_mark: |
| TMDb Profile<sup>2</sup> | `tmdb_profile` | Used to change the collection/playlist's poster to the TMDb Person's profile | TMDb Person ID | :heavy_check_mark: |
| TVDb Poster<sup>2</sup> | `tvdb_poster` | Used to change the collection/playlist's poster to the TVDb Movie poster for a movie library or the TVDb Show poster for a show library | TVDb Movie/Show ID or URL | :heavy_check_mark: |
| File Poster<sup>2</sup> | `file_poster` | Used to change the collection/playlist's poster to the image in the file system | Path to image in the file system | :heavy_check_mark: |

* If no poster is specified the script will look in the library's [Image Asset Directories](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Image-Asset-Directory) for a folder named either the collection/playlist name or the `name_mapping` if specified and look for a `poster.ext` file in that folder (replacing .ext with the image extension).

## Background Details
All the following attributes update the background of the collection/playlist from various sources.

| Name | Attribute | Description | Allowed Values | Works with Playlists |
| :--- | :--- | :--- | :--- | :---: |
| URL Background<sup>3</sup> | `url_background` | Used to change the collection/playlist's background to the URL | URL of image publicly available on the internet | :x: |
| TMDb Background<sup>3</sup> | `tmdb_background` | Used to change the collection/playlist's background to the TMDb Movie/Collection background for a movie library or the TMDb Show background for a show library | TMDb Movie/Show/Collection ID | :x: |
| TVDb Background<sup>3</sup> | `tvdb_background` | Used to change the collection/playlist's background to the TVDb Movie background for a movie library or the TVDb Show background for a show library | TVDb Movie/Show ID or URL | :x: |
| File Background<sup>3</sup> | `file_background` | Used to change the collection/playlist's background to the image in the file system | Path to image in the file system | :x: |

* If no background is specified the script will look in the library's [Image Asset Directories](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Image-Asset-Directory) for a folder named either the collection/playlist name or the `name_mapping` if specified and look for a `background.ext` file in that folder (replacing .ext with the image extension).
