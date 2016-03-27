[TOC]

> 本文中用到的xdebug是2.2版本，phpstorm是2016.1的mac版本

#安装xdebug

默认情况下，我们的开发机是已经安装了xdebug的，如果没有安装，那么可以参考http://192.168.0.232:8090/pages/viewpage.action?pageId=1542198进行xdebug的安装。安装完毕之后，我们需要确认配置文件的信息，比如我的：

```
[Xdebug]
zend_extension = "/usr/local/php/lib/php/extensions/no-debug-non-zts-20100525/xdebug.so"
xdebug.remote_enable = 1
xdebug.remote_port = 9001
xdebug.remote_autostart = 1
xdebug.remote_host = localhost
```

我们需要牢记在我们的开发机上，xdebug监听的端口是**9001**

#建立SSH tunnel

在本地跑如下命令，当然更加建议你直接在phpstorm的terminal里面跑，更加方便

```shell
ssh -R 9001:localhost:9001 -p 10022 user_name@ip_addr
```

将user_name和ip_addr替换成对应的参数

#debug配置

##点击"小电话"

如图，点击该“小电话”图标，开启远程监听

![](http://7xrd8h.com1.z0.glb.clouddn.com/16-3-27/26321179.jpg)

##打一个断点

![](http://7xrd8h.com1.z0.glb.clouddn.com/16-3-27/96731869.jpg)

##验证配置

打开"Web Server Debug Validation"，如下图所示：

![](http://7xrd8h.com1.z0.glb.clouddn.com/16-3-27/69430019.jpg)

点击"Validate"，并且根据提示修改对应的配置。一般一开始配置的时候，我们都需要更改phpstorm默认的xdebug监听端口。比如我们在开发机上配置的是9001，那么我们也需要改为9001，如下图所示：

![](http://7xrd8h.com1.z0.glb.clouddn.com/16-3-27/64534519.jpg)

##使用phpstorm bookmarklets generator

打开[此页面](https://www.jetbrains.com/phpstorm/marklets/)，然后在Xdebug下面点击**GENERATE**，然后将*Start debugger*，*Stop debugger*，*Debug this page*都拖到书签中（chrome里面按住链接然后拖到书签一栏里面就行了）。然后打开我们的页面，比如*cjy.fangcloud.net*，然后点击一下在书签栏中的*Start debugger*，然后刷新页面

![](http://7xrd8h.com1.z0.glb.clouddn.com/16-3-27/97546506.jpg)

#开始debug

回到PhpStorm。当我们刚才刷新了页面之后，PhpStorm中会弹出一个窗口问我们有远程连接过来，需不需要监听，我们点击Accept之后，就可以开始debug了，如下图所示，有木有很激动！

![](http://7xrd8h.com1.z0.glb.clouddn.com/16-3-27/17024391.jpg)

#其他

- 如果有其它问题，可以尝试关闭防火墙试试
- 更多内容可参考https://confluence.jetbrains.com/display/PhpStorm/Remote+debugging+in+PhpStorm+via+SSH+tunnel#RemotedebugginginPhpStormviaSSHtunnel-1.XdebugorZendDebuggerinstalledandconfigured