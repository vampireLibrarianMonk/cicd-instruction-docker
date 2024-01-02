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

9. Log out and back in for this to take effect.

10. To ensure Docker starts when your system boots, enable it:
```bash
sudo systemctl enable docker
```

11. Reboot your computer

12. Verify that Docker is installed correctly by running the hello-world image:
```bash
docker run hello-world
```
Result:

With these steps, Docker should be successfully installed and ready to use on your Ubuntu 22.04.3 system. Remember to log out and back in if you've added your user to the Docker group.
