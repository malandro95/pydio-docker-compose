FROM ubuntu

WORKDIR /srv

RUN apt-get update && apt-get install -y --no-install-recommends gettext-base

# can be 'release/1.2.0' or 'develop'
ARG version=release/1.2.0
ADD https://download.pydio.com/pub/booster/${version}/linux_amd64/pydio /srv/
ADD *.template /srv/
ADD run.sh /srv/

RUN mv pydio pydio-booster \
 && chmod +x pydio-booster \
 && chown -R 33:33 /srv

USER www-data

#      WSS  WS   NSQ
EXPOSE 8090 8040 4150
CMD bash run.sh ./pydio-booster -conf pydioconf
