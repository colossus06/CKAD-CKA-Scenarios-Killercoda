## Containerize a Python Application

Clone the [study group repo](https://github.com/colossus06/cka-ckad-study-group-2024.git), navigate to `study-sessions/week-2` folder. There is a Dockerfile. It runs a python image. do the following:
- change the base image tag to `3.11.4`
- expose port 8000
- run image should run the command `python3 -m flask run --host=0.0.0.0 --port=8000`

Once you edit the file, build and export the image naming `kirbyrocket-gang` with the tag `1.0`. Validate the image.
Pull the container image python:3.11.4-slim from Docker Hub.
Save the container image to the file `python-3.11.4-slim.tar`, delete the python slim image you downloaded.
Load the image from the tar archive.

<details>
<summary>Solution</summary>

```sh
git clone https://github.com/colossus06/cka-ckad-study-group-2024.git
cd cka-ckad-study-group-2024/study-sessions/week-2
vim Dockerfile
curl -sSL https://get.docker.com/ | sh
sudo apt update
sudo apt-get install docker-buildx-plugin -y

IMAGE=kirbyrocket-gang
docker buildx create --name ckad --use --bootstrap
docker buildx build --load --platform linux/amd64 -t $IMAGE:1.0 .
docker image ls | grep kirby
docker save -o python-3.11.4-slim.tar python:3.11.4-slim
docker load -i python-3.11.4-slim.tar
```

</details>