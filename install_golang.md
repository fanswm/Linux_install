## 安装go语言：

+ `sudo apt-get install golang`
+ `go version`

## 编译
+ `go build go_hello_world.go`

## 运行
+ `./go_hello_world`

## test:

```
package main
import  "fmt" //引入fmt库
func main() {
	fmt.Println("Hello World!")
}
```
+ `go build hello_go.go`
+ `./hello_go`
+ `go run ./hello_go.go`
