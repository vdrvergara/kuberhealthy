FROM golang AS builder
RUN apk upgrade
ADD . /build
WORKDIR /build/cmd/dns-resolution-check
ENV CGO_ENABLED=0
RUN go test -v
RUN go build -v

FROM scratch
COPY --from=builder /build/cmd/dns-resolution-check/dns-status-check /app/dns-resolution-check
ENTRYPOINT ["/app/dns-resolution-check"]
