# python3

Docker image available as "jvzantvoort/python3:latest". It's just
the `python:3.6` image with an addition of
[fixuid](https://github.com/boxboat/fixuid).

example use:

```bash

docker .... -u `id -u`:`id -g` "jvzantvoort/python3:latest" ...

```
