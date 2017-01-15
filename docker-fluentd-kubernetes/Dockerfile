FROM fabric8/fluentd:0.14.8

MAINTAINER Jimmi Dyson <jimmidyson@gmail.com>

ENTRYPOINT ["/start-fluentd"]

ENV ELASTICSEARCH_HOST elasticsearch.default.svc.cluster.local

RUN touch /var/lib/rpm/* && yum install -y gcc-c++ && yum clean all

RUN scl enable rh-ruby23 'gem install --no-document fluent-plugin-kubernetes_metadata_filter -v 0.26.2' && \
    scl enable rh-ruby23 'gem install --no-document fluent-plugin-elasticsearch -v 1.9.2' && \
    scl enable rh-ruby23 'gem install --no-document fluent-plugin-prometheus -v 0.2.1' && \
    scl enable rh-ruby23 'gem cleanup fluentd'

ADD start-fluentd.sh /start-fluentd
