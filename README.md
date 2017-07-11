# jupyter-dev-env

Simple dev env to run Jupyter

### Motivation

It could take a while if you want to run [scipy-notebook](https://github.com/jupyter/docker-stack)
in dev mode with proper permissons.

This setup helps to have local customized images with extra packages and
proper permissions.

### Usage
Add let's put some defaults in your docker-compose (container installation)

```
export COMPOSE_OPTIONS="-e USER=$(id -un) -e UID=$(id -u) -e GID=$(id -g)"
```

#### Build it once

It will take a while but you need to do it only once

```
docker-compose build app

```

For example if your user name is `max` and uid is `1002` and guid `1005`
You will have image build for your current env with the name and tag
```
max/scipy-notebook:1002.1005
```

check it yourself

```
docker images | grep scipy-notebook
```

#### Run it

Run jypyter
```
docker-compose up jupyter
```

Or jupyterlab
```
docker-compose up jupyterlab
```

Now try to crate some file in jupyter. Created file should have a proper
permissions in your workdir.

### Customize

If you want to add extra dependencies or functionality just update the
Docker file in `docker-compose/Dockerfile` and rebuild the image.

### Notes
The setup is for dev env - means be ready to update it.
The image tagging was done in a way to have it simple and not fixed -
everything is based on the 'latest'.
So this setup eventually would be outdated. For example when
https://github.com/jupyter/docker-stacks will progress with the changes.
Was tested with
```
jupyter/scipy-notebook
sha256: 1d64a69934d667043e31a01ca1c178104816c84aa87e5d19648e369290b23e22
image_tag: aea0af4df5bf

jupyterlab: 0.24.1-py36_0
```
