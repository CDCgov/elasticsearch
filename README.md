ElasticSearch Container for OpenShift 3
=======================================

Version of the Elastic Co official Docker image that will run on OpenShift 3 with the default Security Context Constraint (restricted).

Notes
-----
* uses Elastic Co's [recommendations to modify official image](https://www.elastic.co/guide/en/elasticsearch/reference/current/docker.html#_c_customized_image)

* the custom `elasticsearch.yml` file disables ElasticSearch's X-Pack Security for convenience in a development environment.  The X-Pack trial license that is bundled with the official image expires after 30 days.  The included `elasticsearch.yml` sets up the container so that developers do not have to worry about making the change after the license expires.
