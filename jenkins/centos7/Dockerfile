FROM centos:7

RUN yum -y install openssh-server

RUN useradd remote_user && \
    echo "1234" | passwd remote_user  --stdin && \
    mkdir /home/remote_user/.ssh && \
    chmod 700 /home/remote_user/.ssh && \
    mkdir /var/jenkins/ && \
    chown remote_user:remote_user /var/jenkins


COPY remote-key.pub /home/remote_user/.ssh/authorized_keys

RUN chown remote_user:remote_user   -R /home/remote_user && \
    chmod 400 /home/remote_user/.ssh/authorized_keys

RUN ssh-keygen -A

RUN yum -y install mysql

RUN yum -y install epel-release && \
    yum -y install python3-pip && \
    yum -y install java-1.8.0-openjdk && \
    pip3 install --upgrade pip && \
    pip3 install awscli

CMD /usr/sbin/sshd -D
