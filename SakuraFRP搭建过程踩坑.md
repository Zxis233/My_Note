SakuraFRP搭建过程踩坑
==============================

几个人合资租了个服务器，忘了几C几G了，总体表现还行，打算整个FRP自己用用。找了一圈在线管理的面板，貌似只有[SakuraFRP](https://github.com/ZeroDream-CN/SakuraPanel)的还不错。使用配套的前端+特制的FRPs即可，FRPc可以任选。

操作系统是~~答辩11~~Debian11  
~~主人之前因为环境配烂了重装了三四次~~

准备
----------------------

先把该装的都装上，iptables、lsof、**nginx、mysql**啥的  
**后续安装时发现还需要其他依赖库，比如php--fpm、**

**SSL证书**也申请好（非必须，但是建议这么做）  
把库git clone一份到本地  

开始部署前端！ <(￣︶￣)↗ GO!
------------------------------

按着[SakuraFRP](https://github.com/ZeroDream-CN/SakuraPanel)的README放置网页文件  
这里因为没学过PHP犯了个错：把主页直接设为pages/home.php。应该设置为**index.php（路由）**

~~因为网站没备案所以~~NGINX监听非80端口，为了确保安全配置SSL证书。但是这样子每次登录主页都要https://xxxxxxxxx:xxxx/，~~非常难受~~

觉得带端口访问太丑？满足你！~~慈善家~~Cloudflare的Origin Rules可以用非公端口接入Cloudflare网络，懂了吧

开始部署后端！ ヾ(≧ ▽ ≦)ゝ
------------------------------

然后一路按着Wiki的教程部署。在configuration.php填写所需要的密钥、数据库地址啥的。

**这里建议数据库用户不要设为root，换一个，不然可能遇到各种各样奇怪的问题**

**貌似数据库初始端口无法连接，只能自己再开一个了 ~~不知道为啥~~**

下载配套的Frps服务端，按照Wiki填写配置文件，记录密钥。

我真傻，真的，我单知道frps内api密钥形式为xxxxxxxxx|n(n为节点编号，面板内新增)
却不知道api/configuration内不需要加节点编号，只要前面key就行了

邮箱问题自行解决，不会，有个懂哥整的

没啥好说的，注册账户，数据库里user的group字段改成admin，开造

The END ~ 
---------------------