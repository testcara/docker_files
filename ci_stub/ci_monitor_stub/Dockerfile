FROM registry.access.redhat.com/rhel7:latest
  
ADD repos/*.repo /etc/yum.repos.d/
RUN yum clean all && yum repolist && yum upgrade -y && yum clean all

# install the basic packages
RUN yum install -y wget git curl java  iputils

# workdir setting
ADD . /workdir
WORKDIR /workdir

#install pip
RUN wget http://bootstrap.pypa.io/get-pip.py \
     && python get-pip.py

# install the CA
RUN wget -O /etc/pki/ca-trust/source/anchors/RH-IT-Root-CA.crt https://password.corp.redhat.com/RH-IT-Root-CA.crt \
    && update-ca-trust extract

# install the ssh-keys
ADD ssh/* /root/.ssh/
