You can have the script edit the metadata of Artists, Albums, and Tracks by adding them to the `metadata` mapping of a Metadata File.

An example of multiple metadata edits in a music library is below:
```yaml
metadata:
  "Avatar: The Last Airbender":
    sort_title: Avatar 01
    seasons:
      1:
        title: "Book One: Water"
        summary: >-
              After a lapse of 100 years, the Avatar-spiritual master of the elements-has returned. And just in 
              the nick of time. The Four Nations (Water, Earth, Fire, and Air) have become unbalanced. The Fire 
              Nation wants to rule the world, and its first conquest will be the Northern Water Tribe. It's up to 
              a 12-year-old Airbender named Aang to find a way to stop it. Join Aang, Katara, Sokka, Momo, and 
              Appa as they head north on the adventure of a lifetime.
        episodes:
          1:
            rating: 9.1
      2:
        title: "Book Two: Earth"
        summary: >-
              Avatar Aang continues his quest to master the four elements before the end of summer. Together with
              Katara, Sokka, Momo, and Appa, he journeys across the Earth Kingdom in search of an Earthbending
              mentor. Along the way, he confronts Princess Azula, treacherous  daughter of Firelord Ozai and 
              sister to Prince Zuko. More powerful than her brother, Azula will stop nothing to defeat the Avatar. 
              But Aang and the gang find plenty of Earth Kingdom allies to help them along the way. From the swamps 
              of the South to the Earth King's palace, Avatar: Book 2 is an adventure like no other.
      3:
        title: "Book Three: Fire"
        summary: >-
              Having survived the terrible battle with Azula, Aang faces new challenges as he and his brave
              friends secretly enter the Fire Nation. Their quest is to find and defeat Firelord Ozai. Along
              the way, they discover that Ozai has plans of his own. The leader of the Fire Nation intends to 
              use the massive power of Sozin's comet to spread his dominion permanently across the four nations. 
              Short on time, Aang has a lot of bending to learn and no master to help him learn it. However, his 
              friends are there to help, and he finds unexpected allies deep in the heart of the Fire Nation. In 
              the spectacular four-part conclusion, Aang must fulfill his destiny and become a fully realized 
              Avatar, or watch the world go up in smoke.
        episodes:
          21:
            summary: The Epic Series Final of Avatar The Last Airbender
  "Avatar: The Legend of Korra":
    sort_title: Avatar 02
    alt_title: The Legend of Korra
    original_title: The Legend of Korra
    seasons:
      1:
        title: "Book One: Air"
      2:
        title: "Book Two: Spirits"
      3:
        title: "Book Three: Change"
      4:
        title: "Book Four: Balance"
```

## Artist

Each artist is defined by the mapping name which must be the same as the artist name in the library unless an `alt_title` is specified.

### Albums
To edit the metadata of a particular Album for an Artist use the `albums` attribute on its artist.

The mapping name is the album name.

### Tracks
To edit the metadata of a particular Track on an Album use the `tracks` attribute on its album.

The mapping name is the episode number in that season or the title of the episode.

## Metadata Edits

The available attributes for editing artists, albums, and tracks are as follows

### Special Attributes

| Name | Attribute | Allowed Values | Artists | Album | Tracks |
| :--- | :--- | :--- | :---: |:---:| :---: |
| Alternative Title | `alt_title` | Alternative title to look for | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Albums | `albums` | Mapping to define Albums | :heavy_check_mark: | :x: | :x: |
| Tracks | `tracks` | Mapping to define Tracks | :x: | :heavy_check_mark: | :x: |

* If you know of another Title your item might exist under, but you want it titled differently you can use `alt_title` to specify another title to look under and then be changed to the mapping name. For Example TMDb uses the name `The Legend of Korra`, but I want it as `Avatar: The Legend of Korra` (Which must be surrounded by quotes since it uses the character `:`):
    ```yaml
    metadata:
      "Avatar: The Legend of Korra":
        alt_title: The Legend of Korra
    ```
    This would change the name of the TMDb default `The Legend of Korra` to `Avatar: The Legend of Korra` and would not mess up any subsequent runs.
``
### General Attributes

| Name | Attribute | Allowed Values | Artists | Album | Tracks |
| :--- | :--- | :--- | :---: | :---: | :---: |
| Sort Title | `sort_title` | Text to change Sort Title | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Rating | `rating` | Number to change Rating | :x:| :heavy_check_mark: | :heavy_check_mark: |
| Originally Available | `originally_available` | Date to change Originally Available<br>**Format:** YYYY-MM-DD  | :x: | :heavy_check_mark: | :x: |
| Record Label | `record_label` | Text to change Record Label | :x: | :heavy_check_mark: | :x: |
| Summary | `summary` | Text to change Summary | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Track | `track` | Text to change Track | :x: | :x: | :heavy_check_mark: |
| Disc | `disc` | Text to change Disc | :x: | :x: | :heavy_check_mark: |
| Original Artist | `original_artist` | Text to change Original Artist | :x: | :x: | :heavy_check_mark: |

### Tag Attributes

You can add `.remove` to any tag attribute to only remove those tags i.e. `genre.remove`. 

You can add `.sync` to any tag attribute to sync all tags vs just appending the new ones i.e. `genre.sync`.

| Name | Attribute | Allowed Values | Artists | Album | Tracks |
| :--- | :--- | :--- | :---: | :---: | :---: |
| Genre | `genre` | List or comma-separated text of each Genre Tag | :heavy_check_mark: | :heavy_check_mark: | :x: |
| Collection | `collection` | List or comma-separated text of each Collection Tag | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Label | `label` | List or comma-separated text of each Label Tag | :x: | :heavy_check_mark: | :x: |
| Style | `style` | List or comma-separated text of each Style Tag | :heavy_check_mark: | :heavy_check_mark: | :x: |
| Mood | `mood` | List or comma-separated text of each Mood Tag | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Country | `country` | List or comma-separated text of each Country Tag | :heavy_check_mark: | :x: | :x: |
| Similar Artist | `similar_artist` | List or comma-separated text of each Similar Artist Tag | :heavy_check_mark: | :x: | :x: |

## Image Attributes

| Name | Attribute | Description | Allowed Values | Artists | Album | Tracks |
| :--- | :--- | :--- | :--- | :---: | :---: | :---: |
| URL Poster | `url_poster` | Used to change the item's poster to the URL | URL of image publicly available on the internet | :heavy_check_mark: | :heavy_check_mark: | :x: |
| File Poster | `file_poster` | Used to change the item's poster to the image in the file system | Path to image in the file system | :heavy_check_mark: | :heavy_check_mark: | :x: |
| URL Background | `url_background` | Use to change the item's background to the URL | URL of image publicly available on the internet | :heavy_check_mark: | :heavy_check_mark: | :x: |
| File Background | `file_background` | Used to change the item's background to the image in the file system | Path to image in the file system | :heavy_check_mark: | :heavy_check_mark: | :x: |

### Advance Attributes

All these attributes only work with Artists.

| Name | Attribute | Allowed Values |
| :--- | :--- | :--- |
| Album Sorting | `album_sorting` | `default`: Library default<br>`oldest`: Oldest first<br>`newest`: Newest first<br>`name`: Alphabetical |