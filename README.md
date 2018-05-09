# snippets
A place to collect some code snippets I seem to usually need and forget at the same time.

# Table of Contents

1. [Python](#python)
2. [Bash](#bash)
3. [Tmux](#tmux)
4. [Linux](#linux)
5. [Docker](#docker)

# Python

## Opencv version
```bash
import cv2
vc2.__version__
```

## Pip package version
```bash
$ pip list | grep the_pip_package_you_seek
```

# Bash
## Cuda version
```bash
$ nvcc --version
```

## CuDNN version
```bash
$ cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2
```

## Check Nvidia GPU
```bash
$ nvidia-smi
```

## Nginx test config
```bash
$ nginx -t
```

# Tmux

## list sessions
```bash
$ tmux list-sessions
```

## attach to session
```bash
$ tmux attach-session -t #
```

## split vertically
```bash
Ctrl+b %
```

## split horizontal
```bash
Ctrl+b "
```

## cycle through panes
```bash
Ctrl+b o
```

## zoom to current pane
```bash
Ctrl+b z
```


## kill pane
```bash
Ctrl+b x
```


# Linux
## Print linux version info

```bash
$ cat /etc/*-release
```

## update your linux
```bash
#!/bin/sh
sudo apt-get update && sudo apt-get dist-upgrade -y
sudo apt-get autoremove -y
sudo apt-get autoclean -y
if [ -f "/var/run/reboot-required" ]; then
    /bin/cat /var/run/reboot-required
fi
```

## Which kernel you are running
```bash
uname -r
```

## Having trouble installing update because of a full /boot drive
[Ipbastola: Safest way to clean up boot partition](https://gist.github.com/ipbastola/2760cfc28be62a5ee10036851c654600)

# Docker

## List containers
```bash
# Running containers
$ docker ps

# Local container images
$ docker images
```

## Build container in current directory
```bash
$ docker build -t container_tag_name .
```

## Run container detached
```bash
# -d: detached
# -p: external_port:internal_port
# --name: running container name
# (frontend): container_tag_name

$ docker run -d -p 8080:80 --name=frontendlocal frontend
```

## Connect bash to a running container
```bash
$ docker exec -it container_name /bin/bash
```

## Start a container that will be proxied by nginx-proxy
(note: the --network flag is not mentioned in the docs, but I needed it to fix a connection problem)
```bash
$ docker run -e VIRTUAL_HOST=DNS_NAME --network=nginx-proxy -d zerotosingularity_site
```
