This builder finds its items by using the features of Plex.

No configuration is required for these builders.

| Name | Attribute | Description | Works with Movies | Works with Shows | Works with Playlists and Custom Sort |
| :--- | :--- | :--- | :---: | :---: | :---: |
| [Plex All](#plex-all) | `plex_all` | Gets every movie/show in your library. Useful with [Filters](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Filters) | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Plex Collectionless](#plex-collectionless) | `plex_collectionless` | Gets every movie/show that is not in a collection | :heavy_check_mark: | :heavy_check_mark: | :x: |
| [Plex Search](#plex-search) | `plex_search` | Gets every movie/show based on the search parameters provided | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |

## Plex All
Finds every item in your library. Useful with [Filters](https://github.com/meisnate12/Plex-Meta-Manager/wiki/Filters).

The expected input is either true or false.

```yaml
collections:
  9.0 Movies:
    plex_all: true
    filters:
      rating.gte: 9
```

## Plex Search
Uses Plex's [Advance Filters](https://support.plex.tv/articles/201273953-collections/) to find all items based on the search parameters provided.

Any Advance Filter made using the Plex UI should be able to be recreated using `plex_search`. If you're having trouble getting `plex_search` to work correctly, build the collection you want inside of Plex's Advance Filters and take a screenshot of the parameters in the Plex UI and post it in either the [Discussions](https://github.com/meisnate12/Plex-Meta-Manager/discussions) or on [Discord](https://discord.gg/TsdpsFYqqm) and I'll do my best to help you. 

like Plex's [Advance Filters](https://support.plex.tv/articles/201273953-collections/) you have to start each search with either `any` or `all` as a base. You can only have one base attribute and all search attributes must be under the base.

Inside the base attribute you can use any search below or nest more `any` or `all`. You can have as many nested `any` or `all` next to each other as you want. If using multiple `any` or `all` you will have to do so in the form of a list.  

There are a couple other attributes you can have at the top level only along with the base attribute are:

## Special Attributes

| Special Option | Attribute | Description | Default |
| :--- | :--- | :--- | :---: |
| Type | `type` | The Type of items inside this collection/playlist<br>**Options**: `movies`, `shows`, `seasons`, `episodes`, `artists`, `albums`, or `tracks` | `movies` for Movies Libraries, `shows` for Show Libraries, and `artists` for Music Libraries |
| Limit | `limit` | The max number of item for the search | all |
| Sort By | `sort_by` | This will control how the search is sorted in your library. You can use any sort options for your search type in the [Sorts Options Table](#sort-options) | `random` |
| Validate | `validate` | Determines if a collection/playlist will fail on a validation error<br>**Options**: `true` or `false` | `true` |

## Sort Options

| Sort Option | Description | Movies | Shows | Seasons | Episodes |
| :--- | :--- | :---: | :---: | :---: | :---: |
| `title.asc`/`title.desc` | Sort by Title | :heavy_check_mark: | :heavy_check_mark: | :x: | :heavy_check_mark: |
| `season.asc`/`season.desc` | Sort by Season | :x: | :x: | :heavy_check_mark: | :x: |
| `show.asc`/`show.desc` | Sort by Show | :x: | :x: | :heavy_check_mark: | :heavy_check_mark: |
| `year.asc`/`year.desc` | Sort by Year | :heavy_check_mark: | :heavy_check_mark: | :x: | :heavy_check_mark: |
| `release.asc`/<br>`release.desc` | Sort by Release Date (Originally Available) | :heavy_check_mark: | :heavy_check_mark: | :x: | :heavy_check_mark: |
| `critic_rating.asc`/<br>`critic_rating.desc` | Sort by Critic Rating | :heavy_check_mark: | :heavy_check_mark: | :x: | :heavy_check_mark: |
| `audience_rating.asc`/<br>`audience_rating.desc` | Sort by Audience Rating | :heavy_check_mark: | :heavy_check_mark: | :x: | :heavy_check_mark: |
| `user_rating.asc`/<br>`user_rating.desc` | Sort by User Rating | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| `content_rating.asc`/<br>`content_rating.desc` | Sort by Content Rating | :heavy_check_mark: | :heavy_check_mark: | :x: | :x: |
| `duration.asc`/`duration.desc` | Sort by Duration | :heavy_check_mark: | :x: | :x: | :heavy_check_mark: |
| `plays.asc`/`plays.desc` | Sort by Number of Plays | :heavy_check_mark: | :x: | :x: | :heavy_check_mark: |
| `added.asc`/`added.desc` | Sort by Date Added | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |
| `episode_added.asc`/<br>`episode_added.desc` | Sort by Last Episode Date Added | :x: | :heavy_check_mark: | :x: | :x: |
| `random` | Sort by Random | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: | :heavy_check_mark: |

## Searches

There are three fields per search option when using Plex's Advance Filters in the Web UI. The first is the **Attribute** (what attribute you wish to search), the second is the **Modifier** (which modifier to use), and the third is the **Term** (actual term to search).

## String Searches
String searches can be used with either no modifier or with `.not`, `.is`, `.isnot`, `.begins`, or `.ends`.

String search can take multiple values **only as a list**.

### String Modifiers

| String Modifier | Description | Plex Web UI Display |
| :--- | :--- | :---: |
| No Modifier | Matches every item where the attribute contains the given string | `contains` |
| `.not` | Matches every item where the attribute does not contain the given string | `does not contain` |
| `.is` | Matches every item where the attribute exactly matches the given string | `is` |
| `.isnot` | Matches every item where the attribute does not exactly match the given string | `is not` |
| `.begins` | Matches every item where the attribute begins with the given string | `begins with` |
| `.ends` | Matches every item where the attribute ends with the given string | `ends with` |

### String Attributes

| String Search | Description | Movie<br>Libraries | Show<br>Libraries |
| :--- | :--- | :---: | :---: |
| `title` | Uses the title attribute to match | :heavy_check_mark: | :heavy_check_mark: |
| `episode_title` | Uses the title attribute of the show's episodes to match | :x: | :heavy_check_mark: |
| `studio` | Uses the studio attribute to match | :heavy_check_mark: | :heavy_check_mark: |

## Tag Searches
Tag searches can be used with either no modifier or with `.not` except for `decade` and `resolution` which can only be used with no modifier.

Tag search can take multiple values as a **list or a comma-separated string**.

### Tag Modifiers

| Tag Modifier | Description | Plex Web UI Display |
| :--- | :--- | :---: |
| No Modifier | Matches every item where the attribute matches the given string | `is` |
| `.not` | Matches every item where the attribute does not match the given string | `is not` |

### Tag Attributes

| Tag Search | Description | Movie<br>Libraries | Show<br>Libraries |
| :--- | :--- | :---: | :---: |
| `actor` | Uses the actor tags to match | :heavy_check_mark: | :heavy_check_mark: |
| `audio_language` | Uses the audio language tags to match | :heavy_check_mark: | :heavy_check_mark: |
| `collection` | Uses the collection tags to match | :heavy_check_mark: | :heavy_check_mark: |
| `content_rating` | Uses the content rating tags to match | :heavy_check_mark: | :heavy_check_mark: |
| `country` | Uses the country tags to match | :heavy_check_mark: | :x: |
| `decade` | Uses the year tag to match the decade | :heavy_check_mark: | :x: |
| `director` | Uses the director tags to match | :heavy_check_mark: | :x: |
| `genre` | Uses the genre tags to match | :heavy_check_mark: | :heavy_check_mark: |
| `label` | Uses the label tags to match | :heavy_check_mark: | :heavy_check_mark: |
| `network` | Uses the network tags to match<br>**Only works with the New Plex TV Agent** | :x: | :heavy_check_mark: |
| `producer` | Uses the actor tags to match | :heavy_check_mark: | :x: |
| `resolution` | Uses the resolution tags to match | :heavy_check_mark: | :heavy_check_mark: |
| `subtitle_language` | Uses the subtitle language tags to match | :heavy_check_mark: | :heavy_check_mark: |
| `writer` | Uses the writer tags to match | :heavy_check_mark: | :x: |
| `year` | Uses the year tag to match | :heavy_check_mark: | :heavy_check_mark: |
| `episode_year` | Uses the year tag to match | :x: | :heavy_check_mark: |

## Date Searches
Date searches can be used with either no modifier or with `.not`, `.before`, or `.after`.

No date search can take multiple values.

### Date Modifiers

| Date Modifier | Description | Format | Plex Web UI Display |
| :--- | :--- | :---: | :---: |
| No Modifier | Matches every item where the date attribute<br>is in the last X days | **Format:** number of days<br>e.g. `30` | `is in the last` |
| `.not` | Matches every item where the date attribute<br>is not in the last X days | **Format:** number of days<br>e.g. `30` | `is not in the last` |
| `.before` | Matches every item where the date attribute<br>is before the given date | **Format:** MM/DD/YYYY<br>e.g. `01/01/2000` | `is before` |
| `.after` | Matches every item where the date attribute<br>is after the given date | **Format:** MM/DD/YYYY<br>e.g. `01/01/2000` | `is after` |

### Date Attributes

| Date Search | Description | Movie<br>Libraries | Show<br>Libraries |
| :--- | :--- | :---: | :---: |
| `added` | Uses the date added attribute to match | :heavy_check_mark: | :heavy_check_mark: |
| `episode_added` | Uses the date added attribute of the show's episodes to match | :x: | :heavy_check_mark: |
| `release` | Uses the release date attribute (originally available) to match | :heavy_check_mark: | :heavy_check_mark: |
| `episode_air_date` | Uses the air date attribute (originally available) of the show's episodes to match | :x: | :heavy_check_mark: |
| `last_played` | Uses the date last played attribute to match | :heavy_check_mark: | :heavy_check_mark: |
| `episode_last_played` | Uses the date last played attribute of the show's episodes to match | :x: | :heavy_check_mark: |

## Number Searches
Number searches must use `.gt`, `.gte`, `.lt`, or `.lte` as a modifier.

No number search can take multiple values.

### Number Modifiers

| Number Modifier | Description | Format | Plex Web UI Display |
| :--- | :--- | :---: | :---: |
| `.gt` | Matches every item where the number attribute<br>is greater then the given number | **Format:** number<br>e.g. `30`, `1995`, or `7.5` | `is greater than` |
| `.gte` | Matches every item where the number attribute<br>is greater then or equal to the given number | **Format:** number<br>e.g. `30`, `1995`, or `7.5` | N/A |
| `.lt` | Matches every item where the number attribute<br>is less then the given number | **Format:** number<br>e.g. `30`, `1995`, or `7.5` | `is less than` |
| `.lte` | Matches every item where the number attribute<br>is less then or equal to the given number | **Format:** number<br>e.g. `30`, `1995`, or `7.5` | N/A |

### Number Attributes

| Number Search | Description | Restrictions | Movie<br>Libraries | Show<br>Libraries |
| :--- | :--- | :---: | :---: | :--: |
| `duration` | Uses the duration attribute to match using minutes | minimum: `1` | :heavy_check_mark: | :x: |
| `plays` | Uses the plays attribute to match | minimum: `1` | :heavy_check_mark: | :heavy_check_mark: |
| `episode_plays` | Uses the plays attribute of the show's episodes to match | minimum: `1` | :x: | :heavy_check_mark: |
| `critic_rating` | Uses the critic rating attribute to match | `0.0` - `10.0` | :heavy_check_mark: | :heavy_check_mark: |
| `audience_rating` | Uses the audience rating attribute to match | `0.0` - `10.0` | :heavy_check_mark: | :heavy_check_mark: |
| `user_rating` | Uses the user rating attribute to match | `0.0` - `10.0` | :heavy_check_mark: | :heavy_check_mark: |
| `episode_user_rating` | Uses the user rating attribute of the show's episodes to match | `0.0` - `10.0` | :x: | :heavy_check_mark: |
| `year` | Uses the year attribute to match | minimum: `1` | :heavy_check_mark: | :heavy_check_mark: |
| `episode_year` | Uses the year attribute of the show's episodes to match | minimum: `1` | :x: | :heavy_check_mark: |

## Boolean Searches
Boolean Searches take no modifier and can only be either `true` or `false`.

### Boolean Attributes

| Boolean Search | Description | Movie<br>Libraries | Show<br>Libraries |
| :--- | :--- | :---: | :---: |
| `hdr` | Is HDR | :heavy_check_mark: | :heavy_check_mark: |
| `unmatched` | Is Unmatched | :heavy_check_mark: | :x: |
| `duplicate` | Is Duplicate | :heavy_check_mark: | :x: |
| `unplayed` | Is Unplayed | :heavy_check_mark: | :x: |
| `progress` | Is In Progress | :heavy_check_mark: | :x: |
| `trash` | Is Trashed | :heavy_check_mark: | :heavy_check_mark: |
| `unplayed_episodes` | Has Unplayed Episodes | :x: | :heavy_check_mark: |
| `episode_unplayed` | Has Episodes Unplayed | :x: | :heavy_check_mark: |
| `episode_duplicate` | Has Duplicate Episodes | :x: | :heavy_check_mark: |
| `episode_progress` | Has Episode Progress | :x: | :heavy_check_mark: |
| `episode_unmatched` | Has Episodes Unmatched | :x: | :heavy_check_mark: |

## Plex Search Examples

A few examples are listed below:

```yaml
collections:
  Documentaries:
    plex_search:
      all:
        genre: Documentary
```
```yaml
collections:
  Dave Chappelle Comedy:
    plex_search:
      all:
        actor: Dave Chappelle
        genre: Comedy
```
```yaml
collections:
  Top Action Movies:
    collection_order: custom
    plex_search:
      all:
        genre: Action
      sort_by: audience_rating.desc
      limit: 20
```
```yaml
collections:
  90s Movies:
    plex_search:
      any:
        year:
          - 1990
          - 1991
          - 1992
          - 1993
          - 1994
          - 1995
          - 1996
          - 1997
          - 1998
          - 1999
```
```yaml
collections:
  90s Movies:
    plex_search:
      any:
        decade: 1990
```
```yaml
collections:
  Best 2010+ Movies:
    collection_order: custom
    plex_search:
      all:
        year.gte: 2010
      sort_by: audience_rating.desc
      limit: 20
```

Here's an example of an episode collection using `plex_search`.

```yaml
 collections:
   Top 100 Simpsons Episodes:
     collection_order: custom
     collection_level: episode
     plex_search:
       type: episodes
       sort_by: audience_rating.desc
       limit: 100
       all:
         title.ends: "Simpsons"
     summary: A collection of the highest rated simpsons epsodes.
```

If you specify TMDb Person ID's using the Detail `tmdb_person` and then tell either `actor`, `director`, `producer`, or `writer` to add `tmdb`, the script will translate the TMDb Person IDs into their names and run the search on those names.

```yaml
collections:
  Robin Williams:
    plex_search:
      all:
        actor: tmdb
    tmdb_person: 2157
```
```yaml
collections:
  Steven Spielberg:
    plex_search:
      all:
        director: tmdb
    tmdb_person: https://www.themoviedb.org/person/488-steven-spielberg
```
```yaml
collections:
  Quentin Tarantino:
    plex_search:
      any:
        actor: tmdb
        director: tmdb
        producer: tmdb
        writer: tmdb
    tmdb_person: 138
```
