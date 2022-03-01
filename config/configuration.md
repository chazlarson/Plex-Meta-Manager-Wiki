# Configuration File

The script utilizes a YAML config file to load information to connect to the various APIs you can connect with. 

By default, the script looks at `/config/config.yml` for the Configuration File unless otherwise specified.

A template Configuration File can be found in the repo [config/config.yml.template](https://github.com/meisnate12/Plex-Meta-Manager/blob/master/config/config.yml.template). 

The YAML mappings that can be set in the configuration file's root:

| Name                       | YAML Attribute   |              Required              |
|:---------------------------|:-----------------|:----------------------------------:|
| [Libraries](libraries)     | `libraries`      |              &#9989;               |
| [Playlist Files](playlist) | `playlist_files` |              &#10060;              |
| [Settings](settings)       | `settings`       |              &#10060;              |
| [Webhooks](webhooks)       | `webhooks`       |              &#10060;              |
| [Plex](plex)               | `plex`           | &#9989; Either here or per library |
| [TMDb](tmdb)               | `tmdb`           |              &#9989;               |
| [Tautulli](tautulli)       | `tautulli`       |              &#10060;              |
| [OMDb](omdb)               | `omdb`           |              &#10060;              |
| [Notifiarr](notifiarr)     | `notifiarr`      |              &#10060;              |
| [AniDB](anidb)             | `anidb`          |              &#10060;              |
| [Radarr](radarr)           | `radarr`         |              &#10060;              |
| [Sonarr](sonarr)           | `sonarr`         |              &#10060;              |
| [Trakt](trakt)             | `trakt`          |              &#10060;              |
| [MyAnimeList](myanimelist) | `mal`            |              &#10060;              |

* You can find a template config file in [config/config.yml.template](https://github.com/meisnate12/Plex-Meta-Manager/blob/master/config/config.yml.template)
