FROM ubuntu

RUN apt-get update -y \
    && apt-get upgrade -y \ 
    && apt-get install -y \
    ssh \
    sudo \
    software-properties-common \
    nodejs \
    npm

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

RUN useradd -rm -d /home/capstone-container -s /bin/bash -g root -G sudo -u 1001 capstone-container \
    && echo capstone-container:12345 | chpasswd \
    && echo "capstone-container ALL=(ALL: ALL) NOPASSWD: ALL" | EDITOR="tee -a" visudo \ && mkdir -p /home/capstone-container/.ssh
    
CMD service ssh start && npm start
