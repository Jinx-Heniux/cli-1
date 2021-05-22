# cli
go语言cli开发工具,使用非常简单,支持各种命令行开发,支持多种系统.

### 使用示例
~~~
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
~~~	
