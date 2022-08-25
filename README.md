# cloud-devops
cloud-devops 

**DOCKER:**

============================================================================================ 
**Docker installation commands :**

    1  sudo apt-get update
    2  sudo apt-get install     ca-certificates     curl     gnupg     lsb-release
    3  sudo mkdir -p /etc/apt/keyrings
    4  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
    5  echo   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    6  sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
    7  sudo apt-get update
    8  sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
    9  docker run hello-world
   10  docker run -it ubuntu bash
   11  docker images
   12  systemctl status docker


==>  By default only the root user can connect to the docker daemon by cli. 
If u want any other user to run docker commands then u need to add the user into the docker group 

vagrant@ubuntu-bionic:~$ whoami

vagrant

vagrant@ubuntu-bionic:~$ docker images

Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/images/json": dial unix /var/run/docker.sock: connect: permission denied

    1  whoami
    2  sudo -i
    3  whoiami
    4  whoami
    5  docker images
    6  sudo /etc/group
    7  cat /etc/group
    8  sudo usermod -aG docker vagrant
    9  id vagrant
   10  docker images
   11  whoami
   12  exit
   13  docker images
   
   vagrant@ubuntu-bionic:~$ docker run hello-world

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


vagrant@ubuntu-bionic:~$ docker ps

CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES

vagrant@ubuntu-bionic:~$ docker ps -a

CONTAINER ID   IMAGE         COMMAND    CREATED          STATUS                        PORTS     NAMES
a2e4189531fc   hello-world   "/hello"   50 seconds ago   Exited (0) 49 seconds ago               affectionate_morse
028e8dfbeabe   ubuntu        "bash"     21 minutes ago   Exited (127) 20 minutes ago             eloquent_davinci
f1fee35546b4   hello-world   "/hello"   23 minutes ago   Exited (0) 23 minutes ago               strange_sammet


==> docker ps -> lists the running container

==> docker ps -a -> lists all the container (dead also) 

root@ubuntu-bionic:~# docker pull hello-world
Using default tag: latest
Error response from daemon: Get "https://registry-1.docker.io/v2/": dial tcp: lookup registry-1.docker.io: Temporary failure in name resolution

1. Open config file sudo nano /etc/resolv.conf and add the following under existing nameservers
nameserver 8.8.8.8
nameserver 8.8.4.4

2. run following commands to restart daemon and docker service
sudo systemctl daemon-reload
sudo systemctl restart docker

   44  sudo nano /etc/resolv.conf
   45  sudo systemctl daemon-reload
   46  sudo systemctl restart docker
   47  docker pull hello-world
   48  docker images
   49  docker pull nginx
   50  docker images
