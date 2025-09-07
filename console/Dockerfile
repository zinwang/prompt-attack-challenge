FROM ubuntu:latest

RUN apt-get update -y && apt-get install -y zsh vim nano less net-tools curl sshpass tmux bat openssh-server
RUN ln -s /usr/bin/batcat /usr/bin/bat
RUN curl -L -o chatgpt https://github.com/kardolus/chatgpt-cli/releases/latest/download/chatgpt-linux-amd64 && chmod +x chatgpt &&  mv chatgpt /usr/local/bin/

RUN useradd -m -s /bin/bash player
RUN chsh -s /usr/bin/zsh player
RUN echo 'player:isc' | chpasswd

COPY ./setenv.sh /home/player
RUN chmod +x /home/player/setenv.sh
COPY ./.tmux.conf /home/player
COPY ./newsess /home/player
COPY ./judge /home/player
COPY ./.chatgpt-cli /home/player/.chatgpt-cli
COPY ./challenge-1 /home/player/challenge-1
COPY ./docs /home/player/docs
RUN chown -R player:player /home/player/.tmux.conf /home/player/docs /home/player/challenge-1 /home/player/.chatgpt-cli/config.yaml

WORKDIR /home/player/

RUN mkdir -p /run/sshd
RUN echo "Port 22" >> /etc/ssh/sshd_config  
RUN echo "PasswordAuthentication yes" >> /etc/ssh/sshd_config
RUN echo "PermitRootLogin yes" >> /etc/ssh/sshd_config

CMD ["bash", "-c", "./setenv.sh; /usr/sbin/sshd -D"]
