# snippets

A place to collect some code snippets I seem to usually need and forget at the same time...

# Table of Contents

1. [Python](#python)
2. [Nvidia](#nvidia)
2. [Bash](#bash)
3. [Tmux](#tmux)
4. [Linux](#linux)
5. [Docker](#docker)
6. [Conda](#conda)
7. [Tensorflow](#tensorflow)

# Python

## Package version
```python
import some_package
some_package.__version__
```

## Module content
```python
import some_module
dir(some_module)
```

## Pip package version
```bash
$ pip list | grep the_pip_package_you_seek
```

## GPU Count PyTorch
```python
import torch
torch.cuda.device_count()
```

## Select GPU PyTorch
```python
import torch
torch.cuda.set_device(device_num)
```
[More PyTorch GPU options](https://pytorch.org/docs/stable/cuda.html)

# Nvidia 

## Cuda version
```bash
cat /usr/local/cuda/version.txt
```

or with nvcc installed:

```bash
$ nvcc --version
```

Install nvcc:
```bash
$ (sudo) apt install nvidia-cuda-toolkit
```

## CuDNN version
```bash
$ cat /usr/local/cuda/include/cudnn.h | grep CUDNN_MAJOR -A 2
```

## Check Nvidia GPU
```bash
$ nvidia-smi
```

### alternative: gpustat
```bash
$ pip install gpustat
$ gpustat -cp
```

## Run script on a specific GPU
```bash
$ CUDA_VISIBLE_DEVICES=0 python some_script.py
```

or
```bash
$ export CUDA_VISIBLE_DEVICES=0
$ python some_script.py
```

# Nginx

## Nginx test config
```bash
$ nginx -t
```

## Nginx restart (Ubuntu)
```bash
$ systemctl restart nginx
```

# Tmux

## list sessions
```bash
$ tmux list-sessions
```

## attach to session
```bash
$ tmux attach-session -t #tmux_session_id
```

## detach current session
```bash
Ctrl+b d
```

## kill session
```bash
$ tmux kill-session -t SESSION_ID
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
# Use again to zoom out again
```

## kill pane
```bash
Ctrl+b x
```

## Equal horizontal width
```bash
Ctrl+b, Alt+1
```
Or (default on Ubuntu)
```bash
Ctrl+b, Esc+1
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
$ uname -r
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

## Force remove a container:
```bash
$ docker rmi -f <image_id> 
```

## Remove all <none> containers (except the ones that need to be forced)
```bash
$ docker rmi $(docker images | grep none | awk '{print $3}') 
```

## Remove all unused data
```bash
$ docker system prune -a
```

# Conda

## Update the current environment based on environment file

```bash
$ conda env update
```

## Create an environment
```bash
$ conda create --name myenv
```

## Create an environment from a file
```bash
$ conda env create -f environment.yml
```

## Create an environment with a specific Python version
```
$ conda create -n myenv python=3.6 # change 'myenv' and '3.6' to your values
```

## List existing environments
```bash
$ conda info --envs
# OR
$ conda env list
```

## Save all info about your packages
```bash
conda list -e > requirements.txt
```

## delete an environment
```bash
conda env remove --name ENV_NAME
```

# Tensorflow

## Tensorflow version
```bash
$ python -c 'import tensorflow as tf; print(tf.__version__)'  # for Python 2
$ python3 -c 'import tensorflow as tf; print(tf.__version__)'  # for Python 3
```
