### 依赖安装

```
go mod tidy
go mod vendor
```

```
go install \
    "github.com/golang/protobuf/protoc-gen-go" \
    "google.golang.org/grpc/cmd/protoc-gen-go-grpc" \
    "github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-grpc-gateway" \
    "github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-openapiv2"
go get -u github.com/gobuffalo/packr/...
```

### 编译二进制
```
go build -trimpath -mod=vendor
//查看版本
./nakama --version
```

更新数据库文件
```
nakama.exe migrate up --database.address "go_admin:111111@192.168.3.22:26257/mahjong"
```