# cli
go语言cli开发工具,使用非常简单,支持各种命令行开发,支持多种系统.

### 特点
这是一个修改自国外的作品的库,原作品很久没更新了,这里主要是修改一下更符合国内.去掉了一些不用的信息.
下面有两种情况一种是
cli add 1 这种命令用 c.Args()[0]获取的就是第一个参数 `1` 长度使用c.NArg()==0来判断是否有参数
cli all --qq=1 这种是设置名称获取c.GetString("qq")
原作品参考<https://github.com/subchen/go-cli>

### 使用示例
~~~
package main
import (
	"fmt"
	"github.com/logoove/cli"
	"strings"
	"os"
)
func main() {
app := cli.NewApp()
	app.Name = "cli"
	app.Version="1.0.0"
	app.Authors="Yoby\nWechat:logove"
	app.Description="程序描述"
	app.Usage="Golang版本管理工具"
	app.SeeAlso = "2021-"+strconv.Itoa(time.Now().Year())
	app.Commands = []*cli.Command{
		{
			Name:   "add",
			Usage:  "Add file contents to the index",
			Action: func(c *cli.Context) {
				fmt.Println("added files: ", strings.Join(c.Args(), ", "))
			},
		},
		{
			// alias name
			Name:   "a,all",
			Usage:  "Record changes to the repository",
			Flags:  []*cli.Flag {
				{
					Name: "qq,q",
					Usage: "commit message",
				},
			},
			Action: func(c *cli.Context) {
				fmt.Println(c.GetString("qq"))
			},
		},
	}
	app.Run(os.Args)
	}
~~~	

### 使用此构建作品
一个go版本管理器 <https://github.com/logoove/gv>
