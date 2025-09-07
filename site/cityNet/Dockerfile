FROM ubuntu:latest
RUN apt-get update -y && apt-get install -y vim nano less net-tools curl openssh-server

RUN useradd -m -s /bin/bash cityadmin
RUN echo 'cityadmin:passwd' | chpasswd

COPY ./banner.sh /home/cityadmin
RUN chmod +x /home/cityadmin/banner.sh
COPY ./.bashrc /home/cityadmin
RUN chown cityadmin:cityadmin /home/cityadmin/banner.sh /home/cityadmin/.bashrc

WORKDIR /home/cityadmin/
RUN mkdir -p /run/sshd
RUN echo "Port 22" >> /etc/ssh/sshd_config  
RUN echo "PasswordAuthentication yes" >> /etc/ssh/sshd_config
RUN echo "PermitRootLogin yes" >> /etc/ssh/sshd_config

CMD ["/usr/sbin/sshd","-D"]
