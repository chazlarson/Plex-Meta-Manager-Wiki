# Music Library Metadata

You can have the script edit the metadata of Artists, Albums, and Tracks by adding them to the `metadata` mapping of a Metadata File.

An example of multiple metadata edits in a music library is below:
```yaml
metadata:
  "Linkin Park":
    country: "United States of America"
    album_sorting: newest
    albums:
      "Hybrid Theory":
        originally_available: "2000-10-24"
        tracks:
          1:
            user_rating: 5
          "One Step Closer":
            user_rating: 5
      "Meteora":
        originally_available: "2003-03-25"
        album_sorting: newest
        tracks:
          9:
            user_rating: 5
          "Numb":
            user_rating: 5
      "Minutes To Midnight":
        originally_available: "2007-05-14"
```

## Artist
Each artist is defined by the mapping name which must be the same as the artist name in the library unless an `alt_title` is specified.

### Albums
To edit the metadata of a particular Album for an Artist use the `albums` attribute on its artist.

The mapping name is the album name.

### Tracks
To edit the metadata of a particular Track on an Album use the `tracks` attribute on its album.

The mapping name is the track number in that Album or the title of the Track.

## Metadata Edits
The available attributes for editing artists, albums, and tracks are as follows

### Special Attributes

| Name              | Attribute   | Allowed Values                | Artists  |  Album   |  Tracks  |
|:------------------|:------------|:------------------------------|:--------:|:--------:|:--------:|
| Alternative Title | `alt_title` | Alternative title to look for | &#9989;  | &#9989;  | &#9989;  |
| Albums            | `albums`    | Mapping to define Albums      | &#9989;  | &#10060; | &#10060; |
| Tracks            | `tracks`    | Mapping to define Tracks      | &#10060; | &#9989;  | &#10060; |

* If you know of another Title your item might exist under, but you want it titled differently you can use `alt_title` to specify another title to look under and then be changed to the mapping name. For Example the Artist `Kesha` used to be stylized as `Ke$ha`, and might still be found that way in Metadata results.
    ```yaml
    metadata:
      "Kesha":
        alt_title: "Ke$ha"
    ```
    This would change the name of the default `Ke$ha` to `Kesha` and would not mess up any subsequent runs.
``
### General Attributes

| Name                 | Attribute              | Allowed Values                                                | Artists  |  Album   |  Tracks  |
|:---------------------|:-----------------------|:--------------------------------------------------------------|:--------:|:--------:|:--------:|
| Title                | `title`                | Text to change Title                                          | &#10060; | &#10060; | &#9989;  |
| Sort Title           | `sort_title`           | Text to change Sort Title                                     | &#9989;  | &#9989;  | &#9989;  |
| User Rating          | `user_rating`          | Number to change User Rating                                  | &#9989;  | &#9989;  | &#9989;  |
| Critic Rating        | `critic_rating`        | Number to change Critic Rating                                | &#10060; | &#9989;  | &#10060; |
| Originally Available | `originally_available` | Date to change Originally Available<br>**Format:** YYYY-MM-DD | &#10060; | &#9989;  | &#10060; |
| Record Label         | `record_label`         | Text to change Record Label                                   | &#10060; | &#9989;  | &#10060; |
| Summary              | `summary`              | Text to change Summary                                        | &#9989;  | &#9989;  | &#9989;  |
| Track                | `track`                | Text to change Track                                          | &#10060; | &#10060; | &#9989;  |
| Disc                 | `disc`                 | Text to change Disc                                           | &#10060; | &#10060; | &#9989;  |
| Original Artist      | `original_artist`      | Text to change Original Artist                                | &#10060; | &#10060; | &#9989;  |

### Tag Attributes

You can add `.remove` to any tag attribute to only remove those tags i.e. `genre.remove`. 

You can add `.sync` to any tag attribute to sync all tags vs just appending the new ones i.e. `genre.sync`.

| Name           | Attribute        | Allowed Values                                          | Artists  |  Album   |  Tracks  |
|:---------------|:-----------------|:--------------------------------------------------------|:--------:|:--------:|:--------:|
| Genre          | `genre`          | List or comma-separated text of each Genre Tag          | &#9989;  | &#9989;  | &#10060; |
| Collection     | `collection`     | List or comma-separated text of each Collection Tag     | &#9989;  | &#9989;  | &#9989;  |
| Label          | `label`          | List or comma-separated text of each Label Tag          | &#10060; | &#9989;  | &#10060; |
| Style          | `style`          | List or comma-separated text of each Style Tag          | &#9989;  | &#9989;  | &#10060; |
| Mood           | `mood`           | List or comma-separated text of each Mood Tag           | &#9989;  | &#9989;  | &#9989;  |
| Country        | `country`        | List or comma-separated text of each Country Tag        | &#9989;  | &#10060; | &#10060; |
| Similar Artist | `similar_artist` | List or comma-separated text of each Similar Artist Tag | &#9989;  | &#10060; | &#10060; |

### Image Attributes

| Name            | Attribute         | Description                                                          | Allowed Values                                  | Artists |  Album  |  Tracks  |
|:----------------|:------------------|:---------------------------------------------------------------------|:------------------------------------------------|:-------:|:-------:|:--------:|
| URL Poster      | `url_poster`      | Used to change the item's poster to the URL                          | URL of image publicly available on the internet | &#9989; | &#9989; | &#10060; |
| File Poster     | `file_poster`     | Used to change the item's poster to the image in the file system     | Path to image in the file system                | &#9989; | &#9989; | &#10060; |
| URL Background  | `url_background`  | Use to change the item's background to the URL                       | URL of image publicly available on the internet | &#9989; | &#9989; | &#10060; |
| File Background | `file_background` | Used to change the item's background to the image in the file system | Path to image in the file system                | &#9989; | &#9989; | &#10060; |

### Advance Attributes

All these attributes only work with Artists.

| Name          | Attribute       | Allowed Values                                                                                         |
|:--------------|:----------------|:-------------------------------------------------------------------------------------------------------|
| Album Sorting | `album_sorting` | `default`: Library default<br>`oldest`: Oldest first<br>`newest`: Newest first<br>`name`: Alphabetical |
