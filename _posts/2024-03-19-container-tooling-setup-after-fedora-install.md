# Container Tooling Setup After a Fresh Fedora Install

Here are the container tooling setup (Based on Podman) I follow each time I install a new Fedora: 

- Install podman-docker
- Enable podman socket: 
```systemctl enable --user --now podman.socket```
- Add podman socket to DOCKER_HOST env variable
```
DOCKER_HOST=unix:///run/user/1000/podman/podman.sock
```
- Install Docker Compose
```
dnf install docker-compose
```
- Log out and log back in or reboot
