FROM python:3.9.16

##### Set time zone #####
ENV TZ=America/Los_Angeles
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

##### Install packages #####
RUN apt update && apt install -y \
    curl \
    git \
    vim \
    openssh-server 
    # python3-pip 

##### Change .bashrc #####
COPY .bashrc /
RUN mv .bashrc ~/.bashrc


#### Install python packages #####
WORKDIR /root
COPY requirements.txt /root
RUN python3.9 -m pip install -r requirements.txt

##### Enable ssh access from client #####
RUN mkdir /var/run/sshd
RUN echo 'root:mypassword' | chpasswd
RUN sed -ri 's/^#?PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd
ENV NOTVISIBLE "in users profile"
RUN echo "export VISIBLE=now" >> /etc/profile
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]