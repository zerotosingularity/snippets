# snippets
A place to collect some code snippets I seem to usually need and forget at the same time.

# Table of Contents

1. [Python](#python)
2. [Bash](#bash)
3. [Tmux](#tmux)
4. [Linux](#linux)

# Python

## Opencv version
```bash
import cv2
vc2.__version__
```

## Pip package version
```bash
pip list | grep the_pip_package_you_seek
```

# Bash
## Cuda version
```bash
nvcc --version
```

# Tmux

## list sessions
```bash
tmux list-sessions
```

## attach to session
```bash
tmux attach-session -t #
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
cat /etc/*-release
```
