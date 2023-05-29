## What is a web server?

A web server is a computer or software application that serves as the foundation for hosting websites and delivering web content over the internet. It receives requests from web browsers or clients and responds by sending back the requested web pages, files, or other resources.

## About this Repository

As part of my work at the university I had to set up an Apache server that runs php as back-end, a MariaDB database and phpMyAdmin for managing the database. After a lot of fails, I end up achieving this goal and finally set up all the requirements. I have created this repository in order to help everyone that wants to achieve the same task with me and make his life easier.

## Requirements
You will first need to  install **Docker**

**Step 1:** Update your existing list of packages
```Bash
sudo apt update
```
**Step 2:** Install the prerequisite packages which let apt use packages over HTTPS
```Bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
**Step 3:** Add the GPG key for the official Docker repository to your system
```Bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
**Step 4: Add the Docker repository to APT sources
```Bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
**Step 5:** Update your existing list of packages again for the addition to be recognized
```Bash
sudo apt update
```
**Step 6:** Make sure you are about to install from the Docker repository instead of the default Ubuntu repository:
```Bash
apt-cache policy docker-ce
```
**Step 7:** Install Docker
```Bash
sudo apt install docker-ce
```
**Step 8:** Check the status of the docker service
```Bash
sudo systemctl status docker
```
**Step 9:** If you want to avoid typing sudo whenever you run the docker command, add your username to the docker group
```Bash
sudo usermod -aG docker ${USER}
```
**Step 10:** Apply the new group membership
```Bash
su - ${USER}
```

## How to setup

**Step 1:** First you will have to create a folder where you will pull and the required files and move into it
```Bash
mkdir WebServer && cd  WebServer
```
**Step 2:** Then you have to clone this repository by running the following command
```Bash
https://github.com/pnasis/Web-Server-setup-using-Docker.git
```
**Step 3:** Run the following command in order to deploy the stack from the **docker-compose.yml** file
```Bash
docker compose up -d
```
**Step 4:** Check the status of the containers
```Bash
docker ps
```
>If  the **status** is **Up** then you are ready.

>By running the **ls** command you will see two folders names **mariadb** and **files**. In the **files** folder you can drop all your php files. The **mariadb** folder is for configuration purposes.

## License

This repository is under [Apache 2.0](https://choosealicense.com/licenses/mit/) licence.
