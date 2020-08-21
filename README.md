# 本实例基于yoyogo v1.5.2
# 特色
- 漂亮又快速的路由器
- 中间件支持 (handler func & custom middleware)
- 微服务框架抽象了分层，在一个框架体系兼容各种server实现，如 rest,grpc等
- 受到许多出色的 Go Web 框架的启发，server可替换，目前实现了 fasthttp 和 net.http

[![](Resources/dingdingQR.jpg)](https://sourcerer.io/yoyofx)

# 框架安装
## go get
```bash
go get github.com/yoyofx/yoyogo
```
## go.mod
```
require github.com/yoyofx/yoyogo v1.5.2
```
# 安装依赖 (由于某些原因国内下载不了依赖)
##  go version < 1.13
```bash
window 下在 cmd 中执行：
set GO111MODULE=on
set  GOPROXY=https://goproxy.cn

linux  下执行：
export GO111MODULE=on
export GOPROXY=https://goproxy.cn
```
##  go version >= 1.13
```
go env -w GOPROXY=https://goproxy.cn,direct
```
### vendor
```
go mod vendor       // 将依赖包拷贝到项目目录中去
```
# 简单的例子
```golang
package main
import ...

func main() {
    YoyoGo.CreateDefaultBuilder(func(router Router.IRouterBuilder) {
        router.GET("/info",func (ctx *Context.HttpContext) {    // 支持Group方式
            ctx.JSON(200, Context.M{"info": "ok"})
        })
    }).Build().Run()       //默认端口号 :8080
}
```
![](https://mnur-prod-public.oss-cn-beijing.aliyuncs.com/0/tech/20200817181043.png)


