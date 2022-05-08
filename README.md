# Studing Golang - gRPC 

An implementing gRPC API:

- API unary call
- API Server streaming
- API Client streaming
- API Bi directional streaming

For run all kind of gRPC's calls, you must uncomment the function calls in `cmd/client/client.go` file.


```go
func main() {
	connection, err := grpc.Dial("localhost:50051", grpc.WithInsecure())
	if err != nil {
		log.Fatalf("Could not connect to gRPC Server: %v", err)
	}
	defer connection.Close()

	client := pb.NewUserServiceClient(connection)

	//AddUser(client)
	//AddUserVerbose(client)
	//AddUsers(client)
	AddUserStreamBoth(client) // -> If u run "go run cmd/client/client.go " will start a bi directional communication 
}
```

First, run:
`go run cmd/server/server.go`
Then `go run cmd/client/client.go`