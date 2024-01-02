# Installing Docker on Ubuntu 22.04.3
This guide provides step-by-step instructions for installing Docker on Ubuntu 22.04.3.

#Prerequisites
  * A machine running Ubuntu 22.04.3
  * sudo privileges

1. Before installing any new software, it's good practice to update your package database. Open a terminal and run:
```bash
sudo apt-get update
```

2. Install packages to allow apt to use a repository over HTTPS
```bash
sudo apt-get install ca-certificates curl gnupg
```

3. Add Docker's official GPG key to verify the integrity of the Docker packages:
```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

4. Add the Docker repository to APT sources:
```bash
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

5. Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

6. Update the package database with Docker packages from the newly added repo:
```bash
sudo apt-get update
```

7.  Install the latest version of Docker Community Edition:
```bash
sudo apt-get install docker-ce
```

8. By default, Docker requires administrator privileges. To run Docker commands as a non-root user, add your user to the docker group:
```bash
sudo usermod -aG docker ${USER}
```
9. To ensure Docker starts when your system boots, enable it:
```bash
sudo systemctl enable docker
```

10. Log out and back in if you've added your user to the Docker group.

11. Verify that Docker is installed correctly by running the hello-world image:
```bash
docker run hello-world
```
Result:
```bash
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
c1ec31eb5944: Pull complete 
Digest: sha256:ac69084025c660510933cca701f615283cdbb3aa0963188770b54c31c8962493
Status: Downloaded newer image for hello-world:latest

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

With these steps, Docker should be successfully installed and ready to use on your Ubuntu 22.04.3 system.
