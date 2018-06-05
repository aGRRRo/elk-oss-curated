FROM docker.elastic.co/elasticsearch/elasticsearch-oss:6.2.4
MAINTAINER Nikolai Khvatov <n.hvatov@gmail.com>

ENV CURATOR_LOG_LEVEL=INFO
ENV CURATOR_FILTER_VALUE=logstash-*
ENV CURATOR_UNITS=days
ENV CURATOR_UNIT_COUNT=15



RUN curl "https://bootstrap.pypa.io/get-pip.py" -o "get-pip.py"
RUN python get-pip.py
RUN pip install elasticsearch-curator
RUN /usr/bin/curator --version
RUN yum install crontabs -y
RUN mkdir /usr/share/elasticsearch/curator
COPY elasticsearch/build_config/action_file.yml /usr/share/elasticsearch/curator/action_file.yml
COPY elasticsearch/build_config/curator.yml /usr/share/elasticsearch/curator/curator.yml
RUN echo "0 0 * * * /usr/bin/curator --config /usr/share/elasticsearch/curator/curator.yml /usr/share/elasticsearch/curator/action_file.yml 2>&1" >> /var/spool/cron/root
