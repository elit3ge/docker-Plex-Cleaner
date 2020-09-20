# Plex-Cleaner Docker

[![Build Status](https://travis-ci.org/elit3ge/docker-Plex-Cleaner.svg?branch=master)](https://travis-ci.org/elit3ge/docker-Plex-Cleaner)

Dokerized version of ngovil21/Plex-Cleaner

## First run 

```
docker pull elit3ge/docker-plex-cleaner
docker run -ti -v /path/to/config/folder:/config nitrikx/plex-cleaner
```

## Testing 

```
docker run -ti -v /path/to/config/folder:/config nitrikx/plex-cleaner --test
```

## Execution frequence

```
# Run every 4 hours
docker run -ti -v /path/to/config/folder:/config -e "EXECUTION_CRON_EXPRESSION=0 */4 * * *" elit3ge/docker-plex-cleaner

# Run once
docker run -ti -v /path/to/config/folder:/config -e "EXECUTION_CRON_EXPRESSION=ONCE" elit3ge/docker-plex-cleaner
````

## plex_delete = false

If you want to delete the file without passing by the Plex Web API, you need to mount your plex data directory:

```
docker run -ti -v /path/to/config/folder:/config -v /path/to/plex/folder:/plexdata elit3ge/docker-plex-cleaner
```

and then adjust your configuration:

```
...
    "default_location": "/plexdata",
...
```

## Logs

You can also export the logs by mounting a volume on `/logs`:
```
docker run -ti -v /path/to/config/folder:/config -v /path/to/logs/folder:/logs nitrikx/plex-cleaner
```
