Configuring [AniDB](https://anidb.net/) is optional but can allow you to access mature content with AniDB Builders.

**All AniDB Builders still work without this, they will just not have mature content**

A `anidb` mapping is in the root of the config file.

Below is a `anidb` mapping example and the full set of attributes:
```yaml
anidb:
  username: ######
  password: ######
```

| Name     | Attribute  | Allowed Values |      Required      |
|:---------|:-----------|:---------------|:------------------:|
| Username | `username` | AniDB Username | :heavy_check_mark: |
| Password | `password` | AniDB Password | :heavy_check_mark: |