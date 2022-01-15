You can have the script edit the metadata of Shows, Seasons, and Episodes by adding them to the `metadata` mapping of a Metadata File.

An example of multiple metadata edits in a show library is below:
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

## Shows

Each show is defined by the mapping name which must be the same as the show name in the library unless an `alt_title` is specified.

### Seasons
To edit the metadata of a particular Season in a Show use the `seasons` attribute on its show.

The mapping name is the season number (use 0 for specials) or the season name.

### Episodes
To edit the metadata of a particular Episode in a Season use the `episodes` attribute on its season.

The mapping name is the episode number in that season or the title of the episode.

## Metadata Edits

The available attributes for editing shows, seasons, and episodes are as follows

### Special Attributes

| Name | Attribute | Allowed Values | Shows | Seasons | Episodes |
| :--- | :--- | :--- | :---: | :---: | :---: |
| Title | `title` | Title if different from the mapping value useful when you have multiple shows with the same name | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| Alternative Title | `alt_title` | Alternative title to look for | :heavy_check_mark: | :x: | :x: |
| Year | `year` | Year of show for better identification | :heavy_check_mark: | :x: | :x: |
| TMDb Show ID | `tmdb_show` | TMDb Show ID to use for metadata useful for miniseries that have been compiled into a movie | :heavy_check_mark: | :x: | :x: |
| TMDb Movie ID | `tmdb_movie` | TMDb Movie ID to use for metadata useful for movies that have been split into segments | :heavy_check_mark: | :x: | :x: |
| Seasons | `seasons` | Mapping to define Seasons | :heavy_check_mark: | :x: | :x: |
| Episodes | `episodes` | Mapping to define Episodes | :x: | :heavy_check_mark: | :x: |

* YAML files cannot have two items with the same mapping name so if you have two shows with the same name you would change the mapping values to whatever you want. Then use the `title` attribute to specify the real title and use the `year` attribute to specify which of the multiple shows to choose.
    ```yaml
    metadata:
      Godzilla1:
        title: Godzilla
        year: 1954
        content_rating: R
      Godzilla2:
        title: Godzilla
        year: 1998
        content_rating: PG-13
    ```

* If you know of another Title your show might exist under, but you want it titled differently you can use `alt_title` to specify another title to look under and then be changed to the mapping name. For Example TMDb uses the name `The Legend of Korra`, but I want it as `Avatar: The Legend of Korra` (Which must be surrounded by quotes since it uses the character `:`):
    ```yaml
    metadata:
      "Avatar: The Legend of Korra":
        alt_title: The Legend of Korra
    ```
    This would change the name of the TMDb default `The Legend of Korra` to `Avatar: The Legend of Korra` and would not mess up any subsequent runs.

### General Attributes

| Name | Attribute | Allowed Values | Shows | Seasons | Episodes |
| :--- | :--- | :--- | :---: | :---: | :---: |
| Sort Title | `sort_title` | Text to change Sort Title | :heavy_check_mark: | :x: | :heavy_check_mark: |
| Original Title | `original_title` | Text to change Original Title | :heavy_check_mark: | :x: | :heavy_check_mark: |
| Originally Available | `originally_available` | Date to change Originally Available<br>**Format:** YYYY-MM-DD  | :heavy_check_mark: | :x: | :heavy_check_mark: |
| Content Rating | `content_rating` | Text to change Content Rating | :heavy_check_mark: | :x: | :x: |
| Rating | `rating` | Number to change Rating | :heavy_check_mark:| :x: | :heavy_check_mark: |
| Studio | `studio` | Text to change Studio | :heavy_check_mark: | :x: | :x: |
| Tagline | `tagline` | Text to change Tagline | :heavy_check_mark:| :x: | :x: |
| Summary | `summary` | Text to change Summary | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |

### Tag Attributes

You can add `.remove` to any tag attribute to only remove those tags i.e. `genre.remove`. 

You can add `.sync` to any tag attribute to sync all tags vs just appending the new ones i.e. `genre.sync`.

| Name | Attribute | Allowed Values | Shows | Seasons | Episodes |
| :--- | :--- | :--- | :---: | :---: | :---: |
| Director | `director` | List or comma-separated text of each Director Tag | :x: | :x: | :heavy_check_mark: |
| Genre | `genre` | List or comma-separated text of each Genre Tag | :heavy_check_mark: | :x: | :x: |
| Writer | `writer` | List or comma-separated text of each Writer Tag | :x: | :x: | :heavy_check_mark: |
| Collection | `collection` | List or comma-separated text of each Collection Tag | :heavy_check_mark: | :x: | :x: |
| Label | `label` | List or comma-separated text of each Label Tag | :heavy_check_mark: | :x: | :x: |

## Image Attributes

| Name | Attribute | Description | Allowed Values | Shows | Seasons | Episodes |
| :--- | :--- | :--- | :--- | :---: | :---: | :---: |
| URL Poster | `url_poster` | Used to change the show's poster to the URL | URL of image publicly available on the internet | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| File Poster | `file_poster` | Used to change the show's poster to the image in the file system | Path to image in the file system | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| URL Background | `url_background` | Use to change the show's background to the URL | URL of image publicly available on the internet | :heavy_check_mark: | :heavy_check_mark: | :x: |
| File Background | `file_background` | Used to change the show's background to the image in the file system | Path to image in the file system | :heavy_check_mark: | :heavy_check_mark: | :x: |

### Advance Attributes

All these attributes only work with Shows.

| Name | Attribute | Allowed Values |
| :--- | :--- | :--- |
| Episode Sorting | `episode_sorting` | `default`: Library default<br>`oldest`: Oldest first<br>`newest`: Newest first |
| Keep Episodes | `keep_episodes` | `all`: All episodes<br>`5_latest`: 5 latest episodes<br>`3_latest`: 3 latest episodes<br>`latest`: Latest episodes<br>`past_3`: Episodes added in the past 3 days<br>`past_7`: Episodes added in the past 7 days<br>`past_30`: Episodes added in the past 30 days |
| Delete Episodes | `delete_episodes` | `never`: Never<br>`day`: After a day<br>`week`: After a week<br>`refresh`: On next refresh |
| Season Display | `season_display` | `default`: Library default<br>`show`: Show<br>`hide`: Hide |
| Episode Ordering | `episode_ordering` | `default`: Library default<br>`tmdb_aired`*: The Movie Database (Aired)<br>`tvdb_aired`: TheTVDB (Aired)<br>`tvdb_dvd`: TheTVDB (DVD)<br>`tvdb_absolute`: TheTVDB (Absolute) |
| Metadata Language* | `metadata_language` | `default`, `ar-SA`, `ca-ES`, `cs-CZ`, `da-DK`, `de-DE`, `el-GR`, `en-AU`, `en-CA`, `en-GB`, `en-US`, `es-ES`, `es-MX`, `et-EE`, `fa-IR`, `fi-FI`, `fr-CA`, `fr-FR`, `he-IL`, `hi-IN`, `hu-HU`, `id-ID`, `it-IT`, `ja-JP`, `ko-KR`, `lt-LT`, `lv-LV`, `nb-NO`, `nl-NL`, `pl-PL`, `pt-BR`, `pt-PT`, `ro-RO`, `ru-RU`, `sk-SK`, `sv-SE`, `th-TH`, `tr-TR`, `uk-UA`, `vi-VN`, `zh-CN`, `zh-HK`, `zh-TW` |
| Use Original Title* | `use_original_title` | `default`: Library default<br>`no`: No<br>`yes`: Yes |

\* Must be using the **New Plex TV Agent** 
