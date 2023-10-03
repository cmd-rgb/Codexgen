# Codexgen
Codexgen is an open source development platform packed with the power of code hosting and automated DevOps pipelines.

## Overview
Codexgen is an open source development platform packed with the power of code hosting and automated continuous integration pipelines.

## Codexgen Development
### Pre-Requisites

TO-DO

### Build

TO-DO

### Run

TO-DO

## User Interface

This project includes a full user interface for interacting with the system. When you run the application, you can access the user interface by navigating to `http://localhost:5555` in your browser.

## REST API

This project includes a swagger specification. When you run the application, you can access the swagger specification by navigating to `http://localhost:5555/swagger` in your browser (for raw yaml see `http://localhost:5555/openapi.yaml`).


For testing, it's simplest to just use the cli to create a token (this requires codexgen server to run):
```bash
# LOGIN (user: admin, pw: changeit)
$ ./codexgen login

# GENERATE PAT (1 YEAR VALIDITY)
$ ./codexgen user pat "my-pat-uid" 3684101
```

The command outputs a valid PAT that has been granted full access as the user.
The token can then be send as part of the `Authorization` header with Postman or curl:

```bash
$ curl http://localhost:5555/api/v1/user \
-H "Authorization: Bearer $TOKEN"
```


## CLI
This project includes VERY basic command line tools for development and running the service. Please remember that you must start the server before you can execute commands.

For a full list of supported operations, please see
```bash
$ ./codexgen --help
```
