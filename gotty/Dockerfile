FROM golang:alpine

EXPOSE 8080

RUN apk add --update go git bash && \
  mkdir -p /tmp/gotty && \
  GOPATH=/tmp/gotty go get github.com/yudai/gotty && \
  mv /tmp/gotty/bin/gotty /usr/local/bin/ && \
  apk del go git && \
  rm -rf /tmp/gotty /var/cache/apk/*

COPY on-init /pwinit/

ENTRYPOINT ["/usr/local/bin/gotty"]
CMD ["--permit-write","--reconnect","--ws-origin","pathwar.net","/bin/bash"]
