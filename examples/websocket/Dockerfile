FROM golang:1.8-alpine
ADD . /go/src/websocket
RUN apk update && apk upgrade && \
    apk add --no-cache bash git openssh
RUN go get github.com/gorilla/websocket
RUN go install github.com/gorilla/websocket
RUN go install websocket

FROM alpine:latest
COPY --from=0 /go/bin/websocket .
ENV PORT 8080
CMD ["./websocket"]
