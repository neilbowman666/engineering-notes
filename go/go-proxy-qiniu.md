# 设置代理加速国内源

## Go 1.13 及以上（推荐）

打开你的终端并执行

```bash
go env -w GO111MODULE=on
go env -w GOPROXY=https://goproxy.cn,direct
```

完成。

## macOS 或 Linux

打开你的终端并执行

```bash
export GO111MODULE=on
export GOPROXY=https://goproxy.cn
```

或者

```bash
echo "export GO111MODULE=on" >> ~/.profile
echo "export GOPROXY=https://goproxy.cn" >> ~/.profile
source ~/.profile
```

完成。

## Windows

打开你的 PowerShell 并执行

```powershell
C:\> $env:GO111MODULE = "on"
C:\> $env:GOPROXY = "https://goproxy.cn"
```

或者

1. 打开“开始”并搜索“env”
2. 选择“编辑系统环境变量”
3. 点击“环境变量…”按钮
4. 在“<你的用户名> 的用户变量”章节下（上半部分）
5. 点击“新建…”按钮
6. 选择“变量名”输入框并输入“GO111MODULE”
7. 选择“变量值”输入框并输入“on”
8. 点击“确定”按钮
9. 点击“新建…”按钮
10. 选择“变量名”输入框并输入“GOPROXY”
11. 选择“变量值”输入框并输入“https://goproxy.cn”
12. 点击“确定”按钮

完成。

## 自托管 Go 模块代理
你的代码永远只属于你自己，因此我们向你提供目前世界上最炫酷的自托管 Go 模块代理搭建方案。通过使用 Goproxy 这个极简主义项目，你可以在现有的任意 Web 服务中轻松地引入 Go 模块代理支持，要知道 Goproxy.cn 就是基于它搭建的。

创建一个名为 goproxy.go 的文件
```golang
package main

import (
	"net/http"
	"os"

	"github.com/goproxy/goproxy"
)

func main() {
	http.ListenAndServe("localhost:8080", &goproxy.Goproxy{
		GoBinEnv: append(
			os.Environ(),
			"GOPROXY=https://goproxy.cn,direct", // 使用 Goproxy.cn 作为上游代理
			"GOPRIVATE=git.example.com",         // 解决私有模块的拉取问题（比如可以配置成公司内部的代码源）
		),
		ProxiedSUMDBs: []string{
			"sum.golang.org https://goproxy.cn/sumdb/sum.golang.org", // 代理默认的校验和数据库
		},
	})
}
```
并且运行它

```bash
go run goproxy.go
```

然后通过把 GOPROXY 设置为 http://localhost:8080 来试用它。另外，我们也建议你把 GO111MODULE 设置为 on。

就这么简单，一个功能完备的 Go 模块代理就搭建成功了。事实上，你还可以将 [Goproxy](https://github.com/goproxy/goproxy) 结合着你钟爱的 Web 框架一起使用，比如 [Gin](https://pkg.go.dev/github.com/gin-gonic/gin#WrapH) 和 [Echo](https://pkg.go.dev/github.com/labstack/echo/v4#WrapHandler)，你所需要做的只是多添加一条路由而已。更高级的用法请查看[文档](https://pkg.go.dev/github.com/goproxy/goproxy)。