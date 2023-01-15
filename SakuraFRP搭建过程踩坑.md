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

开始部署！ <(￣︶￣)↗ GO!
------------------------------

按着[SakuraFRP](https://github.com/ZeroDream-CN/SakuraPanel)的README放置网页文件  
这里因为没学过PHP犯了个错：把主页直接设为pages/home.php。应该设置为**index.php（路由）**
