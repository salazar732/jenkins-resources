FROM jenkins/jenkins

USER root

RUN apt-get update && apt-get install python3-pip -y && \
    pip3 install ansible --upgrade && \
    mkdir /etc/ansible

COPY  ansible.cfg /etc/ansible/ansible.cfg

USER jenkins
