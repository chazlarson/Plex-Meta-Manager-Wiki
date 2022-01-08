The main goal of the script is to allow a complete recreation of your library just from the Metadata File and to dynamically build and maintain collections and playlists.

You specify the metadata and collections in a Metadata File that is defined by the [Libraries Attribute](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Libraries-Attributes) in the Configuration File. 

While you specify playlists in a Playlist File that is defined by the [Playlist Files Attribute](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Playlist-Files-Attributes) in the Configuration File.

## Metadata Files

There are three mappings allowed in the Metadata File's root:

| Name | Attribute | Description |
| :--- | :--- | :--- |
| [Metadata](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Metadata-Attributes) | `metadata` | mapping where metadata changes go |
| [Templates](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Template-Attributes) | `templates` | mapping where templates for automatic collections go |
| [Collections](#collections-and-playlists-mappings) | `collections` | mapping where automatic collections and collection metadata go |

* Either `metadata` or `collections` is required in order to run the Metadata File.
* You can find example Metadata Files in the [Plex Meta Manager Configs Repository](https://github.com/meisnate12/Plex-Meta-Manager-Configs)

## Playlist Files

There are two mappings allowed in the Playlist File's root:

| Name | Attribute | Description |
| :--- | :--- | :--- |
| [Templates](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Template-Attributes) | `templates` | mapping where templates for automatic collections go |
| [Playlists](#additional-playlist-attributes) | `playlists` | mapping where automatic playlists and playlist metadata go |

* `playlists` is required in order to run the Playlist File.
* You can find example Playlist Files in the [Plex Meta Manager Configs Repository](https://github.com/meisnate12/Plex-Meta-Manager-Configs)

## Collections and Playlists Mappings
The script can run different collection/playlist operations like automatically build collections/playlists, send missing movies/series to radarr/sonarr, and even refresh item's added within the last 30 days in order to update their metadata all using the `collections`/`playlists` attributes.

Each collection/playlist operation is defined by the mapping name which becomes the name of the Plex collection/playlist if it's created.

There are three types of attributes in a collection/playlist
1. **Builders:** an attribute that finds items to be added to the collection/playlist. Multiple builders can be used in the same collection/playlist from a variety of sources listed below.

   * [Plex Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Plex-Builders)
   * [Smart Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Smart-Builders)
   * [TMDb Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/TMDb-Builders)
   * [TVDb Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/TVDb-Builders)
   * [IMDb Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/IMDb-Builders)
   * [Trakt Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Trakt-Builders)
   * [Tautulli Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Tautulli-Builders)
   * [Letterboxd Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Letterboxd-Builders)
   * [ICheckMovies Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/ICheckMovies-Builders)
   * [FlixPatrol Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/FlixPatrol-Builders)
   * [StevenLu Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/StevenLu-Builders)
   * [AniDB Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/AniDB-Builders)
   * [AniList Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/AniList-Builders)
   * [MyAnimeList Builders](https://github.com/meisnate12/Plex-Meta-Manager/wiki/MyAnimeList-Builders)

2. **Details:** an attribute that changes anything about the metadata of the item or about how the script functions for th collection/playlist
 
   * [Setting Details](Setting-Details)
   * [Schedule Detail](Schedule-Detail)
   * [Image Overlay Detail](Image-Overlay-Detail)
   * [Metadata Details](Metadata-Details)
   * [Arr Details](Arr-Details)

3. **[Filters](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Filters):** attributes that filters items added to all Builders

## Additional Playlist Attributes

Each playlist operation requires the `libraries` attribute. Which is how the script knows which libraries to search for items in. 

The names can either be a list or comma-separated string of names that match the mapping names defined in your Configuration File.

Each playlist can also be given the `sync_to_user` which will overrider the global [`playlist_sync_to_user` Setting](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Settings-Attributes#playlist-sync-to-user). 

The values can either be `all` or a list or comma-separated string of users you want the playlist synced to in addition to yourself. To Sync a playlist to only yourself leave `sync_to_user` blank. 

```yaml
plalists:
  Marvel Cinematic Universe:
    sync_mode: sync
    libraries: Movies, TV Shows
    sync_to_user: all
    trakt_list: https://trakt.tv/users/donxy/lists/marvel-cinematic-universe?sort=rank,asc
    summary: Marvel Cinematic Universe In Chronological Order
```

**Note: For a library to be able to be used with the playlist it must be defined in the Configuration File's `libraries` attribute.**
**Note: Playlists can only have a max of one Builder because they are all inherently ordered.**
