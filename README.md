Under the guidance of Vimal Daga Sir, I have made this final project which opens a GUI like Firefox inside a main server whilst accessing it from a docker container to show remote access.

## Set-up required:
I am using RHEL (Red Hat Enterprise Linux) 8, along with yum and docker configured for future operations.
## Environment settings:
Firewall sometimes blocks installation through yum, hence we have to disable the firewall using the following code: -
  systemctl stop firewalld
We have to start docker service for us to use it
  systemctl start docker
To disable security we use 
  xhost +
## For reference see screenshot folder            
## Image used:
Centos OS:  I used Centos OS for my docker image with the command: -
docker pull centos

## Configuring dockers:
	I have created a docker with the name client which will act as our user using command :-
			docker run -it –name client centos

To start network access to root/server with docker, we need to establish an ssh network. But docker by default does not contain any ssh files. For this we use yum command to install the necessary things.

   yum install openssh-server
  
  "Screenshot image 1"
  
 	yum install openssh-clients
  
   "Screenshot image 2"
   
Now, in our root/server we use ifconfig enp0s3 to find out the ip address which we need for ssh.
   "Screenshot image 3"
 
In client side, we use ssh 10.0.2.15 to login to servers’ side remotely.
   "Screenshot image 4"
 
We are now logged in to server’s root. To display short commands like date and cal on server, we use tty to see the server’s address to display the ouput of date. By using the following command we can see the output is displayed on server’s side. 
		date > /dev/pts/1
 
   "Screenshot image 5"

Once connection is established, to display Firefox which is a GUI, we have to assign DISPLAY to GUI window.
   "Screenshot image 6"

We can now see firefox opened in server’s side.
   "Screenshot image 7"

References:
IIEC_connect :- https://www.youtube.com/channel/UCtY-JhEZ3iPLtozWGgd2efQ 

