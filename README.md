# Python3.9.16-Env

## This is a Docker container for Python3.9.16 environment
### How to use 
1. git clone https://github.com/toshikondo/Python3.9.16-Env.git
2. cd ~/Python3.9.16-Env
3. $docker build -f ./docker/Dockerfile ./docker -t \<docker image\>
4. $docker run -p 51022:22 -v ~/Python3.9.16-Env/PermanentData:/root/PemanentData -d \<docker image name or ID\>  
5. Login remote device  
   ssh root@\<ip address of docker host\> -p 51022  
   password: mypassword

- All files in PermanetData directory is untracked.
- PermanetData directory on host is mounted /root/PemanentData on container. 
- If you want to add a python package you need to add the package's name on requirements.txt 
