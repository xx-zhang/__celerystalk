from ubuntu:trusty

ENV WORKDIR /usr/local/src

RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak && \
cat > /etc/apt/sources.list <<- EOF
deb http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ trusty-backports main restricted universe multiverse
EOF

RUN apt-get install wget unzip curl git -y
RUN apt-get install software-properties-common -y && \
add-apt-repository ppa:jonathonf/python3.6 && \
apt-get -y update && apt-get install python3.6 -y

RUN rm /usr/bin/python3 && ln -sn /usr/bin/python3.6 /usr/bin/python3
RUN cd ${WORKDIR} && curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py && python3 get-pip.py && python get-pip.py

RUN apt-get update -qq && apt-get install -y nmap redis-server
RUN pip install six --upgrade --ignore-installed six

RUN cd ${WORKDIR} && git clone https://github.com/the-champions-of-capua/celerystalk \
 && cd celerystalk/setup && ./install.sh

WORKDIR ${WORKDIR}/celerystalk

USER root
