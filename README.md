# SPARCS nugu

- Slack Bot
- Homepage
- Command line

## Installation

### Prerequisite

* On Debin/Ubuntu Linux
  - `apt-get install libmysqlclient-dev`

* On MacOS
  - `brew install mysql --client-only --universal`

### The main package

For developemnt or as an editable package inside a virtual environment:
```bash
source $NUGU_VENV/bin/activate
pip install -e .
```

## Configuration

### Environment Variables (Common)

* `NUGU_SLACK_TOKEN`: The API token for Slack bot
* `NUGU_DB_HOST`: The database server's hostname 
* `NUGU_DB_USER`: The username to connect to the database server
* `NUGU_DB_PASSWORD`: The password to connect to the database server
* `NUGU_DB_NAME`: The database name

If `DEBUG` is set to `1`, it uses a local sqlite3 database as specified in
`NUGU_DB_PATH` variable.

### As a Command

Add the following as `/SPARCS/bin/nugu`

```bash
#! /bin/bash
source $NUGU_VENV/bin/activate
exec python -m nugu.cli $@
```

### As a Slack bot using supervisord

Add the following as `/etc/supervisor/conf.d/nugu.conf` after modifying
the paths to match with your setup.

```dosini
[app:nugu]
command=/SPARCS/nugu/run_bot.sh
environment=NUGU_VENV="/SPARCS/nugu/venv"
directory=/SPARCS/nugu
stopasgroup=true
killasgroup=true
```

## Developers

- samjo (조성원)
- netj (신재호)
- daybreaker (김준기)
