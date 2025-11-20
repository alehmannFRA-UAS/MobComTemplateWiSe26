# How to build the Docker images on your own

If you want to build the images on your own, open a terminal under this folder and call
``` shell
make all
```

To delete all call
``` shell
make clean
```
To clean docker from all unused containers, networks, images (both dangling and unused), and optionally, volumes
``` shell
make docker-prune-system
```