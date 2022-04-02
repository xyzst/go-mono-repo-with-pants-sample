# mono repository pattern w/ go & pants

## build without pants
```text
# protocol buffer and grpc codegen step w/ protoc
$ protoc --go_out=./ --go_opt=paths=source_relative \
    --go-grpc_out=./ --go-grpc_opt=paths=source_relative \
    ./pkg/model/hello_world.proto
 
# build server component
$ go build -o srv cmd/server/main.go

# build client component
$ go build -o clt cmd/client/main.go
```

## run
```text
# if you did not use pants, run the following commands in separate terminal instances
$ ./srv  
2022/04/02 13:48:54 server listening at [::]:50051

$ ./clt
2022/04/02 13:49:17 Greeting: Hello world

(after second command is executed, return to the terminal instance w/ the server component)
$ ./server
2022/04/02 13:48:54 server listening at [::]:50051
2022/04/02 13:49:17 Received: world
```