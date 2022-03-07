# Dynamic Collections
Plex Meta Manager can dynamically create collections based on different criteria, such as
* Collections based on the Collections from TMDb for every item in the library. ([Star Wars](https://www.themoviedb.org/collection/10-star-wars-collection), [The Lord of the Rings](https://www.themoviedb.org/collection/119), etc...)
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

| Attribute                                          | Description                                                                                                                    |     Required      |
|:---------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------|:-----------------:|
| [`type`](#type-&-data)                             | Type of Dynamic Collection to be created.                                                                                      |      &#9989;      |
| [`data`](#type-&-data)                             | Data to determine how certain `type`s of dynamic collections are created.                                                      | Depends on `type` | 
| [`keys`](#example-key-usage)                       | Defines how keys can be overridden before being turned into collection titles.                                                 |     &#10060;      |
| [`exclude`](#example-key-usage)                    | Exclude this list of keys from being created into collections.                                                                 |     &#10060;      |
| [`addons`](#example-key-usage)                     | Defines how multiple keys can be combined under a parent key.                                                                  |     &#10060;      |
| [`remove_suffix`](#tmdb-collection)                | Removes suffixes from the key before it's used in the collection title.                                                        |     &#10060;      |
| [`remove_prefix`](#tmdb-collection)                | Removes prefixes from the key before it's used in the collection title.                                                        |     &#10060;      |
| [`template`](#genre)                               | Name of the template to use for these dynamic collections.                                                                     |     &#10060;      |
| [`template_variables`](#template-variables)        | Defines how template variables can be defined by key.                                                                          |     &#10060;      |
| [`title_format`](#example-key-usage)               | This is the format for the collection titles.                                                                                  |     &#10060;      |
| [`titles`](#decade)                                | Defines how collection titles can be specifically defined by key.                                                              |     &#10060;      |
| [`test`](#../../home/environmental.html#run-tests) | Can set all dynamic collections to having `test: true` for test runs.                                                          |     &#10060;      |
| [`sync`](#sync)                                    | Will remove dynamic collections that are no longer in the creation list.                                                       |     &#10060;      |
| [`include`](#year)                                 | Define a list of keys to be made into collections.                                                                             |     &#10060;      |
| [`other_name`](#other-name)                        | Used in combination with `include`. When defined, all keys not in `include` or `addons` will be combined into this collection. |     &#10060;      |

## Type & Data

Specifies the type of dynamic collection to be created. <br>
Depending on the `type` of dynamic collection, `data` is used to specify the options that are required to fulfill the requirements of creating the collection.
<br>Example usage of each option can be found [here](#examples)

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

## Keys

A `key` are used to refer to a specific value/result from the initial dynamic collection criteria that will be used to create the collection.<br>
An example of some keys that would be generated from a `genre` dynamic collection are; "Animation", "Horror" and "Comedy"<br>

### Example Key Usage

Keys can be used for a number of purposes, examples can be found throughout this page. A few examples are shown below:

* Excluding the "Horror" key from the `Genre` dynamic collection definition
```yaml
dynamic_collections:
  Genres:         # mapping name does not matter, just needs to be unique
    type: genre
    exclude:
          - Horror
```
* Using the `keys` attribute to change the formatting of "France" to "French" so that a collection can be named "French Cinema" instead of simply "France"
  * This particular example also uses the `title_format` attribute to manipulate the naming convention of the collections.
```yaml
dynamic_collections:
  Countries:         # mapping name does not matter, just needs to be unique
    type: country
    title_format: <<country>> Cinema
    template: country_dynamic
    keys:
      France: French
```
* Using the `addons` attribute to combine multiple `keys`, i.e. merging "MTV", "MTV2", "MTV3" and "MTV (UK)" into one "MTV Worldwide" collection.
  * When doing this, individual collections will not be created for the individual MTV collections, instead they will be merged within the "MTV Worldwide" collection.
```yaml
dynamic_collections:
  networks:
    type: network
     addons:
      MTV: 
        - MTV
        - MTV2
        - MTV3
        - MTV (UK)
```
# Examples

## TMDb Collection

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

### Example: Create collection for every TMDb Collection found in the library.

```yaml
dynamic_collections:
  TMDb Collections:          # This name is the mapping name
    type: tmdb_collections
    remove_suffix: Collection
    remove_prefix: The
```


## TMDb Popular People

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

### Example: Create collection for the top 10 popular people

```yaml
dynamic_collections:
  TMDb Popular People:          # This name is the mapping name
    type: tmdb_popular_people
    data: 10
```

## Trakt User Lists

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

### Example: Create collections for each of the lists that the users have created

```yaml
dynamic_collections:
  Trakt User Lists:          # This name is the mapping name
    type: trakt_user_lists
    data:
     - me
     - yozoraxcii
```

## Trakt Liked Lists

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

### Example: Create collections for each of the lists that the user has liked within Trakt

```yaml
dynamic_collections:
  Trakt Liked Lists:          # This name is the mapping name
    type: trakt_liked_lists
```

## Trakt People Lists

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

### Example: Create a collection for each of the people on the trakt list
```yaml
dynamic_collections:
  Trakt User Lists:
    type: trakt_people_lists
    data:
     - https://trakt.tv/users/ash9001/lists/all-time-top-actors
```

## Actor

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
                <td><strong>Values:</strong> Number greater then 0</td> 
                <td><strong>Default:</strong> 3</td>
            </tr>
            <tr>
                <td><code>actor_minimum</code></td>
                <td><strong>Values:</strong> Number greater then 0</td> 
                <td><strong>Default:</strong> 3</td>
            </tr>
            <tr>
                <td><code>number_of_actors</code></td>
                <td><strong>Values:</strong> Number greater then 0</td> 
                <td><strong>Default:</strong> None</td>
            </tr>
        </table>
    </td>
  </tr>
  <tr>
    <th>Default Template</th>
    <td>

```yaml
default_template: 
  tmdb_person: <<actor>>
  plex_search:
    all:
      actor: tmdb
```

</td>
  </tr>
</table>

* `actor_depth` determines how many top billed actor per item they are in. (i.e. if they play a cameo role, this is unlikely to be counted)
* `actor_minimum` determines the minimum number of times the actor must appear within `actor_depth` for the collection to be created.
* `number_of_actors` determines the number of actor collection to max out at. (i.e. if to make collections for the top 25 actors)

### Example :

* Create a collection for the top 25 actors who appear in the top 5 billing credits of movies

```yaml
dynamic_collections:
  Top Actors:         # mapping name does not matter just needs to be unique
    type: actor
    data:
      actor_depth: 5
      number_of_actors: 25
```

## Genre

Create a collection for each genre found in the library.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>genre</code></td>
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
  smart_filter:
  limit: 50
  sort_by: critic_rating.desc
    any:
      genre: <<genre>>
```

</td>
  </tr>
</table>

### Example: 
* Create dynamic collections based on each genre found in the library (TV and Movies)
* Amend the template to increase the limit from 50 to 100
* Exclude the "Talk Show" genre
* Name the collection Top [Genre] Movies or Top [Genre] Shows

```yaml
templates:
  genre collection:
    smart_filter: 
      limit: 100
      sort_by: critic_rating.desc
      all: 
        genre: <<genre>>
dynamic_collections:
  Genres:         # mapping name does not matter just needs to be unique
    type: genre
    exclude:
          - Talk Show
    title_format: Top <<title>> <<library_type>>s
    template: genre collection
```

## Year

Create a collection for each year found in the library.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>year</code></td>
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
  smart_filter:
  limit: 50
  sort_by: critic_rating.desc
    any:
      year: <<year>>
```

</td>
  </tr>
</table>

### Example
* Create dynamic collections based on each year found in the library (TV and Movies)
* Use the `include` attribute to only show collections for years "2020", "2021" and "2022"
* Name the collection "Best of (year)"
```yaml
dynamic_collections:
  Years:         # mapping name does not matter just needs to be unique
    type: year
    include:
      - 2020
      - 2021
      - 2022
    title_format: Best of <<title>>
```

## Decade

Create a collection for each decade found in the library 

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>decade</code></td>
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
  smart_filter:
  limit: 50
  sort_by: critic_rating.desc
    any:
      decade: <<decade>>
```

</td>
  </tr>
</table>

## Example: 
* Create a collection for each decade found in the library (TV and Movies)
* Name the collection Top [Decade] Movies
* Rename the `2020` collection name to "Top 2020 Movies (so far)"

```yaml
dynamic_collections:
  Decades:         # mapping name does not matter just needs to be unique
    type: decade
    title_format: Top <<title>> <<library_type>>s
    template: decade collection
    titles:
      2020: Top <<title>> <<library_type>>s (so far)
```

## Country

Create a collection for each country found in the library 

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>country</code></td>
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
  smart_filter:
  limit: 50
  sort_by: critic_rating.desc
    any:
      country: <<country>>
```

</td>
  </tr>
</table>

### Example:

* Create a collection for the top 100 movies from each country found in the library
* Name the collection Top [Country] Cinema
* The `keys` attribute is used here in combination with the `title_format` to change the collection name from "France" which would be the default title, to "Top French Cinema"

```yaml
templates:
  country_dynamic:
    smart_filter: 
      limit: 100
      sort_by: critic_rating.desc
      all: 
        country: <<country>>
dynamic_collections:
  Countries:         # mapping name does not matter just needs to be unique
    type: country
    title_format: Top <<country>> Cinema
    template: country_dynamic
    keys:
      France: French
      Germany: German
      India: Indian
```


## Network

Create a collection for each network found in the library.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>network</code></td>
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
  smart_filter:
  limit: 50
  sort_by: critic_rating.desc
    any:
      network: <<network>>
```

</td>
  </tr>
</table>


### Example: 

* Create a collection for each network found in a TV Shows library

```yaml
templates:
  network collection:
    smart_filter: 
      sort_by: critic_rating.desc
      all: 
        network: <<network>>
    sort_title: <<collection_name>>
dynamic_collections:
  Networks:         # mapping name does not matter just needs to be unique
    type: network
    title_format: <<title>>
    template: network collection
```

## Mood

Create a collection for each mood found in the library. 

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>mood</code></td>
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
  smart_filter:
  limit: 50
  sort_by: critic_rating.desc
    any:
      mood: <<mood>>
```

</td>
  </tr>
</table>

### Example:

* Create a collection for the top 100 items for each mood found in the Music library
* Name the collection Top [Mood] Tracks

```yaml
templates:
  mood collection:
    smart_filter: 
      limit: 100
      sort_by: critic_rating.desc
      type: tracks
      all: 
        mood: <<mood>>
dynamic_collections:
  Moods:         # mapping name does not matter just needs to be unique
    type: mood
    title_format: Top <<title>> Tracks
    template: mood collection
```

## Style

Create a collection for each style found in the library.

<table class="dualTable colwidths-auto align-default table">
  <tr>
    <th><code>type</code> Option</th>
    <td><code>style</code></td>
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
  smart_filter:
  limit: 50
  sort_by: critic_rating.desc
    any:
      style: <<style>>
```

</td>
  </tr>
</table>

### Example: 

* Create a collection for the top 100 items for each style found in the Music library
* Name the collection Top [Style] Tracks

```yaml
templates:
  mood collection:
    smart_filter: 
      limit: 100
      sort_by: critic_rating.desc
      type: tracks
      all: 
        style: <<style>>
dynamic_collections:
  Moods:         # mapping name does not matter just needs to be unique
    type: style
    title_format: Top <<title>> Tracks
    template: mood collection
```