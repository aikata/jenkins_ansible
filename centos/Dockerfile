FROM centos:7
ADD https://github.com/krallin/tini/releases/download/v0.19.0/tini /tini
EXPOSE 22
RUN yum -y install openssh openssh-server openssh-clients && \
    yum -y clean all
RUN ssh-keygen -t ed25519 -f /etc/ssh/ssh_host_ed25519_key && \
    ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
RUN useradd jenkins && \
    mkdir /home/jenkins/.ssh
ADD ./ssh/ /home/jenkins/.ssh
RUN chown -R jenkins:jenkins /home/jenkins
RUN chmod 755 /home/jenkins/.ssh
RUN chmod -R 600 /home/jenkins/.ssh
ADD start.sh /start.sh
RUN chmod +x /start.sh /tini
ENTRYPOINT ["/tini", "-g", "--"]
CMD /start.sh
