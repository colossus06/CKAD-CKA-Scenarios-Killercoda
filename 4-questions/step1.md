## Containerize a Python Application

Clone the [study group repo](https://github.com/colossus06/cka-ckad-study-group-2024.git), navigate to `study-sessions/week-2` folder. There is a Dockerfile. It runs a python image. do the following:
- change the base image tag to `3.11.4`
- expose port 8000
- run image should run the command `python3 -m flask run --host=0.0.0.0 --port=8000`

Once you edit the file, build and export the image naming `kirbyrocket-gang` with the tag `1.0`. Validate the image.
Pull the container image python:3.11.4-slim from Docker Hub.
Save the container image to the file `python-3.11.4-slim.tar`, delete the python slim image you downloaded.
Load the image from the tar archive.