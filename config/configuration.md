# Configuration File

Plex Meta Manager utilizes a YAML configuration file to connect with the Plex Media Server and other third-party services via API.

By default and unless otherwise stated, Plex Meta Manager looks for the configuration file within `/config/config.yml`

A template Configuration File can be found in the [GitHub Repo](https://github.com/meisnate12/Plex-Meta-Manager/blob/master/config/config.yml.template). 

The below table outlines the third-party services that are compatible with Plex Meta Manager. Each service has specific requirements for setup that can be found by clicking the links within the table.

| Name                       | YAML Attribute   |              Required              |
|:---------------------------|:-----------------|:----------------------------------:|
| [Libraries](libraries)     | `libraries`      |              &#9989;               |
| [Playlist Files](playlist) | `playlist_files` |              &#10060;              |
| [Settings](settings)       | `settings`       |              &#10060;              |
| [Webhooks](webhooks)       | `webhooks`       |              &#10060;              |
| [Plex](plex)               | `plex`           | &#9989; <br/>Either here or per library |
| [TMDb](tmdb)               | `tmdb`           |              &#9989;               |
| [Tautulli](tautulli)       | `tautulli`       |              &#10060;              |
| [OMDb](omdb)               | `omdb`           |              &#10060;              |
| [Notifiarr](notifiarr)     | `notifiarr`      |              &#10060;              |
| [AniDB](anidb)             | `anidb`          |              &#10060;              |
| [Radarr](radarr)           | `radarr`         |              &#10060;              |
| [Sonarr](sonarr)           | `sonarr`         |              &#10060;              |
| [Trakt](trakt)             | `trakt`          |              &#10060;              |
| [MyAnimeList](myanimelist) | `mal`            |              &#10060;              |