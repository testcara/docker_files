From centos:latest
MAINTAINER cara wang wlin@redhat.com
# add nginx repo
ADD nginx.repo /etc/yum.repos.d/nginx.repo
# install nginx
RUN yum install -y  nginx
# change the index html
RUN echo "<strong> I am one nginx server</strong>" > /usr/share/nginx/html/index.html
EXPOSE 80
# as default, start the nginx service
ENTRYPOINT ["/usr/sbin/nginx"]
CMD ["-h"]
