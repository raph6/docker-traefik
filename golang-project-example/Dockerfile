FROM golang:alpine
RUN apk add -U --no-cache git ca-certificates
WORKDIR /go
COPY go.mod go.sum /go/
RUN go mod download && go mod verify
COPY . .
RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -ldflags="-w -s" .
RUN echo "nobody:x:65534:65534:Nobody:/:" > /etc_passwd


FROM scratch

COPY --from=0 /etc_passwd /etc/passwd
COPY --from=0 /go/go /go
COPY --from=0 /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/

USER nobody

EXPOSE 8080
ENV GIN_MODE=release
ENTRYPOINT ["/go"]