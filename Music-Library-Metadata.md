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
            rating: 5
          "One Step Closer":
            rating: 5
      "Meteora":
        originally_available: "2003-03-25"
        album_sorting: newest
        tracks:
          9:
            rating: 5
          "Numb":
            rating: 5
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

| Name              | Attribute   | Allowed Values                |      Artists       |       Album        |       Tracks       |
|:------------------|:------------|:------------------------------|:------------------:|:------------------:|:------------------:|
| Alternative Title | `alt_title` | Alternative title to look for | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Albums            | `albums`    | Mapping to define Albums      | :heavy_check_mark: |        :x:         |        :x:         |
| Tracks            | `tracks`    | Mapping to define Tracks      |        :x:         | :heavy_check_mark: |        :x:         |

* If you know of another Title your item might exist under, but you want it titled differently you can use `alt_title` to specify another title to look under and then be changed to the mapping name. For Example the Artist `Kesha` used to be stylized as `Ke$ha`, and might still be found that way in Metadata results.
    ```yaml
    metadata:
      "Kesha":
        alt_title: "Ke$ha"
    ```
    This would change the name of the default `Ke$ha` to `Kesha` and would not mess up any subsequent runs.
``
### General Attributes

| Name                 | Attribute              | Allowed Values                                                |      Artists       |       Album        |       Tracks       |
|:---------------------|:-----------------------|:--------------------------------------------------------------|:------------------:|:------------------:|:------------------:|
| Sort Title           | `sort_title`           | Text to change Sort Title                                     | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Rating               | `rating`               | Number to change Rating                                       |        :x:         | :heavy_check_mark: | :heavy_check_mark: |
| Originally Available | `originally_available` | Date to change Originally Available<br>**Format:** YYYY-MM-DD |        :x:         | :heavy_check_mark: |        :x:         |
| Record Label         | `record_label`         | Text to change Record Label                                   |        :x:         | :heavy_check_mark: |        :x:         |
| Summary              | `summary`              | Text to change Summary                                        | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Track                | `track`                | Text to change Track                                          |        :x:         |        :x:         | :heavy_check_mark: |
| Disc                 | `disc`                 | Text to change Disc                                           |        :x:         |        :x:         | :heavy_check_mark: |
| Original Artist      | `original_artist`      | Text to change Original Artist                                |        :x:         |        :x:         | :heavy_check_mark: |

### Tag Attributes

You can add `.remove` to any tag attribute to only remove those tags i.e. `genre.remove`. 

You can add `.sync` to any tag attribute to sync all tags vs just appending the new ones i.e. `genre.sync`.

| Name           | Attribute        | Allowed Values                                          |      Artists       |       Album        |       Tracks       |
|:---------------|:-----------------|:--------------------------------------------------------|:------------------:|:------------------:|:------------------:|
| Genre          | `genre`          | List or comma-separated text of each Genre Tag          | :heavy_check_mark: | :heavy_check_mark: |        :x:         |
| Collection     | `collection`     | List or comma-separated text of each Collection Tag     | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Label          | `label`          | List or comma-separated text of each Label Tag          |        :x:         | :heavy_check_mark: |        :x:         |
| Style          | `style`          | List or comma-separated text of each Style Tag          | :heavy_check_mark: | :heavy_check_mark: |        :x:         |
| Mood           | `mood`           | List or comma-separated text of each Mood Tag           | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Country        | `country`        | List or comma-separated text of each Country Tag        | :heavy_check_mark: |        :x:         |        :x:         |
| Similar Artist | `similar_artist` | List or comma-separated text of each Similar Artist Tag | :heavy_check_mark: |        :x:         |        :x:         |

## Image Attributes

| Name            | Attribute         | Description                                                          | Allowed Values                                  |      Artists       |       Album        | Tracks |
|:----------------|:------------------|:---------------------------------------------------------------------|:------------------------------------------------|:------------------:|:------------------:|:------:|
| URL Poster      | `url_poster`      | Used to change the item's poster to the URL                          | URL of image publicly available on the internet | :heavy_check_mark: | :heavy_check_mark: |  :x:   |
| File Poster     | `file_poster`     | Used to change the item's poster to the image in the file system     | Path to image in the file system                | :heavy_check_mark: | :heavy_check_mark: |  :x:   |
| URL Background  | `url_background`  | Use to change the item's background to the URL                       | URL of image publicly available on the internet | :heavy_check_mark: | :heavy_check_mark: |  :x:   |
| File Background | `file_background` | Used to change the item's background to the image in the file system | Path to image in the file system                | :heavy_check_mark: | :heavy_check_mark: |  :x:   |

### Advance Attributes

All these attributes only work with Artists.

| Name          | Attribute       | Allowed Values                                                                                         |
|:--------------|:----------------|:-------------------------------------------------------------------------------------------------------|
| Album Sorting | `album_sorting` | `default`: Library default<br>`oldest`: Oldest first<br>`newest`: Newest first<br>`name`: Alphabetical |
