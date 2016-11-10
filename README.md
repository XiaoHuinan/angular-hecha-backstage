###Angular+Bootstrap项目：和茶网后台管理系统(www.takozhang.cn)）

### 项目构建： ###
项目由angular+bootstrap搭建，主要使用的是angular,bootstrap,angular-ui-router。

###项目环境
由于项目中使用到了ajax，切忌直接打开文件，请先开一个服务，再跑代码。项目的API接口使用的node+express+mongodb，如果想开发API，可先看我的另一篇[开发后台接口的文章](https://github.com/dushao103500/angular-project-api)

###项目功能
**1. 账号登录**
	
只有管理员身份才能登录，所以偷偷透露一个账号:dushao,密码是103500
![](http://oe51jhwvd.bkt.clouddn.com/angular-login.png)

**2. 动态列表**

信息列表是动态数据，同时也具有隐入和淡出的功能，如图：![](http://oe51jhwvd.bkt.clouddn.com/angular-list.png)

**3. 商品信息管理**

商品信息管理主要是增删改查，增加商品是会弹出添加页面完成添加功能，如图：![](http://oe51jhwvd.bkt.clouddn.com/angular-add.png),删除功能主要是对选中的商品进行删除操作，支持全选，如图：
![](http://oe51jhwvd.bkt.clouddn.com/angular-delete.png)，商品查找功能主要是通过输入框输入关键字进行查找，同时商品信息会即使同步，如图：![](http://oe51jhwvd.bkt.clouddn.com/angular-search.png)，商品修改功能通过点击编辑按钮，弹出当前点击商品的信息，然后进行修改，如图：![](http://oe51jhwvd.bkt.clouddn.com/angular-modify.png)

**4. 用户信息管理**
用户信息管理基本同商品信息管理相同，就不详细介绍，直接上图：![](http://oe51jhwvd.bkt.clouddn.com/angular-user.png)

####项目在很短时间内赶出来，略显粗糙，代码看起来非常冗余无结构，但思路还是比较清晰，希望大家多多担待。
