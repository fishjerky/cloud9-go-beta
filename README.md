# Cloud9 Docker Image for go Development using specific go version
OS: CentOS 7
change GO_VERSION to specific go version

Command:  curl wget zip unzip gcc git which vim

## Run the container with defaults

```
docker run -d -p 8080:8080 fishjerky/c9-go
```

## Options

### PNAT the port and modify the mounted go directory

```
docker run -d -v ~/my_go_workspace:/go -p 8888:8080 fishjerky/c9-go
```


### Add basic authentication

```
docker run -d -v ~:/go -p 8080:8080 fishjerky/c9-go -a user:pass
```

Note: the password will be easily visible to anyone in the docker group, so no valuable passwords!


# Command Note
//build base image
sudo docker build -f Dockerfile-base --tag fishjerky/centos-base:7 .

//build cloud 9 with go 
sudo docker build -f Dockerfile-c9-go  -t fishjerky/c9-go:1.16.5 .

//save image
docker save -o c9sdk-go1.16.5.tar fishjerky/c9-go:1.16.5
