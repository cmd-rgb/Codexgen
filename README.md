# Codexgen
Codexgen is an open source development platform packed with the power of code hosting.

## Codexgen Development
### Pre-Requisites

- Install the latest stable version of Node and Go version 1.19 or higher, and then install the below Go programs. 
- Ensure the GOPATH [bin directory](https://go.dev/doc/gopath_code#GOPATH) is added to your $PATH.

Install **protobuf**:
- Check if you've already installed protobuf ```protoc --version```
- If your version is different than v3.21.11, run ```brew unlink protobuf```
- Get v3.21.11 ```curl -s https://raw.githubusercontent.com/Homebrew/homebrew-core/9de8de7a533609ebfded833480c1f7c05a3448cb/Formula/protobuf.rb > /tmp/protobuf.rb```
- Install it ```brew install /tmp/protobuf.rb```
- Check out your version ```protoc --version```

Install **protoc-gen-go** and **protoc-gen-go-rpc**:

- Install protoc-gen-go v1.28.1 ```go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.28.1```
  - Note that this will install a binary in $GOBIN so make sure $GOBIN is in your $PATH.

- Install protoc-gen-go-grpc v1.2.0 ```go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2.0```

```bash
$ make dep
$ make tools
```

### Build

First step is to build the user interface artifacts:

```bash
$ pushd web
$ yarn install
$ yarn build
$ popd
```

After that, you can build the Codexgen binary:

```bash
$ make build
```

### Run

This project supports all operating systems and architectures supported by Go.  This means you can build and run the system on your machine; docker containers are not required for local development and testing.

To start the server at `localhost:5555`, simply run the following command:

```bash
./codexgen server .local.env
```

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
This project includes **VERY** basic command line tools for development and running the service. Please remember that you must start the server before you can execute commands.

For a full list of supported operations, please see
```bash
$ ./codexgen --help
```
