# Docker Setup Exercise #

1. Install using Ubuntu repositories: ```sudo apt install docker.io -y```
2. Alternatively, by downloading from <a href="latest version from download.docker.com" target="_blank">download.docker.com</a>
3. Checking that docker cli (command line interface) is installed: ```docker --version```
4. Checking that docker daemon is running: ```sudo docker images```
5. Expected output is an empty list as we have not created/pulled any images
6. Running your first container: ```sudo docker run hello-world```
7. Expected output:
  ```
  78445dd45222: Pull complete  
  Digest: sha256:c5515758d4c5e1e838e9cd307f6c6a0d620b5e07e6f927b07d05f6d12a1ac8d7  
  Status: Downloaded newer image for hello-world:latest  
  Hello from Docker!  
  ... more text comes here...  
  ```
8. List your container: ```sudo docker ps -a```
9. Expected output is a list with one item on it