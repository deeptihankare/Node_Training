# Node_Training

# Proxy Server

This is a Proxy Server for Node.js submitted as the [pre-work](http://courses.codepath.com/snippets/intro_to_nodejs/prework) requirement for CodePath.

Time spent: 18 hours

Completed:

* [Completed] Required: Requests to port `8000` are echoed back with the same HTTP headers and body
* [Completed] Required: Requests/reponses are proxied to/from the destination server
* [Completed] Required: The destination server is configurable via the `--host`, `--port`  or `--url` arguments
* [Completed] Required: The destination server is configurable via the `x-destination-url` header
* [Completed] Required: Client requests and respones are printed to stdout
* [Completed] Required: The `--logfile` argument outputs all logs to the file specified instead of stdout
* [] Optional: The `--exec` argument proxies stdin/stdout to/from the destination program
* [] Optional: The `--loglevel` argument sets the logging chattiness
* [] Optional: Supports HTTPS
* [] Optional: `-h` argument prints CLI API

Walkthrough Gif:
[![proxy_server](https://cloud.githubusercontent.com/assets/3597382/12122851/74d4ffa2-b392-11e5-8bcc-b9e616bf4b39.gif)]


Note: to embed the gif file, just check your gif file into your repo and update the name of the file above.

## Starting the Server

```bash
npm start
```

## Features

### Echo Server:

```bash
curl -v -X POST http://127.0.0.1:8000 -d "hello self" -H "x-asdf: yodawg"
* Rebuilt URL to: http://127.0.0.1:8000/
* Hostname was NOT found in DNS cache
*   Trying 127.0.0.1...
* Connected to 127.0.0.1 (127.0.0.1) port 8000 (#0)
> POST / HTTP/1.1
> User-Agent: curl/7.37.1
> Host: 127.0.0.1:8000
> Accept: */*
> x-asdf: yodawg
> Content-Length: 10
> Content-Type: application/x-www-form-urlencoded
> 
* upload completely sent off: 10 out of 10 bytes
< HTTP/1.1 200 OK
< user-agent: curl/7.37.1
< host: 127.0.0.1:8000
< accept: */*
< x-asdf: yodawg
< content-length: 10
< content-type: application/x-www-form-urlencoded
< Date: Mon, 13 Apr 2015 00:45:50 GMT
< Connection: keep-alive
< 
* Connection #0 to host 127.0.0.1 left intact
hello self
```

### Proxy Server:

Port 8001 will proxy to the echo server on port 8000.

```bash
curl -v http://127.0.0.1:8001/asdf -d "hello proxy"
* Hostname was NOT found in DNS cache
*   Trying 127.0.0.1...
* Connected to 127.0.0.1 (127.0.0.1) port 8001 (#0)
> POST /asdf HTTP/1.1
> User-Agent: curl/7.37.1
> Host: 127.0.0.1:8001
> Accept: */*
> Content-Length: 11
> Content-Type: application/x-www-form-urlencoded
> 
* upload completely sent off: 11 out of 11 bytes
< HTTP/1.1 200 OK
< user-agent: curl/7.37.1
< host: 127.0.0.1:8001
< accept: */*
< content-length: 11
< content-type: application/x-www-form-urlencoded
< connection: close
< date: Mon, 13 Apr 2015 02:03:29 GMT
< 
* Closing connection 0
hello proxy
```

### Configuration:

#### CLI Arguments:

The following CLI arguments are supported:

##### `--host`

The host of the destination server. Defaults to `127.0.0.1`.

##### `--port`

The port of the destination server. Defaults to `80` or `8000` when a host is not specified.

##### `--url`

A single url that overrides the above. E.g., `http://www.google.com`

##### `--logfile`

Specify a file path to redirect logging to.

#### Headers

The follow http header(s) are supported:

##### `x-destination-url`

Specify the destination url on a per request basis. Overrides and follows the same format as the `--url` argument.
commands used
 curl -METHOD POST http://localhost:8000  -Body "hello self"
  curl -METHOD POST http://localhost:8000  -Body "hello self" -Headers @{"x-asdf"="yodawg"}
   nodemon --exec babel-node -- -- index.js --foo=bar
      nodemon --exec babel-node -- index.js --logfile=C:/DEEPTI/WORK/proxy_server/server.log

   babel-node index.js
    curl -METHOD POST http://127.0.0.1:8001  -Body "hello self" -Headers @{"x-asdf"="yodawg"}
	curl -METHOD POST http://localhost:8001  -Body "hello self" -Headers @{"x-asdf"="yodawg"}


