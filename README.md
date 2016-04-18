### 部署 APP ###
----
首先在 heroku 绑定自己的GitHub</br>
fork 一下 https://github.com/Kisesy/Gogo 到自己 GitHub</br>

在 heroku 新建个app，建完之后在部署页面(deploy)有个 Deployment method，选成 Github</br>
然后在下面的 Connect to GitHub 右边的框里写上 "gogo"，点搜索，选上刚才 fork 的 Gogo</br>

在 settings 页有个 Buildpacks 点击 add Buildpack</br>
填上 https://github.com/heroku/heroku-buildpack-java</br>
回到部署页面，点最下面的 Deploy Branch 就行了</br>

> 这样就完成了 App 的部署

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
