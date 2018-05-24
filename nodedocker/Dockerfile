FROM phusion/baseimage

RUN rm /bin/sh && ln -s /bin/bash /bin/sh

# Install packages
RUN apt-get update && apt-get -y upgrade

# 配置环境变量
ENV NVM_DIR /usr/local/nvm
ENV NODE_VERSION 10.2.0
 
# 下载和配置Node.js环境
# 这些命令一定要写在一起, 否则`nvm`命令会找不到
RUN curl https://raw.githubusercontent.com/creationix/nvm/v0.33.2/install.sh | bash \
    && source $NVM_DIR/nvm.sh \
    && nvm install v$NODE_VERSION \
    && nvm use v$NODE_VERSION \
    && nvm alias default v$NODE_VERSION
 
ENV NODE_PATH $NVM_DIR/v$NODE_VERSION/lib/node_modules
ENV PATH      $NVM_DIR/v$NODE_VERSION/bin:$PATH

RUN apt-get install -y git npm

RUN npm install -g pm2
RUN ln -s /usr/bin/nodejs /usr/bin/node

RUN npm install -g cnpm --registry=https://registry.npm.taobao.org

WORKDIR /server
VOLUME ["/server"]
CMD ["/sbin/my_init"]
RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
