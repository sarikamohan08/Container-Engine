
# Container-Engine

access file without build tools open terminal sudo apt updater


## Prerequisite
- Windows 10 (host machine)
- ubuntu (guest machine) (latest version)with memory of 110gb 



  
## Environment Setup

To run this project, you will need to add the following environment variables to your .env file

step 1: open ubuntu terminal 
`sudo apt update`

step 2: Settings->network-> advanced ->port forwarding click add in terminal check ifconfig set Host IP 0.0.0.0 set Host POrt 20022 set Guest IP 10.0.2.15 set Guest Port 22 and give allow access


step 3: install ssh in terminal(ubuntu)
`sudo apt install ssh ` and
`systemctl status ssh`

step 4: connect guest and host via cmd 
`ssh sarika@127.0.0.1 -p 20022` (replace sarika with guest machine's name)


continue with host cmd

step 5: install go complier `sudo apt install golang-go`

step 6: create a go file `vi hello.go`

step 7: add the following helloworld program in hello.go file

``` http
package main

import (
	"fmt"
)

func main() {
	fmt.Println("Hello, playground")
}
```

step 8: run the go file by one of the methods 

 `go run hello.go`

 `go build hello.go`

 `./hello`

- [docker docs](https://docs.docker.com/engine/install/ubuntu/)

 step 9: Update the apt package index and install packages to allow apt to use a repository over HTTPS

 ``` http
 sudo apt-get install
apt-transport-https
ca-certificates
curl
gnupg
lsb-release 
```
 step 10 : Add Docker’s official GPG key

 ` curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg`

 step 11: Use the following command to set up the stable repository
 ```http
  echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  ```

step 12 : to see the changes  `sudo apt-get update`

step 13: Install Docker Engine

```http
 sudo apt-get update
 sudo apt-get install docker-ce docker-ce-cli containerd.io
 ```

 step 14: check the installation  enter the command `docker`

 step 15: remove the go complier `sudo apt remove golang-go`

 step 16: check the directory for `hello.go` it wont be there  but we can find binary file run (hello)

 step 17: run the binary file `./hello`

back to ubuntu vm


 step 18:  open text file `vi DockerFile` add the following content

 ```http
  from golang:latest 
  copy hello.go . 
  cmd go run test.go
```
ready to run Dockerfile image in Host(windows command prompt)

step 19: run the following command to build your docker image

```http
sudo docker build -t test:1 .
```

it shows "Successfully tagged test:1"

step 20: load the docker images 
`sudo docker images`







  
## Running Tests

To run tests, run the following command

```bash
  sudo docker run test:1
```

  