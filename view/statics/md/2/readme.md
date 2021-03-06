# 第一次在 VPS 上建立 Web 服务器的经历

初始创建于：***2020/10/19***

最后编辑于：***2020/12/14***

## 折腾由来

刚进 SRE 运维安全部，就被要求自己做一个博客，幸好，条件几乎不限。虽然我之前高中时就用 Github Pages 做了个简单的网站，但是后端使用的是 Bmob 后端云 ~~（实际上只是个数据库而已）~~- ，自己实际上只写了前端部分，但是既然我现在也已经同时加入了 Web 开发部，正好可以自己重写一个后端，既练习了 Golang，又完成了运维部的作业，一举两得，岂不美哉？因此，我便开始了第一次的后端历程。

另外之所以选择用 Golang 而没有选择 WordPress 这类博客框架，还有一个原因是因为我个人不喜欢用这类稍微大型的框架，自己造的轮子虽然可能不咋地但好歹用着舒服，而且可定制化极高，不会有那种冗余的感觉。(注意 冗余 ≠ 臃肿) 

~~Gin 框架...用 Gin 造轮子不算用，造轮子的事，能叫用吗！~~

## 捣鼓经历

由于之前一直做前端，所以最常用的语言长期以来是 Javascript，比如红岩入校考试的算法题就是用 JS 写的。虽然也接触过 Python，nodeJS，但也只是大体了解了下语法而已（第一个Python爬虫还是上个月刚写的），所以我对后端服务器并没有多少了解。所以一开始我甚至看着 Golang 教程尝试用 tcp 搞一个服务器，结果写了一段时间后由于过于复杂最终放弃了 （老实说 tcp 是干啥的我现在还不清楚）。于是后来在学长的建议下转向了 Gin 。

一开始我尝试在慕课网上查找教程，好不容易找到一个，结果错误太多（章节顺序错乱缺失），而且讲解水平也比较一般，然后又尝试在B站上搜索，最终找到了 一个比较适合我这种新手的[教程](https://www.bilibili.com/video/BV1RJ411a7iL)，然后终于开始了正式写代码（bushi

在本地安装环境还算顺利，但是还是遇到了一个难题：
```go
r.POST("/login", func(c *gin.Context){
	account := c.PostForm("account")
	password := c.PostForm("password")
	if account == "" {
		c.String(200, "Invalid Account")
	} else {
		if account == "admin" {
			if password == "password" {
				c.String(200, "Login successfully.")
			} else {
				c.String(200, "Wrong password.")
			}
		} else {
			c.String(200, "Account does not exist.")
		}
	}
})
```
如上面的代码所示，当时我用的是传统的表单提交方式，所以导致每次服务器向客户端返回数据的时候都会导致页面重新加载，所以我就思考如何实现在网页不重新加载的情况下可以实现服务器向浏览器的数据传输。最终通过在群里提问，了解了 ajax ，虽然这个名词之前早已有所耳闻，但一直不知其为何物，于是当天晚上我一直在搜索关于 ajax 的资料，也看到了许多关于 websocket 未来是否会取代 ajax 的讨论，不过最终，综合各方因素（主要是 websocket 的实现好像比较困难），最终还是去学习了 ajax。我是在菜鸟教程上看的[教程](https://www.runoob.com/ajax/ajax-tutorial.html)，不过实在是没有预料到神秘的 ajax 居然远比我想象的要简单。接着我就用 ajax重构了一下登录部分。最后就差把它传到服务器上了。另外顺便在这儿贴一下前端的部分代码：

```javascript
let login = document.querySelector("div#login input")
let account, password
login.addEventListener('click',function(){
    account = document.querySelector("#account").value
    password = document.querySelector("#password").value
    let xml = new XMLHttpRequest()
    xml.onreadystatechange = function(){
        if(xml.readyState == 4 && xml.status == 200)
            alert(xml.response)
    }
    let url = '/loginRequest?account=' + account + '&password=' + password
    xml.open('POST', url, true)
    xml.send()
})
```

不过传到服务器上远比我想象的要困难。由于幸好一开始的代码量还不算多，并且也没有图片等资源，所以代码的话我是先暂时采取的复制粘贴的方式将其传到服务器上。但是当我尝试编译代码时发现 Go 的环境变量没有配置好；然后好不容易修改了 GOPATH ，结果又发现阿里云的服务器上不能连接到 Github 下载 Gin 框架；当我好不容易经过 baidu +  copy 的方式添加了代理，又折腾了半天才发现 Go 版本过旧，导致百度搜索到的添加代理方法是无效的；好不容易执行了`sudo apt update`和 `sudo apt upgrade`，结果才发现其实我原来已经是更新到了 debian （延长支持版）软件仓库的最新版本；~~好不容易更新了镜像源，发现并没有什么卵用；~~于是接下来根据群里大佬的建议尝试在官网上直接下载并安装，那么问题来了：
1. 如果我要安装 Go ，那么需要从本地上传安装包（Go 官网进不去，镜像的话尝试在[Goproxy 中国](https://goproxy.cn/)找过但没找到，也尝试过上传到网盘再下载但最终找不到直链）；
2. 如果我要上传安装包，那么需要先用 Go 写个代码用于上传（其他方法感觉有点复杂）；
3. 如果我要用 Go 写个上传数据的代码，那么需要用到 Gin 框架；
4. 如果我要安装 Gin 框架，需要设置代理；
5. 如果我要设置代理，需要更新 Go；
6. 如果我要更新 Go，需要上传安装包
导致陷入了一个死循环（悲

所幸最终终于找到了[下载镜像](https://studygolang.com/dl)打破了僵局。不过安装时又遇到一个问题，就是当我想卸载旧版本的 Go 时，执行`sudo apt uninstall golang`后输入`go version`发现 Go 并未被卸载，秉着多一事不如少一事的心态，我就直接重置了服务器，然后继续输入以下命令：
```bash
wget https://studygolang.com/dl/golang/go1.15.3.linux-amd64.tar.gz
tar -C /usr/local -xzf go1.15.3.linux-amd64.tar.gz
sudo vim /etc/profile
```
写入`export PATH=$PATH:/usr/local/go/bin`于最后一行，保存并退出，再接着输入：
```bash
source /etc/profile
go env -w GO111MODULE=on
go env -w GOPROXY=https://goproxy.cn,direct
go get github.com/gin-gonic/gin
cd ~/server
go mod init server
go run main.go
```
大功告成！
![效果图](1.gif)

## 胡扯笔记

[Go 下载](https://studygolang.com/dl) [Go 安装](https://golang.org/doc/install) [Go 代理](https://goproxy.cn/) [Gin 基础](https://www.bilibili.com/video/BV1RJ411a7iL)

##  混乱计划

- 赶紧用 Go 写个上传文件的功能，熟悉一下文件操作，方便文件上传操作
- 赶紧写个正经博客主页，就一登录页面还不能注册过于生草