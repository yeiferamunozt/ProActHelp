When you initialize a new **frappe-bench** directory, you will have a directory structure similar to

```
.
├── apps
│   ├── frappe
│   ├── custom_app
├── config
│   ├── redis_cache.conf
│   ├── redis_queue.conf
│   └── redis_socketio.conf
├── env
├── logs
├── Procfile
└── sites
    ├── apps.txt
    ├── assets
    ├── common_site_config.json
    ├── site1.local
    │   ├── private
    │   ├── public
    │   └── site_config.json
    └── site1.local
        ├── private
        ├── public
        └── site_config.json
```

### Apps

The `frappe` app and other frappe based apps live in this directory. The app will be bootstrapped in this directory. Your custom apps live here and you are supposed to edit/work with them here.
### Sites

Sites are served from this directory. The site will be created in this directory. Sites are distinguished based on their directory name.
### Logs

This directory is used to dump log files from various processes. Each log file is named based on the process it is logged from.
### Config

Frappe uses 3 Redis instances to manage caching, job queueing and socketio communication. All of those configurations live here.
### Env

The Python virtual environment live in this directory. Frappe based apps and Python package dependencies are installed here.
### Procfile

Frappe uses Procfile based process management. The default Procfile looks something like this:

```
redis_cache: redis-server config/redis_cache.conf
redis_socketio: redis-server config/redis_socketio.conf
redis_queue: redis-server config/redis_queue.conf
web: bench serve --port 8000

socketio: /usr/bin/node apps/frappe/socketio.js

watch: bench watch

schedule: bench schedule
worker_short: bench worker --queue short --quiet
worker_long: bench worker --queue long --quiet
worker_default: bench worker --queue default --quiet
```

Let's see what each process is used for.

#### [[Redis cache]]

Redis used for in-memory caching.

#### [[Redis socketio]]

Redis used as a pub/sub between `web` and `socketio` processes for realtime communication.

#### [[Redis queue]]

Redis used for managing background jobs queuing.

#### [[Web]]

Python web server based on [Werkzeug](https://palletsprojects.com/p/werkzeug/).

#### [[Socketio]]

Node server for a socketio connection with the browser for realtime communication.

#### [[Watch]]

Node server for bundling JS/CSS assets using [Rollup](https://rollupjs.org/). It will also rebuild files as they change.

#### [[Schedule]]

Job Scheduler using Python RQ.

#### [[Worker short]]

Python worker with a (short) timeout of 300s.

#### [[Worker long]]

Python worker with a (long) timeout of 1500s.

#### [[Worker default]]

Python worker with a timeout of 300s.