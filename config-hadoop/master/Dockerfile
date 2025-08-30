# Base Image
FROM hadoop-base1

USER hadoopquocduc
WORKDIR /home/hadoopquocduc

# Copy Hadoop configuration files
COPY config/core-site.xml /home/hadoopquocduc/hadoop/etc/hadoop/core-site.xml
COPY config/hdfs-site.xml /home/hadoopquocduc/hadoop/etc/hadoop/hdfs-site.xml
COPY config/mapred-site.xml /home/hadoopquocduc/hadoop/etc/hadoop/mapred-site.xml
COPY config/yarn-site.xml /home/hadoopquocduc/hadoop/etc/hadoop/yarn-site.xml

USER root
# Convert files to Unix format
RUN dos2unix /home/hadoopquocduc/hadoop/etc/hadoop/core-site.xml && \
    dos2unix /home/hadoopquocduc/hadoop/etc/hadoop/hdfs-site.xml && \
    dos2unix /home/hadoopquocduc/hadoop/etc/hadoop/yarn-site.xml && \
    dos2unix /home/hadoopquocduc/hadoop/etc/hadoop/mapred-site.xml

# Format HDFS
USER hadoopquocduc
RUN hdfs namenode -format

USER root
# Start SSH and Hadoop services
CMD ["/bin/bash", "-c", "service ssh start && su - hadoopquocduc && bash"]
