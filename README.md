# jupyter-dev-env

Simple dev env to run Jupyter


### Usage
Lets define user user_id and group_id for user which we will use to run the container.

```
export CONTAINER_USER="$(id -u):$(id -g)"
```

#### Run it

As simple as
```
docker-compose up
```

Find and open the url from the logs which starts with  `http://127.0.0.1:8888/lab...`
