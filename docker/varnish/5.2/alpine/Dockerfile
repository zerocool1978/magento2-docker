FROM    alpine:3.7

LABEL   maintainer="zerocool78"

ENV     VARNISH_CACHE_SIZE=${VARNISH_CACHE_SIZE:-'256M'} \
        VARNISHD_OPTS=${VARNISHD_OPTS:-'-p default_ttl=3600 -p default_grace=3600 -p feature=+esi_ignore_https -p feature=+esi_disable_xml_check'} \
        VARNISH_VCL=${VARNISH_VCL:-'/etc/varnish/default.vcl'}

RUN     set -x && \
        apk add --no-cache --upgrade \
            varnish=5.2.1-r0 && \
        rm -rf /tmp/* /var/cache/apk/*

COPY    conf/default.vcl /etc/varnish/default.vcl
COPY    start.sh /usr/local/bin/start

CMD     /usr/local/bin/start