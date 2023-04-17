FROM ubuntu:latest

RUN apt-get update  -y \
    && apt-get upgrade -y \
    && apt-get install -y curl \
    && curl -sL https://deb.nodesource.com/setup_16.x | bash - \
    && apt-get install -y nodejs \
    ssh \
    sshpass \
    sudo \
    software-properties-common

COPY . /app

WORKDIR /app

COPY startup.sh .

RUN useradd -rm -d /app -s /bin/bash -g root -G sudo -u 1001 ansible_user
RUN echo ansible_user:12345 | chpasswd
RUN echo "ansible_user ALL=(ALL:ALL) NOPASSWD: ALL" |  EDITOR="tee -a"  visudo

ENV NODE_ENV=production

RUN npm install

EXPOSE 3000

CMD /bin/bash startup.sh & npm start 
