# Web site submodule for the example app using the git submodule and docker developer workflow

see the top-level project at [https://github.com/abdes/submodule-docker-dev-workflow](https://github.com/abdes/submodule-docker-dev-workflow)

This is a static web site example. It is part of the overall example system to
demonstrate the use of git submodules and docker to simplify and optimize the
developer workflow.

At runtime, the web site is [dockerized](http://www.docker.com) to run within
a container based on [nginx](https://www.nginx.com). The requests are fronted by
a [nginx](https://www.nginx.com) reverse proxy, also running in a docker container.
