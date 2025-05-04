FROM golang:1.18 AS build

RUN apt-get update && apt-get install -y zip libc6-dev-i386 nmap && rm -rf /var/lib/apt/lists/*

WORKDIR /go/src/github.com/marco-lancini/goscan

COPY . .

RUN go mod tidy
RUN go build -o /bin/goscan

ENTRYPOINT ["/bin/goscan"]
