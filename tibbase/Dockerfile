FROM anapsix/alpine-java

MAINTAINER Jagadish Nagarajaiah <jaganaga@cisco.com>

RUN addgroup -g 433 -S tibgrp && \
	adduser -u 431 -D -S -G tibgrp -h /home/tibusr -s /bin/bash -g "TIBCO user" tibusr && \
	chown -R tibusr:tibgrp /home/tibusr && \
	mkdir -p /opt/tibco && \
	chown -R tibusr:tibgrp /opt/tibco && \
	mkdir -p /tmp/install && \
	chown -R tibusr:tibgrp /tmp/install

USER tibusr
