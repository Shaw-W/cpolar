FROM arm64v8/alpine:3.18 as builder

ENV RELEASE_VERSION=3.3.18

ENV MACHINE=arm64

ENV TMP_DIRECTORY=/tmp/cpolar

RUN mkdir -p $TMP_DIRECTORY && apk add --no-cache curl unzip

RUN curl -R -H 'Cache-Control: no-cache' -o "$TMP_DIRECTORY/cpolar.yml" "http://static.cpolar.com/downloads/cpolar.demo.yml"

RUN curl -R -H 'Cache-Control: no-cache' -o "$TMP_DIRECTORY/cpolar-stable-linux-$MACHINE.zip" "http://static.cpolar.com/downloads/releases/$RELEASE_VERSION/cpolar-stable-linux-$MACHINE.zip"

RUN unzip -q "$TMP_DIRECTORY/cpolar-stable-linux-$MACHINE.zip" -d $TMP_DIRECTORY

# image
FROM arm64v8/alpine:3.18

LABEL maintainer="Shaw-W <shaw.wei@qq.com>"

RUN mkdir /cpolar && mkdir /app

COPY --from=builder /tmp/cpolar/cpolar /app/cpolar

COPY --from=builder /tmp/cpolar/cpolar.yml /cpolar/cpolar.yml

ENTRYPOINT ["/app/cpolar", "start-all", "-dashboard=on", "-daemon=on", "-config=/cpolar/cpolar.yml", "-log=stdout"]
