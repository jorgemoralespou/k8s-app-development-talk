FROM golang:1.12
WORKDIR /go/src/github.com/example/app/
COPY app.go .
RUN CGO_ENABLED=0 GOOS=linux go build -v -o app

FROM scratch
COPY --from=0 /go/src/github.com/example/app/app .
EXPOSE 80
ENTRYPOINT ["/app"]
