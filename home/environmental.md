# Run Commands & Environmental Variables

The below table outlines the run commands and environment variables that can be utilized to customise the running of Plex Meta Manager to the user's requirements. Environmental Variable values are used over Shell Command values.

If you run into a race condition where you have set an Environment Variable within your system and also use a Shell Command for the same attribute, then the Environment Variable will take priority.


| Attribute                                                  | Shell Command                      | Environmental Variable   |
|:------------------------------------------------------|:-----------------------------------|:-------------------------|
| [Config](#config)                                     | `-c` or `--config`                 | `PMM_CONFIG`             |
| [Time to Run](#time-to-run)                           | `-t` or `--time`                   | `PMM_TIME`               |
| [Run](#run)                                           | `-r` or `--run`                    | `PMM_RUN`                |
| [Run Tests](#run-tests)                               | `-rt`, `--tests`, or `--run-tests` | `PMM_TEST`               |
| [Collections Only](#collections-only)                 | `-co` or `--collections-only`      | `PMM_COLLECTIONS_ONLY`   |
| [Libraries Only](#libraries-only)                     | `-lo` or `--libraries-only`        | `PMM_LIBRARIES_ONLY`     |
| [Run Collections](#run-collections)                   | `-rc` or `--run-collections`       | `PMM_COLLECTIONS`        |
| [Run Libraries](#run-libraries)                       | `-rl` or `--run-libraries`         | `PMM_LIBRARIES`          |
| [Run Metadata Files](#run-metadata-files)             | `-rm` or `--run-metadata-files`    | `PMM_METADATA_FILES`     |
| [Libraries First](#libraries-first)                   | `-lf` or `--libraries-first`       | `PMM_LIBRARIES_FIRST`    |
| [Ignore Schedules](#ignore-schedules)                 | `-is` or `--ignore-schedules`      | `PMM_IGNORE_SCHEDULES`   |
| [Delete Collections](#delete-collections)             | `-dc` or `--delete-collections`    | `PMM_DELETE_COLLECTIONS` |
| [Resume Run](#resume-run)                             | `-re` or `--resume`                | `PMM_RESUME`             |
| [No Countdown](#no-countdown)                         | `-nc` or `--no-countdown`          | `PMM_NO_COUNTDOWN`       |
| [No Missing](#no-missing)                             | `-nm` or `--no-missing`            | `PMM_NO_MISSING`         |
| [Read Only Config](#read-only-config)                 | `-ro` or `--read-only-config`      | `PMM_READ_ONLY_CONFIG`   |
| [Divider Character](#divider-character--screen-width) | `-d` or `--divider`                | `PMM_DIVIDER`            |
| [Screen Width](#divider-character--screen-width)      | `-w` or `--width`                  | `PMM_WIDTH`              |

Further explanation and examples of each command can be found below.
## Run Command Attribute Examples
### Config
Specify the location of the configuration YAML file.

| Flags               | Default Value       | Allowed Values            | Example Value       |
|:--------------------|:--------------------|:--------------------------|:--------------------|
| `-c` or `--config`  | `config/config.yml` | Path to YAML config file  | `/data/config.yml`  |

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --config <path_to_config>
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --config <path_to_config>
```

</details>

### Time to Run
Specify the time of day that Plex Meta Manager will run.

| Flags             | Default Value | Allowed Values                          | Example Value             |
|:------------------|:--------------|:----------------------------------------|:--------------------------|
| `-t` or `--time`  | `03:00`       | comma-separated list in `HH:MM` format  | `00:00,06:00,12:00,18:00` |

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --time 22:00,03:00
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --time 22:00,03:00
```

</details>

### Run
Perform a run immediately, bypassing the time to run flag.

| Flags            |  
|:-----------------|
| `-r` or `--run`  |
<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --run
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --run
```

</details>

### Run Tests
Run Plex Meta Manager in test/debug mode

| Flags                              |
|:-----------------------------------|
| `-rt`, `--tests` or `--run-tests`  | 

* Only collections with `test: true` enabled will be run 
<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --run-tests
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --run-tests
```

</details>

### Collections Only
Only run collection metadata/YAML files, skip library operations.

| Flags                          |
|:-------------------------------
| `-co` or `--collections-only`  |

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --collections-only
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --collections-only
```

</details>

### Libraries Only
Only run library operations, skip collections.

| Flags                        |
|:-----------------------------|
| `-lo` or `--libraries-only`  |

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --libraries-only
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --libraries-only
```

</details>

### Run Collections
Run only the pre-defined collections

| Flags             | Allowed Values                          | Example Value             |
|:------------------|:----------------------------------------|:--------------------------|
| `-rc` or `--run-collections` | comma-separated list  | `Star Wars, Marvel Cinematic Universe` |

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --run-collections "Harry Potter, Star Wars"
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --run-collections "Harry Potter, Star Wars"
```

</details>

### Run Libraries
Run only the pre-defined libraries

| Flags             | Allowed Values                          | Example Value             |
|:------------------|:----------------------------------------|:--------------------------|
| `-rl` or `--run-libraries` | comma-separated list  | `Movies - 4K, TV Shows - 4K` |

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --run-libraries "TV Shows"
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --run-libraries "TV Shows"
```

</details>

### Run Metadata Files
Run only the pre-defined metadata files

| Flags             | Allowed Values                          | Example Value             |
|:------------------|:----------------------------------------|:--------------------------|
| `-rm` or `--run-metadata-files` | comma-separated list  | `Movies.yml, MovieCharts` |

* This works for all different metadata paths i.e. `git`, `url`, `file`, or `repo`.
<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --run-metadata-files "Movies"
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --run-metadata-files "Movies"
```

</details>



### Libraries First
To have the script run library operations first before collections during the run use the `--libraries-first` option.

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --libraries-first
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --libraries-first
```

</details>

### Ignore Schedules
To have the script ignore all schedules during the run except for range schedules use the `--ignore-schedules` option.

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --ignore-schedules
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --ignore-schedules
```

</details>

### Delete Collections
To have the script delete all collections in a Library before a run use the `--delete-collections` option.

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --delete-collections
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --delete-collections
```

</details>

### Resume Run
To have the script resume a run from a specific collection use the `--resume` option.

**Allowed Values:** Name of the Collection you want to resume the run at

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --resume "Star Wars"
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --resume "Star Wars"
```

</details>

### No Countdown 
To have the script run without displaying a countdown use the `--no-countdown` option.

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --no-countdown
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --no-countdown
```

</details>

### No Missing 
To have the script run without any of the missing movie/show functions use the `--no-missing` option.

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --no-missing
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --no-missing
```

</details>

### Read Only Config
To have the script run without writing to the config use the `--read-only-config` option.

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --read-only-config
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --read-only-config
```

</details>


### Divider Character & Screen Width
To change the terminal output divider character or width use the `--divider` and `--width` options.

#### Divider Character
**Default Value:** `=`<br>
**Allowed Values:** Any character

#### Screen Width
**Default Value:** `100`<br>
**Allowed Values:** Integer between 90 and 300

<details>
  <summary>Local Environment</summary>

```shell
python plex_meta_manager.py --divider * --width 200
```

</details>
<details>
  <summary>Docker Environment</summary>

```shell
docker run -it -v "X:\Media\Plex Meta Manager\config:/config:rw" meisnate12/plex-meta-manager --divider * --width 200
```

</details>
