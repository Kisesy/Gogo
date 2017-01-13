[GoGo官网][1] [Gitter聊天室][2] 大家可以到这里来讨论

----

### 部署 APP ###
----
首先在 heroku 绑定自己的GitHub</br>
fork 一下 https://github.com/Kisesy/Gogo 到自己 GitHub</br>

在 heroku 新建个app，建完之后在部署页面(deploy)有个 Deployment method，选成 Github</br>
然后在下面的 Connect to GitHub 右边的框里写上 "gogo"，点搜索，选上刚才 fork 的 Gogo</br>

在 settings 页有个 Buildpacks 点击 add Buildpack</br>
填上 https://github.com/heroku/heroku-buildpack-java</br>
回到部署页面，点最下面的 `Deploy Branch` 就行了</br>

> 这样就完成了 App 的部署

傻瓜版部署图

![snipaste20170113_103931](https://cloud.githubusercontent.com/assets/5843694/21916621/ca341f58-d97c-11e6-8df3-980856201ee6.png)

打开 GoGo 里 config 文件夹下的 gogo.conf，把部署的 app 按下面这样写
```json
	  "version" : "1.6.0",
	  "proxyOnlyForForeignIPs" : "true",
	  "apps" : [{
		"app" : "创建App的名字", <==== 关键
		"platform" : "heroku"
	  }, {
		"app" : "freetunnel0",
		"platform" : "heroku"
	  }, {
		"app" : "freetunnel1",
		"platform" : "heroku"
	  }
```
重载gogo，打开 http://127.0.0.1:9092/apps 就能看到效果了


### 更新 APP ###
----
很简单，以后 GoGo 更新了服务端，大家只要把服务端改名为 `gogo-server.jar` </br>
然后把服务端文件拖放到自己的 Github Gogo 项目中，上传，提交 </br>
再到 heroku 的 APP 的部署页面最下面点 `Deploy Branch` 按钮，即可更新部署完成

或者点部署页面里的 `Enable automatic deploys` 按钮，这样以后只更新 Github 里的文件即可自动部署

如果不想自己更新，想要跟我的同步，也可以这么做：通过pull request拉取更新
参考知乎 https://www.zhihu.com/question/20393785/answer/30725725


### 部署失败？ ###
----
如果部署完成后打开app的地址，发现 `Application Error`，可以到 app 的 `Overview` 页查看这里是否是 **OFF** 状态

![sp20161011_113357](https://cloud.githubusercontent.com/assets/5843694/19257917/211b0fa0-8fa6-11e6-96d2-e379e0792de5.png)

如果是 OFF 状态，可以到箭头所指的页面，把里面的开关按钮，掰到右边</br>
如果切换为ON还是有问题，或者有其他错误，可以到 `Gitter聊天室` 问一下

  [1]: http://www.gogotunnel.com/ "GoGo 官网"
  [2]: https://gitter.im/gogotunnel/gogo "Gitter聊天室"