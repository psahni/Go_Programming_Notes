### gRPC

Remote procedure call

#### Microservices communication
Allows the client to execute remote function on the server
Go client can call a server function written in rust

#### 3 Steps
* Define API and data structure/Schema
* RPC and its req/res are defined using protobuf
* Generate gRPC stubs (welcome.proto)  (welcome.go) (protoc)
* Implement the server
* Use the client

### Why gRPC
* High performance
* HTTP2
* Bidirectional communication
* Binary framing
* Strong API contract (protbufs)
* Protbuf is made of binary encoding which is must faster than json

### 4 Types of Grpc
* Unary
* Client Streaming grpc
* Server Streaming grpc
* Bi directional gRPC

### gRPC gateway
Serve both gRPC and HTTP requests at once

Go files are generated using protoc command


https://grpc.io/docs/languages/go/quickstart/

Gin server is converted to grpc server
Evans client is grpc client used for calling grpc apis

```Go
type Server struct {
  pb.UnimplementedSimpleServer
  ..
}
```

UnimplementedSimpleServer must be embedded to have forward compatible implementation, which means the server can accept calls to CreateUser and LoginUser RPCs before they are actually implemented. We can give their actual implementation later.

