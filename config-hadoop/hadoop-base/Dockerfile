# Base Image
FROM ubuntu:22.04

LABEL maintainer="DOCUTEE <work.docutee@outlook.com>"

# Set root password
RUN echo "root:root" | chpasswd

# Update and install required packages
RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y openjdk-11-jdk wget ssh openssh-server dos2unix vim sudo telnet iputils-ping && \
    apt-get clean

# Set environment variables
ENV JAVA_HOME=/usr/lib/jvm/java-1.11.0-openjdk-arm64
ENV HADOOP_HOME=/home/hadoopquocduc/hadoop
ENV PATH=$PATH:$HADOOP_HOME/bin:$HADOOP_HOME/sbin:$JAVA_HOME/bin

# Create user hadoopquocduc
RUN adduser --disabled-password --gecos "" hadoopquocduc && \
    echo "hadoopquocduc:hadoopquocduc" | chpasswd && \
    usermod -aG sudo hadoopquocduc && \
    echo "hadoopquocduc ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers

# Install Hadoop
USER hadoopquocduc

WORKDIR /home/hadoopquocduc
RUN wget https://dlcdn.apache.org/hadoop/common/hadoop-3.4.1/hadoop-3.4.1.tar.gz && \
    tar -xzf hadoop-3.4.1.tar.gz && \
    mv hadoop-3.4.1 hadoop && \
    rm hadoop-3.4.1.tar.gz

# Set JAVA_HOME in hadoop-env.sh
RUN echo "export JAVA_HOME=/usr/lib/jvm/java-1.11.0-openjdk-arm64" >> /home/hadoopquocduc/hadoop/etc/hadoop/hadoop-env.sh
    

# Copy Hadoop configuration files
COPY .bashrc /home/hadoopquocduc/.bashrc

RUN mkdir -p /home/hadoopquocduc/.ssh && \
    ssh-keygen -t rsa -P '' -f /home/hadoopquocduc/.ssh/id_rsa && \
    cat /home/hadoopquocduc/.ssh/id_rsa.pub >> /home/hadoopquocduc/.ssh/authorized_keys && \
    chmod 600 /home/hadoopquocduc/.ssh/authorized_keys && \
    chown -R hadoopquocduc:hadoopquocduc /home/hadoopquocduc/.ssh

# Add permission to ssh folder and keys
USER root

# Convert files to Unix format
RUN dos2unix /home/hadoopquocduc/.bashrc 

# Expose ports
EXPOSE 9000 50070 9001 9002 9003 9004 9005 9006 9870 9864 8088 8042
