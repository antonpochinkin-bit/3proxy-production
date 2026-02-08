FROM alpine:latest

RUN echo "http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories && \
    apk update && \
    apk add --no-cache 3proxy curl

CMD ["3proxy", "/etc/3proxy/3proxy.cfg"]
