FROM docker.elastic.co/elasticsearch/elasticsearch:5.6.2

MAINTAINER Tim Taylor <ttaylor@mitre.org>

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

#######################
# MITRE Additions
#######################

ENV http_proxy=http://gatekeeper.mitre.org:80/ \
    https_proxy=http://gatekeeper.mitre.org:80/ \
    no_proxy=localhost

# Add MITRE CA certificates to system trusted store
COPY certs/*.pem /etc/pki/ca-trust/source/anchors/
RUN /usr/bin/update-ca-trust extract

#######################
# end MITRE Additions
#######################


COPY elasticsearch.yml /usr/share/elasticsearch/config/



RUN chown -R 1001:0 ${ES_HOME} && \
    chmod g+rwx ${ES_HOME} && \
    chmod g+rw ${ES_HOME}/{config,data,logs}

USER 1001

# use the default RUN directive from official container
