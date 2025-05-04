FROM golang:1.18 AS build

# Clean up legacy Debian mirror issues
RUN sed -i 's|deb.debian.org|archive.debian.org|g' /etc/apt/sources.list && \
    sed -i 's|security.debian.org|archive.debian.org|g' /etc/apt/sources.list && \
    sed -i '/stretch-updates/d' /etc/apt/sources.list && \
    apt-get update && apt-get install -y zip libc6-dev-i386 nmap

WORKDIR /go/src/github.com/marco-lancini/goscan

COPY . .

RUN go mod tidy
RUN go build -o /bin/goscan

ENTRYPOINT ["/bin/goscan"]