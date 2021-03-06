
#DockerX2go
==========

Docker images which contain different Desktop setups 

Currently we have

1. Xubuntu
2. LXDE



###WHY ?

I want an Isolated thin client server setup that still re-uses the disk/memory for common programs and OS.

I wanted a full desktop running on the docker so I can painlessly create multiple isolated linux systems to which our thinclients on our offices work with.

Instead of running 20 seperate virtual machines that has the same Kernel/Same applications that take up lot of ram ( 20x) I wanted to use a common VM with same base os/applications and then users can customize the os do anything they want without killing other users/etc.

This system also works as a cheap remote-desktop for anyone who wants a desktop on the cloud for anything from working remotely or browse internet where there are VPN restrictions.


### How to run a server?

Pull from Docker Index and run the image

```
docker pull paimpozhil/dockerx2go
CID=$(docker run -p 2222:22 -t -d paimpozhil/dockerx2go)
docker logs $CID

note down the root/dockerx passwords.
```

OR

build it yourself.

```
git clone https://github.com/paimpozhil/DockerX2go.git .
docker build -t [yourimagename] .
CID=$(docker run -p 2222:22 -t -d [yourimagename])

docker logs $CID

note the root/dockerx passwords
```


### How to run/connect to server with a Client?

Download the x2go client for your OS from:
http://wiki.x2go.org/doku.php/doc:installation:x2goclient

Connect to your server with docker hosts's IP , Port : 2222 , Username : root , Password : ( look at docker logs for container)

Select the Session TYPE as : XFCE , this is very important

You can also SSH to the docker container directly with root or dockerx users and their passwords over the port 2222 with linux ssh or windows putty clients.

users dockerx can be used to login however for some reason you need to use root for your very first login then you can use dockerx to login with x2go :)

```
ssh root@dockerhost -p 2222
```

###Credits:

####http://bmullan.wordpress.com/
####https://github.com/rogaha/docker-desktop
####https://github.com/tutumcloud/tutum-ubuntu

#### Docker.io && x2go.org
