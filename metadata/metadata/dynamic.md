# Dynamic Collections


Plex Meta Manager can automatically create dynamic collections based on different criteria, such as
* Collections for the top `X` popular people on TMDB (Bruce Willis, Tom Hanks etc.)
* Collections for each decade represented in the library (Best of 1990s, Best of 2000s etc.)
* Collections for each of the moods/styles within a Music library (Accapella, Pop Rock etc.)

The main purpose of dynamic collections is to automate the creation of collections which would otherwise require considerable user input and repetition (such as creating a collection for every genre).

Below is an example dynamic collection which will create a collection for each of the decades represented within the library:

```yaml
dynamic_collections:
  Decades:
    type: decade
```

# Attributes

The available attributes for dynamic collections are shown below. Example usage of each attribute can be found further down this page.

| Attribute                                       | Description                                                                                                              | Works with Movies | Works with Shows | Works with Music | Playlists and Custom Sort |
|:------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------|:-----------------:|:----------------:|:----------------:|:------------------------------------:|
| [`genre`](#genre) | Create a collection for each genre found in the library   |      &#9989;      |     &#9989;      |               &#10060;               |               &#9989;                |
| [`actor`](#actor)     | Create a collection for each actor found in the library   |      &#9989;      |     &#9989;      |               &#10060;               |               &#9989;                |
| [`year`](#ayear)   | Create a collection for each year found in the library |      &#9989;      |     &#9989;      |               &#10060;               |               &#9989;                |
| [`decade`](#decade)       | Create a collection for each decade found in the library |      &#9989;      |     &#10060;        |               &#10060;               |               &#10060;               |
| [`country`](#country) | Create a collection for each country found in the library |      &#9989;      |     &#9989;      |               &#10060;               |               &#9989;                |
| [`network`](#network)     | Create a collection for each network found in the library  |      &#10060;      |     &#9989;      |               &#10060;               |               &#9989;                |
| [`mood`](#mood)              | Create a collection for each mood found in the library |      &#10060;      |     &#10060;      |               &#9989;               |               &#10060;                |
| [`style`](#style)              | Create a collection for each style found in the library|     &#10060;      |     &#10060;      |               &#9989;               |               &#10060;               |
| [`tmdb_people`](#special-attributes) | Create a collection based on user criteria<br>* see Special Attributes section for further info|     &#9989;      |     &#9989;      |               &#10060;               |               &#9989;               |

## Attribute Examples

### Genre

Create a collection for each genre found in the library 

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Type</th>
    <td><code>actor</code></td>
  </tr>
</table>

#### Example: 
* Create a collection for the top 100 items for each genre found in the library (TV and Movies)
* Exclude the "Talk Show" genre
* Name the collection "Top [Genre] Movies or Top [Genre] Shows

```yaml
templates:
  genre collection:
    smart_filter: 
      limit: 100
      sort_by: critic_rating.desc
      all: 
        genre: <<genre>>
    sort_title: <<collection_name>>
dynamic_collections:
  Genres:         # this name does not matter
    type: genre
    exclude:
          - Talk Show
    title_format: Top <<title>> <<library_type>>s
    template: genre collection
```

### Actor

Create a collection for each actor found in the library 

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Type</th>
    <td><code>actor</code></td>
  <tr>
    <th>Data</th>
    <td><code>`actor_depth`</code>: integer<br>
    <code>`actor_minimum`</code>: integer</td>
  </tr>
</table>

* `actor_depth` searches the top billed actor per movie they they are in (i.e. if they play a cameo role, this is unlikely to be counted)
* `actor_minimum` is the minimum number of times the actor must appear within `actor_depth` for the collection to be created.

#### Example:
* Create a collection for actors who appear in the top 5 billing credits of movies
* Only create the collection if they are in the top 5 billing credits of at least 20 movies

```yaml
dynamic_collections:
  Actors:         # this name does not matter
    type: actor
    data:
      actor_depth: 5
      actor_minimum: 20
```
# Special Attributes

## Overview
The `tmdb_people` attribute is a special attribute which requires the user to specify the `type` and `data` of the attribute, allowing for personalization of the dynamic collections that are created.

The below example will create dynamic collections for the 10 most popular actors
```yaml
dynamic_collections:
  tmdb_people:
    type: tmdb_popular_people
    data: 10
```

This example will create dynamic collections based on the lists that the user defines
```yaml
dynamic_collections:
  tmdb_people:
    type: trakt_user_lists
    data:
     - URL1
     - URL2
     - URL3
```

## Attribute Types

### TMDB Popular People

Create collections based on the most popular people according to TMDB

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Type</th>
    <td><code>tmdb_popular_people</code></td>
  <tr>
    <th>Data</th>
    <td>Any integer</td>
  </tr>
</table>

##### Example: Create collection for the top 10 popular people
```yaml
dynamic_collections:
  tmdb_people:
    type: tmdb_popular_people
    data: 10
```
### TMDB Collection
Create collections based on the list of TMDB Collections specified.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Type</th>
    <td><code>tmdb_collection</code></td>
  <tr>
    <th>Data</th>
    <td>Comma-separated list of TMDB collections</td>
  </tr>
</table>

##### Example: Create collections for Star Wars, The Hunger Games and Lord of the Rings
```yaml
dynamic_collections:
  tmdb_people:
    type: tmdb_collections
    data: 10, 131635, 119
```

### Trakt Liked Lists
Create collections for each of the Trakt lists that the user has liked/
* Requires [Trakt Authentication](https://metamanager.wiki/en/develop/config/trakt.html) to be configured within the Configuration File

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Type</th>
    <td><code>trakt_liked_lists</code></td>
  <tr>
    <th>Data</th>
    <td>Not Required</td>
  </tr>
</table>

##### Example: Create collections for each of the lists that the user has liked within Trakt
```yaml
dynamic_collections:
  tmdb_people:
    type: trakt_liked_lists
```

### Trakt User Lists
Create collections for each of the Trakt list that the user specifies
* Requires [Trakt Authentication](https://metamanager.wiki/en/develop/config/trakt.html) to be configured within the Configuration File

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Type</th>
    <td><code>trakt_user_lists</code></td>
  <tr>
    <th>Data</th>
    <td>List of Trakt URLs</td>
  </tr>
</table>

##### Example: Create collections for each of the lists that the user has liked within Trakt
```yaml
dynamic_collections:
  tmdb_people:
    type: trakt_user_lists
    data:
     - https://trakt.tv/users/giladg/lists/latest-releases      
     - https://trakt.tv/users/donxy/lists/marvel-cinematic-universe
     - https://trakt.tv/users/yozoraxcii/lists/christmas-extravaganza-non-tv-movie
```
### Trakt People Lists
Create collections for each of the people found within Trakt lists that the user specifies
* Requires [Trakt Authentication](https://metamanager.wiki/en/develop/config/trakt.html) to be configured within the Configuration File

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th>Type</th>
    <td><code>trakt_user_lists</code></td>
  <tr>
    <th>Data</th>
    <td>List of Trakt URLs</td>
  </tr>
</table>

##### Example: Create a collection for each of the people within the Star Wars Canon franchise
```yaml
dynamic_collections:
  tmdb_people:
    type: trakt_user_lists
    data:
     - https://trakt.tv/users/movistapp/lists/star-wars
     - https://trakt.tv/users/ruben_vw_/lists/star-wars-canon-timeline?display=show
```