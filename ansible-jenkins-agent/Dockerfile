FROM ubuntu

ENV DEBIAN_FRONTEND=noninteractive

EXPOSE 22/tcp

ADD start.sh /
RUN chmod +x /start.sh
RUN apt update -y
RUN apt upgrade -y
RUN apt install git -y
RUN apt install default-jdk -y
RUN apt-get install python3 -y
RUN apt-get install python3-pip -y
RUN pip3 install ansible
RUN apt-get install openssh-server -y
RUN sed 's/\#Port/Port/' /etc/ssh/sshd_config
RUN echo "PermitRootLogin yes" >> /etc/ssh/sshd_config
RUN echo "root:jenkins_agent" | chpasswd
RUN service ssh start
RUN sh start.sh

CMD ["/start.sh"]