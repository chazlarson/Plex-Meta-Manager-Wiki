# Metadata and Playlist Files

The main goal of the script is to allow a complete recreation of your library just from the Metadata File and to dynamically build and maintain collections and playlists.

Metadata operations and collections are defined in one or more Metadata files that are associated with libraries in the [Libraries Attribute](../config/libraries) in the Configuration File.

Playlists are defined in one or more Playlist files that are listed in the [Playlist Files Attribute](../config/playlist) in the Configuration File.

## Metadata Files

There are three mappings allowed in the Metadata File's root:

| Name                                               | Attribute     | Description                                                    |
|:---------------------------------------------------|:--------------|:---------------------------------------------------------------|
| Metadata                                           | `metadata`    | mapping where metadata changes go                              |
| [Templates](templates)                             | `templates`   | mapping where templates for automatic collections go           |
| [Collections](#collections-and-playlists-mappings) | `collections` | mapping where automatic collections and collection metadata go |

* Either `metadata` or `collections` is required in order to run the Metadata File.
* You can find example Metadata Files in the [Plex Meta Manager Configs Repository](https://github.com/meisnate12/Plex-Meta-Manager-Configs)

## Playlist Files

There are two mappings allowed in the Playlist File's root:

++Note: Many players cannot resume playing a playlist in order vote for this [Feature](https://forums.plex.tv/t/playlists-remember-position-for-subsequent-resume/84866) to be added.**

| Name                                         | Attribute   | Description                                                |
|:---------------------------------------------|:------------|:-----------------------------------------------------------|
| [Templates](templates)                       | `templates` | mapping where templates for automatic collections go       |
| [Playlists](#additional-playlist-attributes) | `playlists` | mapping where automatic playlists and playlist metadata go |

* `playlists` is required in order to run the Playlist File.
* You can find example Playlist Files in the [Plex Meta Manager Configs Repository](https://github.com/meisnate12/Plex-Meta-Manager-Configs)

## Collections and Playlists Mappings

The script can run different collection/playlist operations like automatically build collections/playlists, send missing movies/series to radarr/sonarr, or refresh items added within the last 30 days to update their metadata all using the `collections`/`playlists` attributes.

Each collection/playlist operation is defined by the mapping name which becomes the name of the Plex collection/playlist if it's created.

There are three types of attributes in a collection/playlist
1. **Builders:** an attribute that finds items to be added to the collection/playlist. Multiple builders can be used in the same collection/playlist from a variety of sources listed below.

   * [Plex Builders](builders/plex)
   * [Smart Builders](builders/smart)
   * [TMDb Builders](builders/tmdb)
   * [TVDb Builders](builders/tvdb)
   * [IMDb Builders](builders/imdb)
   * [Trakt Builders](builders/trakt)
   * [Tautulli Builders](builders/tautulli)
   * [Letterboxd Builders](builders/letterboxd)
   * [ICheckMovies Builders](builders/icheckmovies)
   * [FlixPatrol Builders](builders/flixpatrol)
   * [StevenLu Builders](builders/stevenlu)
   * [AniDB Builders](builders/anidb)
   * [AniList Builders](builders/anilist)
   * [MyAnimeList Builders](builders/myanimelist)

2. **Details:** an attribute that changes anything about the metadata of the item or about how the script functions for th collection/playlist
 
   * [Setting Details](details/setting)
   * [Schedule Detail](details/schedule)
   * [Image Overlay Detail](details/overlay)
   * [Metadata Details](details/metadata)
   * [Arr Details](details/arr)

3. **[Filters](filters):** attributes that filters items added to all Builders

## Additional Playlist Attributes

Each playlist operation requires the `libraries` attribute, which is how the script knows which libraries to search for items in. 

The names can either be a list or comma-separated string of names that match the mapping names defined in your Configuration File.

Each playlist can also contain `sync_to_users`, which will overrider the global [`playlist_sync_to_users` Setting](../config/settings.md#playlist-sync-to-users). 

The values can either be `all` or a list or comma-separated string of users you want the playlist synced to in addition to yourself. To Sync a playlist to only yourself leave `sync_to_users` blank. 

```yaml
playlists:
  Marvel Cinematic Universe:
    sync_mode: sync
    libraries: Movies, TV Shows
    sync_to_users: all
    trakt_list: https://trakt.tv/users/donxy/lists/marvel-cinematic-universe?sort=rank,asc
    summary: Marvel Cinematic Universe In Chronological Order
```

**Note: For a library to be able to be used with the playlist it must be defined in the Configuration File's `libraries` attribute.**
**Note: Playlists can only have a max of one Builder because they are all inherently ordered.**
