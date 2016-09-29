# WebConnectV5d1 （项目更名为：web_chats）

## 更新情况：持续开发中。。后台架构test用例搭建完毕，从持久层到业务层到api接口层的设计范式提交完毕。。

### 说明：
#### 整体来说，这个测试项目也可以作为一个Maven + Spring + SpringMVC + Mybatis的开发范例！
#### 在数据持久层采用mybatis配置开发的方式，由一个抽象类MybatisRepository类及其实现类DataRepository类组成，并且两个类通过Spring配置文件的方式注入IOC容器中。
#### 在Service层采用Spring配置开发方式，通过Spring配置文件配置beans依赖注入进行管理。Service所需的数据服务通过调用DataRepository类获取数据服务。
#### Controller接口层采用Spring注解开发方式，对外提供API接口，以JSON或者XML的格式提供数据给请求发起者。
## 主要完成任务：我的毕业设计代码重构尝试！
## （目前是测试版本，只设计了基本的开发示例，模块划分还在持续开发中。。）
### 空闲时更新，纯属个人爱好。
### 原型为我的毕业设计《基于Ajax异步请求的网页版实时通讯应用程序开发》
### 原设计基于SpringMVC+Mybatis+jQuery框架，采用Ajax技术和JSP编程
## 设计总说明（部分）
### 本设计重点利用Ajax完成核心功能的开发，Ajax是一种充分利用了现有的通信及计算机网络标准实现的客户端浏览器向服务器请求数据的交互式网页开发技术，可以达到不需要刷新整个页面就能够异步更新局部网页的效果[1]。编程语言使用Java语言，是基于B/S架构的网页实时聊天通讯应用。主要特点是对话信息及用户状态的无刷新实时显示，这使得用户能够迅速与其他在线用户进行对话交互。
本设计基于数据库表及相对应的功能来划分功能模块并进行模块化管理。主要功能包括有以下几大模块：
#### 登录注册模块：主要功能有响应用户登陆请求的用户名及密码校验、支持新用户的注册、支持用户的密码修改、已登陆用户的正常退出处理和部分相关的页面跳转功能。
#### 用户信息管理模块：该模块功能包括提供给用户一个展示个人资料的页面，同时包含修改个人资料的功能，其他用户也可以通过搜索找到希望查询到的用户的信息。
#### 用户状态信息模块：用户状态信息模块主要用于显示我的关注好友列表及实时显示输出在线用户列表。
#### 用户实时群聊功能模块：用户实时群聊功能是本设计的主要功能模块，能够让用户输入并发送消息，然后实时地显示在聊天对话框中，同时也可以实时地看到在线的用户。
#### 好友关系管理模块：好友关系管理模块主要用于让用户能够执行对用户的搜索并添加或取消关注操作。搜索功能直接显示在群聊天主界面中，而添加取消关注按钮，正如前面论述所说，将会出现在用户信息的下方。当你查看的用户不是登陆用户的关注好友的时候，将会显示添加关注按钮，否则将会显示取消关注按钮。本模块的好友关系是双向的，无需经过对方同意就可以添加关注，并且一方关注另一方的关注好友列表也将显示为已关注。
#### 用户实时私聊功能模块：用户实时私聊模块主要是为了满足部分用户与指定用户间单独的聊天对话需求开发的功能。私聊功能同样需要有无刷新实时显示的效果。为能够满足一般性的聊天对话功能，主要开发的功能有两个部分：发送消息，实时显示消息。
#### 管理员后台管理模块：管理员后台管理模块的主要作用是处理管理员的登录退出请求、处理用户发送的违规消息或者将违规用户的账号注销收回以及其他的相关管理操作。本设计中，需要的基本功能有管理员用户的登录和退出、清空用户发送违规消息、注销违规用户的账号。
本设计代码风格遵循Google Java编程开发者指南的规范，采用MVC分层结构的设计模式。