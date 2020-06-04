#FROM kong:0.9.9

# ensure Kong logs go to the log pipe from our entrypoint and so to docker logging
#RUN mkdir -p /usr/local/kong/logs \
#    && ln -sf /dev/stdout /usr/local/kong/logs/serf.log \
#    && ln -sf /dev/stderr /usr/local/kong/logs/error.log \
#    && ln -sf /dev/stdout /usr/local/kong/logs/access.log


#=========================================================================

FROM keshavprasad/kong:0.12.3

RUN yum install -y net-tools

COPY docker-entrypoint.sh /docker-entrypoint.sh
ENTRYPOINT ["/docker-entrypoint.sh"]

# ensure Kong logs go to the log pipe from our entrypoint and so to docker logging
RUN mkdir -p /usr/local/kong/logs \
    && ln -sf /tmp/logpipe /usr/local/kong/logs/access.log \
    && ln -sf /tmp/logpipe /usr/local/kong/logs/serf.log \
    && ln -sf /tmp/logpipe /usr/local/kong/logs/error.log

EXPOSE 8000 8443 8001 7946
CMD ["kong", "start"]
