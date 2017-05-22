FROM phusion/baseimage

# Install packages
RUN apt-get update && apt-get -y upgrade
RUN apt-get install -y git

RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash
RUN nvm install v6.2.1
RUN nvm use v6.2.1

RUN npm install -g pm2
RUN ln -s /usr/bin/nodejs /usr/bin/node

RUN npm install -g cnpm --registry=https://registry.npm.taobao.org

WORKDIR /server
VOLUME ["/server"]
CMD ["/sbin/my_init"]
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
