# Python3.9.16-Env

## This is a Docker container for Python3.9.16 environment
### How to use __without docker-compose__
1. Download file  
   >git clone https://github.com/toshikondo/Python3.9.16-Env.git
2. Move to Python3.9.16-Env directory  
   >cd Python3.9.16-Env
3. Build Docker image
   >$docker build -f ./docker/Dockerfile ./docker --build-arg PASSWD=\<YOUR PASSWORD\> -t \<docker image\> 
4. Run Docker container
   >$docker run -p 51022:22 -v ./PermanentData:/root/PemanentData -d \<docker image name or ID\>  
5. Login Docker container from remote device  
   &emsp;Login remote device  
   &emsp;ssh root@\<ip address of docker host\> -p 51022  
   &emsp;password: \<YOUR PASSWORD\>   (If you did not set YOUR PASSWORD default password is "mypassword")
### How to use __with docker-compose__
1. Download file  
   >git clone https://github.com/toshikondo/Python3.9.16-Env.git
2. Move to Python3.9.16-Env directory
   >cd Python3.9.16-Env
3. Set your own password. (If you did not edit the password defauld password is "mypassword")
   &emsp;Edit password(PASSWD: \<YOUR PASSWORD\>) in docker-compose.yml to set your own password.  
4. Build & RUN Docker container
   >docker compose up -d --build
5. Login Docker container from remote device  
   &emsp;Login remote device  
   &emsp;ssh root@\<ip address of docker host\> -p 51022  
   &emsp;password: \<YOUR PASSWORD\>   (If you did not set YOUR PASSWORD default password is "mypassword")

- All files in PermanetData directory is untracked.
- PermanetData directory on host is mounted /root/PemanentData on container. 
- If you want to add a python package you need to add the package's name on requirements.txt 
