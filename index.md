# <img width="80px" src="_static/pmm.png" alt="PMM"> Plex Meta Manager

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/meisnate12/Plex-Meta-Manager?style=plastic)](https://github.com/meisnate12/Plex-Meta-Manager/releases)
[![Docker Image Version (latest semver)](https://img.shields.io/docker/v/meisnate12/plex-meta-manager?label=docker&sort=semver&style=plastic)](https://hub.docker.com/r/meisnate12/plex-meta-manager)
[![Docker Pulls](https://img.shields.io/docker/pulls/meisnate12/plex-meta-manager?style=plastic)](https://hub.docker.com/r/meisnate12/plex-meta-manager)
[![GitHub commits since latest release (by SemVer)](https://img.shields.io/github/commits-since/meisnate12/plex-meta-manager/latest/develop?label=Commits%20in%20Develop&style=plastic)](https://github.com/meisnate12/Plex-Meta-Manager/tree/develop)

[![Discord](https://img.shields.io/discord/822460010649878528?label=Discord&style=plastic)](https://discord.gg/NfH6mGFuAB)
[![Docker Cloud Build Status](https://img.shields.io/docker/cloud/build/meisnate12/plex-meta-manager?style=plastic)](https://hub.docker.com/r/meisnate12/plex-meta-manager)
[![Read the Docs](https://img.shields.io/readthedocs/plex-meta-manager-wiki?style=plastic)](https://metamanager.wiki)
[![Sponsor or Donate](https://img.shields.io/badge/-Sponsor_or_Donate-blueviolet?style=plastic)](https://github.com/sponsors/meisnate12)

Plex Meta Manager is an open source Python 3 project that has been designed to ease the creation and maintenance of metadata, collections, and playlists within a Plex Media Server. The script is designed to be run continuously and be able to update information based on sources outside your plex environment. Plex Meta Manager supports Movie/TV/Music libraries and Playlists.

## Getting Started

1. Install Plex Meta Manager either by following the [Local Walkthrough](home/guides/local)
   or by installing Docker and following the [Docker Walkthrough](home/guides/docker) or the [unRAID Walkthrough](home/guides/unraid).

2. Once installed, you have to create a [Configuration File](config/configuration) filled with all your values to connect to the various services.

3. After that you can start updating Metadata and building automatic Collections by creating a [Metadata File](metadata/metadata) for each Library you want to interact with.

4. Explore the Wiki to see all the different Collection Builders that can be used to create collections.

## Development & Nightly Builds
There is a [develop](https://github.com/meisnate12/Plex-Meta-Manager/tree/develop) build which will have the most updated fixes and enhancements to the script.
. To access the Docker Image for the develop build, use the `develop` tag by adding `:develop` to the image name. i.e. `meisnate12/plex-meta-manager:develop`

If switching to the develop build, it is recommended to also use the [develop](https://metamanager.wiki/en/develop/) branch of the wiki documents any changes made from the Master build.

There is also a [nightly](https://github.com/meisnate12/Plex-Meta-Manager/tree/nightly) build which will have the absolute latest version of the script, but it could easily break and the features are not documented until they're in develop. To access the Docker Image for the nightly build use the `nightly` tag by adding `:nightly` to the image name. i.e. `meisnate12/plex-meta-manager:nightly`. As this build is subject to extreme change, there is no nightly branch of the wiki and all discussions relating to any change made in the nightly build will be held within the [Plex Meta Manager Discord Server](https://discord.gg/NfH6mGFuAB).

## Example Usage

Plex Meta Manager gives the user the power to curate a set of Collections to make discovering and organizing media easy. They can be built either using plex-based searches/filters, or by using popular builders such as TMDB, IMDB, Trakt, MDBList, MyAnimeList and many more.

Some example collections that can be created are:
  * Trending/Popular (based on TMDB, IMDB, Trakt, etc.)
  * Streaming Service (such as Netflix, Disney+, etc.)
  * Networks
  * Studios
  * Genres
  * Actors
  * Decades

Below are some user-curated collections which have been created by Plex Meta Manager.

![Movie Preview](home/movie-preview.png)

![Show Preview](home/show-preview.png)

To see user submitted Metadata configuration files, and you to even add your own, go to the [Plex Meta Manager Configs](https://github.com/meisnate12/Plex-Meta-Manager-Configs).

Plex Meta Manager can manage the metadata fields for movies, shows, seasons, episodes, artists, albums, tracks, and collections, which can allow you to have a full backup of your customizations in case of a database loss.

## Discord Support Server
Before posting on GitHub about an enhancement, error, or configuration question please visit the [Plex Meta Manager Discord Server](https://discord.gg/NfH6mGFuAB). we have a dedicated support thread system so that your query can be dealt with efficiently by our team and community.

## Feature Requests, Errors, and Configuration Questions
If you are unable to use the [Plex Meta Manager Discord Server](https://discord.gg/NfH6mGFuAB), please follow the below guidance:
* If you have an idea for how to enhance Plex Meta Manager please open a new [Feature Request](https://github.com/meisnate12/Plex-Meta-Manager/issues/new?assignees=meisnate12&labels=status%3Anot-yet-viewed%2C+enhancement&template=feature_request.md&title=Feature+Request%3A+).
* If you're getting an Error please update to the latest version and then open a [Bug Report](https://github.com/meisnate12/Plex-Meta-Manager/issues/new?assignees=meisnate12&labels=status%3Anot-yet-viewed%2C+bug&template=bug_report.md&title=Bug%3A+) if the error persists.
* If you have a metadata configuration query please post in the [Discussions](https://github.com/meisnate12/Plex-Meta-Manager/discussions).

## Contributing
* Pull Requests are greatly encouraged, please submit all Pull Requests to the nightly branch.
* If you wish to contribute to the Wiki please fork and send a pull request on the [Plex Meta Manager Wiki Repository](https://github.com/meisnate12/Plex-Meta-Manager-Wiki).

## IBRACORP Video Walkthrough

[IBRACORP](https://ibracorp.io/) made a video walkthough for installing Plex Meta Manager on unRAID. While you might not be using unRAID the video goes over many key accepts of Plex Meta Manager and can be a great place to start learning how to use the script.

<iframe width="560" height="315" src="https://www.youtube.com/embed/dF69MNoot3w" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>