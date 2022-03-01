# Playlist Files Attributes

Since playlists are not specific to one library they will need their own special [Playlist File](../metadata/metadata) to work.

You can define Playlist Files by using `playlist_files`. They can either be on the local system, online at an url, or directly from the [Plex Meta Manager Configs](https://github.com/meisnate12/Plex-Meta-Manager-Configs) repository.

By default, when `playlist_files` is missing the script will look in your config directory for `playlists.yml`.

To use a local Playlist File add `file` under playlist_files set to the system path of the yaml file.
```yaml
playlist_files:
  file: /config/My Movies Playlists.yml
```
To use all yaml files in a particular folder add `folder` under playlist_files set to the system path of the folder containing the yaml files.
```yaml
playlist_files: 
  folder: /config/Movie Playlists/
```
To use a Playlist File online add `url` under playlist_files set to the url of the yaml file.
```yaml
playlist_files:
  url: http://somesite.com/playlist_file.yml
```
To use a Playlist File from the [Plex Meta Manager Configs](https://github.com/meisnate12/Plex-Meta-Manager-Configs) repository add `git` under playlist_files set to the path in the repository.
```yaml
playlist_files:
  git: meisnate12/Playlists
```
To use a Playlist File from a `custom_repo` defined in the global Settings add `repo` under playlist_files set to the path in the repository.
* This loads the yaml file at `https://raw.githubusercontent.com/zluckytraveler/Plex-Meta-Manager-Configs/master/zluckytraveler/Collections/Movies/Movies.yml`
```yaml
settings:
  custom_repo: https://raw.githubusercontent.com/zluckytraveler/Plex-Meta-Manager-Configs/master/zluckytraveler/
playlist_files:
  repo: Collections/Movies/Movies
```
You can specify multiple paths of any type using a list like below.
```yaml
playlist_files:
  - file: /config/My Movies Playlists.yml
  - file: /config/My Shows Playlists.yml
  - url: http://somesite.com/playlist_file.yml
  - git: meisnate12/Playlists
```

