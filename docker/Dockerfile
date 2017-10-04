FROM docker.elastic.co/elasticsearch/elasticsearch:5.6.2

MAINTAINER Tim Taylor <mpx1@cdc.giv>

# ElasticSearch image for OpenShift 3 with the following properties:
#   - runs under the restricted (default) Security Context Constraints
#   - runs without XPACK (set in custom elasticsearch.yml)
#
#
# Volumes:
#  * /usr/share/elasticsearch/config
#  * /elasticsearch/persistent

EXPOSE 9200
EXPOSE 9300
USER 0

ENV ES_HOME=/usr/share/elasticsearch \
    ES_VER=5.6.2


#WORKDIR ${ES_HOME}


COPY elasticsearch.yml /usr/share/elasticsearch/config/

RUN chown -R 1001:0 ${ES_HOME} && \
    chmod g+rwx ${ES_HOME} && \
    chmod g+rw ${ES_HOME}/{config,data,logs}

USER 1001

# use the default RUN directive from official container
