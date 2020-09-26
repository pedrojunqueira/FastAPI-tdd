# Test-Driven Development with FastAPI and Docker

![Continuous Integration and Delivery](https://github.com/pedrojunqueira/fastapi-tdd/workflows/Continuous%20Integration%20and%20Delivery/badge.svg?branch=master)

# FastAPI application from testdriven.io tutorial course

FastAPI makes API development fast, fun and performing

It has an amazing documentation and very accessible.

This application is just a simple application that demonstrates the functionality and easy of use of FastAPI.

## Usage

### Start

```bash
docker-compose up -d --build
```
### Stop

```bash
docker-compose down
```

Application will be running on http://0.0.0.0:8002/ping

The heart beat response should be

```bash
$ http http://0.0.0.0:8002/ping
HTTP/1.1 200 OK
content-length: 52
content-type: application/json
date: Sat, 26 Sep 2020 02:26:19 GMT
server: uvicorn

{
    "environment": "dev",
    "ping": "pong!",
    "testing": false
}
```

## REST Routes

### POST

```bash
http --json POST http://localhost:8002/summaries/ url=http://testdriven.io
HTTP/1.1 201 Created
content-length: 37
content-type: application/json
date: Tue, 26 May 2020 21:12:14 GMT
server: uvicorn

{
    "id": 1,
    "url": "http://testdriven.io"
}
```

### GET

#### Single entry by id

```bash
$ http http://0.0.0.0:8002/summaries/1/
HTTP/1.1 200 OK
content-length: 105
content-type: application/json
date: Sat, 26 Sep 2020 02:29:38 GMT
server: uvicorn

{
    "created_at": "2020-09-26T01:40:11.162371",
    "id": 1,
    "summary": "dummy summary",
    "url": "http://testdriven.io"
}
```

#### all summaries

```bash
$ http http://0.0.0.0:8002/summaries/
HTTP/1.1 200 OK
content-length: 324
content-type: application/json
date: Sat, 26 Sep 2020 02:30:15 GMT
server: uvicorn

[
    {
        "created_at": "2020-09-26T01:40:11.162371",
        "id": 1,
        "summary": "dummy summary",
        "url": "http://testdriven.io"
    },
    {
        "created_at": "2020-09-26T01:41:40.203105",
        "id": 2,
        "summary": "dummy summary",
        "url": "https://download-data.com"
    }
]
```

currently app is deployed at [Heroku](https://www.heroku.com/home) on https://fastapi-pedro.herokuapp.com/docs
