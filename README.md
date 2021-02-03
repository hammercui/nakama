### 1 依赖安装
```
go mod tidy
```

```
go install \
    "github.com/golang/protobuf/protoc-gen-go" \
    "google.golang.org/grpc/cmd/protoc-gen-go-grpc" \
    "github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-grpc-gateway" \
    "github.com/grpc-ecosystem/grpc-gateway/v2/protoc-gen-openapiv2"
go get -u github.com/gobuffalo/packr/...
```

更新数据库文件
```
nakama.exe migrate up --database.address "go_admin:111111@192.168.3.22:26257/mahjong"
```

安装console所需依赖
>基于angular开发
```
npm install -g @angular/cli
cd console/ui
ng serve
```

### 2 启动服务
```
go run main.go --database.address "go_admin:111111@192.168.3.22:26257/mahjong"

```


### 3 编译二进制
```
go build -trimpath -mod=vendor
//查看版本
./nakama --version
```

### 4 docker 启动nakama

```
docker run --link=cockroachdb heroiclabs/nakama migrate up --database.address go_admin:111111@cockroachdb:26257/mahjong
docker run --link=cockroachdb --rm -p 7350:7350 -p 7351:7351 --name nakama heroiclabs/nakama --database.address go_admin:111111@cockroachdb:26257/mahjong
```
### 5 项目解析
#### 端口分配
* 7348：console模块grpc端口
* 7351：console模块http端口
* 7350：api模块http端口，
* 7349：api模块grpc端口
