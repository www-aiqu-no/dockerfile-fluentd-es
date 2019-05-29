ARG FLUENTD_VERSION="v1.5-1"

FROM fluent/fluentd:${FLUENTD_VERSION}

USER root

RUN apk add --no-cache --update --virtual .build-deps \
    sudo build-base ruby-dev \
  && \
    sudo gem install fluent-plugin-elasticsearch \
  && \
    sudo gem sources --clear-all \
 && \
  apk del .build-deps \
 && \
  rm -rf /tmp/* /var/tmp/* /usr/lib/ruby/gems/*/cache/*.gem

COPY fluent.conf /fluentd/etc/
COPY entrypoint.sh /bin/

USER fluent
