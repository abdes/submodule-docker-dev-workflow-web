# Web site submodule for the example app using the git submodule and docker developer workflow

see the top-level project at [https://github.com/abdes/submodule-docker-dev-workflow](https://github.com/abdes/submodule-docker-dev-workflow)

This is a static web site example. It is part of the overall example system to
demonstrate the use of git submodules and docker to simplify and optimize the
developer workflow.

At runtime, the web site is [dockerized](http://www.docker.com) to run within
a container based on [nginx](https://www.nginx.com). The requests are fronted by
a [nginx](https://www.nginx.com) reverse proxy, also running in a docker container.

## Module structure

```
├── LICENSE
├── README.md
├── nginx
│   ├── conf.d
│   │   └── default.conf
│   └── nginx.conf
└── public
    ├── 404.html
    ├── assets
    │   ├── css
    │   ├── fonts
    │   ├── images
    │   │   └── favicon.ico
    │   └── js
    └── index.html
```

The submodule contains two parts:
1. nginx: configuration files for nginx web server
2. public: the web site html files and assets (images, css, fonts, js)

Both folders are mounted at runtime by the docker container to provide the
configuration files to nginx and the web site root.

## nginx configuration

Two files are provided for nginx configuration:
* nginx.conf: the main server configuration file
* conf.d/default.conf: default configuration for nginx servers

The default configuration defines aliases to streamline access to the assets by
simply referring to them from the web site root. For example, to embed abc.png
from the images assets folder, you can simply use: ``/images/abc.png`.

The configuration only support HTTP on port 80 (which will be mapped to a
different external port in the docker container). HTTPS can be easily added
following the [nginx documentation](http://nginx.org/en/docs/http/configuring_https_servers.html).
Keys and certificates will need to be added to this submodule and mounted
as a volume in the docker container for access by nginx.
