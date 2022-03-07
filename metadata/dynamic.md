# Dynamic Collections

Plex Meta Manager can dynamically create collections based on different criteria, such as
* Collections based on the Collections from TMDb for every item in your library. ([Star Wars](https://www.themoviedb.org/collection/10-star-wars-collection), [The Lord of the Rings](https://www.themoviedb.org/collection/119), etc...)
* Collections based on each of a Users Trakt Lists
* Collections for the top `X` popular people on TMDb (Bruce Willis, Tom Hanks, etc...)
* Collections for each decade represented in the library (Best of 1990s, Best of 2000s, etc...)
* Collections for each of the moods/styles within a Music library (A Cappella, Pop Rock, etc...)

The main purpose of dynamic collections is to automate the creation of collections which would otherwise require considerable user input and repetition (such as creating a collection for every genre).

Each dynamic collection like collections must have a mapping name, which is also attached to the collection as a label to mark the collections created by this dynamic collection. 

Below is an example dynamic collection which will create a collection for every TMDb Collection associated with items in the library.

```yaml
dynamic_collections:
  TMDb Collections:          # This name is the mapping name
    type: tmdb_collections
    remove_suffix: "Collection"
```

## Attributes

| Attribute                                   | Description                                                                                                   |     Required      |
|:--------------------------------------------|:--------------------------------------------------------------------------------------------------------------|:-----------------:|
| [`type`](#type)                             | Type of Dynamic Collection to be created.                                                                     |      &#9989;      |
| [`data`](#data)                             | Data to determine how certain `type`s of dynamic collections are created.                                     | Depends on `type` | 
| [`exclude`](#exclude)                       | Exclude this list of keys from being created into collections.                                                |     &#10060;      |
| [`addons`](#addons)                         | Defines how multiple keys can be combined under a parent key.                                                 |     &#10060;      |
| [`remove_suffix`](#remove-suffix)           | Removes suffixes from the key before it's used in the collection title.                                       |     &#10060;      |
| [`remove_prefix`](#remove-prefix)           | Removes prefixes from the key before it's used in the collection title.                                       |     &#10060;      |
| [`template`](#template)                     | Name of the template to use for these dynamic collections.                                                    |     &#10060;      |
| [`template_variables`](#template-variables) | Defines how template variables can be defined by key.                                                         |     &#10060;      |
| [`title_format`](#title-format)             | This is the format for the collection titles.                                                                 |     &#10060;      |
| [`titles`](#titles)                         | Defines how collection titles can be specifically defined by key.                                             |     &#10060;      |
| [`keys`](#keys)                             | Defines how keys can be overridden before being turned into collection titles.                                |     &#10060;      |
| [`test`](#test)                             | Can set all dynamic collections to having `test: true` for test runs.                                         |     &#10060;      |
| [`sync`](#sync)                             | Will remove dynamic collections that are no longer in the creation list.                                      |     &#10060;      |
| [`include`](#include)                       | Define a list of keys you want made into collections.                                                         |     &#10060;      |
| [`other_name`](#other-name)                 | Used with `include` when defined all keys not in `include` or `addons` will be combined into this collection. |     &#10060;      |

## Type

The available `type` options for dynamic collections are shown below. Example usage of each option can be found further down this page.

| Type Option                                   | Description                                                                                                 | Uses<br>`data` |  Movies  |  Shows   |  Music   |  Video   |
|:----------------------------------------------|:------------------------------------------------------------------------------------------------------------|:--------------:|:--------:|:--------:|:--------:|:--------:|
| [`tmdb_collection`](#tmdb-collection)         | Create a collection for each TMDb Collection associated with an item in the library                         |    &#10060;    | &#9989;  | &#10060; | &#10060; | &#10060; |
| [`tmdb_popular_people`](#tmdb-popular-people) | Create a collection for each actor found on [TMDb's Popular People List](https://www.themoviedb.org/person) |    &#9989;     | &#9989;  | &#9989;  | &#10060; | &#10060; |
| [`trakt_user_lists`](#trakt-user-lists)       | Create a collection for each list from specific trakt users                                                 |    &#9989;     | &#9989;  | &#9989;  | &#10060; | &#10060; |
| [`trakt_liked_lists`](#trakt-liked-lists)     | Create a collection for each list the authenticated trakt user likes                                        |    &#10060;    | &#9989;  | &#9989;  | &#10060; | &#10060; |
| [`trakt_people_list`](#trakt-people-lists)    | Create a collection for each actor found in the trakt list                                                  |    &#9989;     | &#9989;  | &#9989;  | &#10060; | &#10060; |
| [`actor`](#actor)                             | Create a collection for each actor found in the library                                                     |    &#9989;     | &#9989;  | &#9989;  | &#10060; | &#10060; |
| [`genre`](#genre)                             | Create a collection for each genre found in the library                                                     |    &#10060;    | &#9989;  | &#9989;  | &#9989;  | &#9989;  |
| [`year`](#year)                               | Create a collection for each year found in the library                                                      |    &#10060;    | &#9989;  | &#9989;  | &#10060; | &#10060; |
| [`decade`](#decade)                           | Create a collection for each decade found in the library                                                    |    &#10060;    | &#9989;  | &#10060; | &#10060; | &#10060; |
| [`country`](#country)                         | Create a collection for each country found in the library                                                   |    &#10060;    | &#9989;  | &#10060; | &#9989;  | &#9989;  |
| [`network`](#network)                         | Create a collection for each network found in the library                                                   |    &#10060;    | &#10060; | &#9989;  | &#10060; | &#10060; |
| [`mood`](#mood)                               | Create a collection for each mood found in the library                                                      |    &#10060;    | &#10060; | &#10060; | &#9989;  | &#10060; |
| [`style`](#style)                             | Create a collection for each style found in the library                                                     |    &#10060;    | &#10060; | &#10060; | &#9989;  | &#10060; |

### TMDb Collection

Create collections based on the TMDb Collections associated with items in the library.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>tmdb_collection</code></td>
  </tr>
  <tr>
    <th><code>data</code> Value</th>
    <td>Not Used</td>
  </tr>
  <tr>
    <th>Default Template</th>
    <td>

```yaml
default_template: 
  tmdb_collection_details: <<tmdb_collection>>
```

    </td>
  </tr>
</table>

##### Example: Create collection for every TMDb Collection found in the library.

```yaml
dynamic_collections:
  TMDb Collections:          # This name is the mapping name
    type: tmdb_collections
    remove_suffix: Collection
```

### TMDb Popular People

Create collections based on each actor found on [TMDb's Popular People List](https://www.themoviedb.org/person).

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>tmdb_popular_people</code></td>
  </tr>
  <tr>
    <th><code>data</code> Value</th>
    <td>Number greater then 0</td>
  </tr>
  <tr>
    <th>Default Template</th>
    <td>

```yaml
default_template: 
  tmdb_person: <<tmdb_popular_people>>
  plex_search: 
    all: 
      actor: tmdb
```

</td>
  </tr>
</table>

##### Example: Create collection for the top 10 popular people

```yaml
dynamic_collections:
  TMDb Popular People:          # This name is the mapping name
    type: tmdb_popular_people
    data: 10
```

### Trakt User Lists

Create collections for each of the Trakt lists for the specified users. Use `me` to reference the authenticated user.

* Requires [Trakt Authentication](../config/trakt) to be configured within the Configuration File

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>trakt_user_lists</code></td>
  </tr>
  <tr>
    <th><code>data</code> Value</th>
    <td>List of Trakt Users</td>
  </tr>
  <tr>
    <th>Default Template</th>
    <td>

```yaml
default_template: 
  trakt_list_details: <<trakt_user_lists>>
```

</td>
  </tr>
</table>

##### Example: Create collections for each of the lists that the users have created

```yaml
dynamic_collections:
  Trakt User Lists:          # This name is the mapping name
    type: trakt_user_lists
    data:
     - me
     - yozoraxcii
```

### Trakt Liked Lists

Create collections for each of the Trakt lists that the authenticated user has liked.

* Requires [Trakt Authentication](../config/trakt) to be configured within the Configuration File

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>trakt_liked_lists</code></td>
  </tr>
  <tr>
    <th><code>data</code> Value</th>
    <td>Not Used</td>
  </tr>
  <tr>
    <th>Default Template</th>
    <td>

```yaml
default_template: 
  trakt_list_details: <<trakt_liked_lists>>
```

</td>
  </tr>
</table>

##### Example: Create collections for each of the lists that the user has liked within Trakt

```yaml
dynamic_collections:
  Trakt Liked Lists:          # This name is the mapping name
    type: trakt_liked_lists
```

### Trakt People Lists

Create collections for each of the people found within Trakt lists that the user specifies.

* Requires [Trakt Authentication](../config/trakt) to be configured within the Configuration File

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>trakt_user_lists</code></td>
  </tr>
  <tr>
    <th><code>data</code> Value</th>
    <td>List of Trakt URLs</td>
  </tr>
  <tr>
    <th>Default Template</th>
    <td>

```yaml
default_template: 
  tmdb_person: <<trakt_people_list>>
  plex_search: 
    all: 
      actor: tmdb
```

</td>
  </tr>
</table>

##### Example: Create a collection for each of the people on the trakt list
```yaml
dynamic_collections:
  Trakt User Lists:
    type: trakt_people_lists
    data:
     - https://trakt.tv/users/ash9001/lists/all-time-top-actors
```

### Actor

Create a collection for each actor found in the library.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>actor</code></td>
  </tr>
  <tr>
    <th><code>data</code> Values</th>
    <td>
        <table class="clearTable">
            <tr>
                <th>Attribute</th>
                <th>Description & Values</th>
            </tr>
            <tr>
                <td><code>actor_depth</code></td>
                <td><strong>Description:</strong> Number of actors to look at per item<br>
                <strong>Values:</strong> Number greater then 0<br>
                <strong>Default:</strong> 3</td>
            </tr>
            <tr>
                <td><code>actor_minimum</code></td>
                <td><strong>Description:</strong> Minimum number of appearances required for an actor<br>
                <strong>Values:</strong> Number greater then 0<br>
                <strong>Default:</strong> 3</td>
            </tr>
            <tr>
                <td><code>number_of_actors</code></td>
                <td><strong>Description:</strong> Max number of actor collections to create<br>
                <strong>Values:</strong> Number greater then 0<br>
                <strong>Default:</strong> None</td>
            </tr>
        </table>
    </td>
  </tr>
  <tr>
    <th>Default Template</th>
    <td>

```yaml
default_template: 
  smart_filter: 
    limit: 50
    sort_by: critic_rating.desc
    any:
      genre: <<genre>>
```

    </td>
  </tr>
</table>

* `actor_depth` searches the top billed actor per movie they are in (i.e. if they play a cameo role, this is unlikely to be counted)
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

### Genre

Create a collection for each genre found in the library 

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
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

## Country

Create a collection for each country found in the library 

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>country</code></td>
  </tr>
</table>

#### Example: 
* Create a collection for the top 100 items for each country found in the library
* Name the collection "Top [Genre] Movies or Top [Genre] Shows


```yaml
templates:
  country_dynamic:
    smart_filter: 
      limit: 100
      sort_by: critic_rating.desc
      all: 
        country: <<country>>
    sort_title: +4_2_<<collection_name>>
dynamic_collections:
  Genres:         # this name does not matter
    type: country
    title_format: <<country>> Cinema
    template: country_dynamic
```



# Special Attributes

## Overview
Some attributes require the user to specify the `type` and `data` of the attribute, allowing for personalization of the dynamic collections that are created.
For these, the name of the collection within the Metadata file is a placeholder and will be replaced with the title used within the template of the attribute being used.

The below example will create dynamic collections for the 10 most popular actors
```yaml
dynamic_collections:
  TMDb Popular People:          # This name is the mapping name
    type: tmdb_popular_people
    data: 10
```

This example will create dynamic collections based on the lists that the user defines
```yaml
dynamic_collections:
  Trakt User Lists:          # This name is the mapping name
    type: trakt_user_lists
    data:
     - URL1
     - URL2
     - URL3
```

## Attribute Types

### TMDb Popular People

Create collections based on the most popular people according to TMDb

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>tmdb_popular_people</code></td>
  <tr>
    <th><code>data</code> Value</th>
    <td>Any integer</td>
  </tr>
</table>

##### Example: Create collection for the top 10 popular people
```yaml
dynamic_collections:
  TMDb Popular People:          # This name is the mapping name
    type: tmdb_popular_people
    data: 10
```
### TMDb Collection
Create collections based on the list of TMDb Collections specified.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>tmdb_collection</code></td>
  <tr>
    <th><code>data</code> Value</th>
    <td>Comma-separated list of TMDb collections</td>
  </tr>
</table>

##### Example: Create collections for Star Wars, The Hunger Games and Lord of the Rings
```yaml
dynamic_collections:
  TMDb Collections:          # This name is the mapping name
    type: tmdb_collections
    data: 10, 131635, 119
```

### Trakt Liked Lists
Create collections for each of the Trakt lists that the user has liked/
* Requires [Trakt Authentication](../config/trakt) to be configured within the Configuration File

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>trakt_liked_lists</code></td>
  <tr>
    <th><code>data</code> Value</th>
    <td>Not Required</td>
  </tr>
</table>

##### Example: Create collections for each of the lists that the user has liked within Trakt
```yaml
dynamic_collections:
  Trakt Liked Lists:          # This name is the mapping name
    type: trakt_liked_lists
```

### Trakt User Lists
Create collections for each of the Trakt list that the user specifies
* Requires [Trakt Authentication](../config/trakt) to be configured within the Configuration File

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>trakt_user_lists</code></td>
  <tr>
    <th><code>data</code> Value</th>
    <td>List of Trakt URLs</td>
  </tr>
</table>

##### Example: Create collections for each of the lists that the user has liked within Trakt
```yaml
dynamic_collections:
  Trakt User Lists:          # This name is the mapping name
    type: trakt_user_lists
    data:
     - https://trakt.tv/users/giladg/lists/latest-releases      
     - https://trakt.tv/users/donxy/lists/marvel-cinematic-universe
     - https://trakt.tv/users/yozoraxcii/lists/christmas-extravaganza-non-tv-movie
```
### Trakt People Lists
Create collections for each of the people found within Trakt lists that the user specifies
* Requires [Trakt Authentication](../config/trakt) to be configured within the Configuration File

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>trakt_user_lists</code></td>
  <tr>
    <th><code>data</code> Value</th>
    <td>List of Trakt URLs</td>
  </tr>
</table>

##### Example: Create a collection for each of the people within the Star Wars Canon franchise
```yaml
dynamic_collections:
  Trakt User Lists:
    type: trakt_people_lists
    data:
     - https://trakt.tv/users/movistapp/lists/star-wars
     - https://trakt.tv/users/ruben_vw_/lists/star-wars-canon-timeline
```