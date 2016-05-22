FROM gliderlabs/alpine:3.2
MAINTAINER i.am.shige@gmail.com

ENV FLUENTD_VERSION 0.14.0.pre.1

RUN apk-install ca-certificates ruby-dev build-base jemalloc-dev && \
  echo 'gem: --no-document' >> /etc/gemrc && \
  gem update --system && \
  gem install fluentd -v $FLUENTD_VERSION && \
  fluentd --setup /etc/fluent

ENV JEMALLOC_PATH /usr/lib/libjemalloc.so
COPY conf/fluentd.conf /etc/fluent/fluentd.conf
ENTRYPOINT ["/usr/bin/fluentd", "-c", "/etc/fluent/fluentd.conf"]