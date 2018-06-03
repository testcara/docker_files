FROM centos:latest
MAINTAINER cara wang wlin@redhat.com
RUN useradd sshuser 
RUN echo "sshuser:sshuser" | chpasswd
Run echo "sshuser  ALL=(ALL)       NOPASSWD: ALL" >> /etc/sudoers 
RUN yum install -y openssh-server
RUN ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key 
RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
RUN ssh-keygen -t ed25519 -f /etc/ssh/ssh_host_ed25519_key
EXPOSE 22
CMD ['/user/bin/sshd']

