FROM registry.access.redhat.com/rhel6:latest
  
ADD repos/*.repo /etc/yum.repos.d/
RUN yum clean all && yum repolist && yum upgrade -y && yum clean all

# install some untils
RUN yum install -y wget tar

# install the kvm and enable libvirted
RUN yum install -y virt-manager libvirt qemu-kvm && /etc/init.d/libvirtd start

# install kvm driver for docker machine
RUN curl -L https://github.com/dhiltgen/docker-machine-kvm/releases/download/v0.7.0/docker-machine-driver-kvm -o /usr/local/bin/docker-machine-driver-kvm \
    &&  chmod +x /usr/local/bin/docker-machine-driver-kvm

# download and install minishift
RUN wget https://github.com/minishift/minishift/releases/download/v1.19.0/minishift-1.19.0-linux-amd64.tgz  \
    && tar -xvf minishift-1.19.0-linux-amd64.tgz \
    && mv minishift-1.19.0-linux-amd64 /opt/ \
    && mv /opt/minishift-1.19.0-linux-amd64 /opt/minishift \
    && echo "export PATH=${PATH}:/opt/minishift" >> /etc/profile \
    && source /etc/profile
