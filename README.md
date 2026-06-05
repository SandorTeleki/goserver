# goserver

Go HTTP server and a Python bookbot script, both containerized with Docker. Based on the Boot.dev course [Learn Docker](https://www.boot.dev/courses/learn-docker).

## Go Server

A minimal HTTP server written in Go that serves an HTML page. The port is configurable via the `PORT` environment variable.

### Run locally

```bash
export PORT="8991"
go build -o goserver
./goserver
```

### Run with Docker

Build and run the containerized Go server:

```bash
GOOS=linux GOARCH=amd64 go build -o goserver
docker build . -t dailyjoe/goserver:0.2.0
docker run -p 8991:8991 dailyjoe/goserver:0.2.0
```

The server will be available at http://localhost:8991.

## Bookbot (Python)

A Python script that reads `books/frankenstein.txt` and generates a report on word count and character frequency.

### Run locally

```bash
python3 main.py
```

### Run with Docker

```bash
docker build -t bookbot -f Dockerfile.py .
docker run bookbot
```

This image builds Python 3.10 from source inside a Debian slim container.

## Docker Hub

The Go server image is published at [dailyjoe/goserver](https://hub.docker.com/r/dailyjoe/goserver).

```bash
docker pull dailyjoe/goserver:0.2.0
```
