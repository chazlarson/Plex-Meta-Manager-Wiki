Testing has been done only on Python 3.7 and 3.8 on Linux and Windows. Dependencies must be installed by running:

```shell
pip install -r requirements.txt
```

If there are issues installing dependencies try:

```shell
pip install -r requirements.txt --ignore-installed
```

To run the script in an interactive terminal run:

```shell
python plex_meta_manager.py
```

### Shell Commands

| Name | Command | Allowed Values | Default Value |
| :-- | :-- | :-- | :-- |
| [Config](#config) | `-c` or `--config` | Path to YAML config file | `config/config.yml` alongside<br>`plex_meta_manager.py` |
| [Time to Run](#time-to-run) | `-t` or `--time` | Time to update each day<br>**Format:** HH:MM | `03:00` |
| [Run](#run) | `-r` or `--run` | Run without the scheduler | `False` |
| [Divider Character](#config) | `-d` or `--divider` | Character that divides the sections | `=` |
| [Screen Width](#config) | `-w` or `--width` | Integer between 90 and 300 | `100` |

## Config
To choose the location of the YAML config file

```shell
python plex_meta_manager.py --config-path <path_to_config>
```

## Time to Run
To choose the time when the script will run each day

```shell
python plex_meta_manager.py --config-path /configs/config.yml --time 22:00
```

## Run
To just run the script without having it continuously run use the --run option

```shell
python plex_meta_manager.py --config-path /configs/config.yml --run
```
## Screen Width & Divider Character
To change the terminal output width or divider character use --width and --divider

```shell
python plex_meta_manager.py --width 200 --divider *
```