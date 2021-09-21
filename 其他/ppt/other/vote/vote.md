title: vote
author :
  name : 董珂
  email : dong.keke@tongbanjie.com
output: vote.html
encoding: utf-8
theme: sudodoki/reveal-cleaver-theme

--

# 投票系统vote鉴赏

--

### 目的 

1.学习开发一个应用时的思考方式   
2.学习即时应用的代码架构和组织方式  

--

### 目录：

* 需求
* 具体业务逻辑
* 技术实现

--

### 需求：

从一系列选项中选出最佳的选项。

--

### 具体业务逻辑：

设置一个具有N个选项的数组，每次拿出两项让用户进行投票，然后获取票数最多和票数相同的项重新放进数组里面进行再次投票，获取票数最低的直接丢弃。

--

### 技术实现：

架构  
具体实现  


--

### 架构：

  1.浏览器端：React------提供界面  

  2.服务器端：Node-------处理投票逻辑  

  3.浏览器端和服务器端之间的通信：采用WebSockets(具体使用socket.io库)。  

  4.代码的组织方式：采用redux来组织。 

--

### 具体实现：

  服务端  
  浏览器端  

--

### 服务端:

  1.写代码前的准备：   

    (1)考虑redux的状态树在整个应用状态变化期间的结构： 

      初始化：设置可供投票的选项。  
      投票：给每一项记录票数   
      切换到下轮投票：从数组中拿出两项用来投票，并从数组中删除两项。判断是否得到最佳选项，得到的话，则显示结果。否则，继续上面的流程。  

    (2)考虑整个项目的安排：
      项目初始文件：
      转码工具：
      测试：
      断言库：

--

  redux的状态树在整个应用状态变化期间的结构：   

    entries:[]
    vote:
      pair:[x1,x2]
      tally:{
        x1:0,
        x1:1
      }
    winner:""

--

  整个项目的安排（即需要的工具）：   

    package.json：    
    babel：  
    mocha：  
    chai、chai-immutable：  
    immutable：  

--

  2.不可变数据：  

    (1)定义:  
    (2)实现的原理:  
    (3)优缺点:  
    (4)流行的库:  

--

  (1)不可变数据的定义:    

    Immutable Data就是一旦创建，就不能再被更改的数据。
    对Immutable对象的任何修改或添加删除操作都会返回一个新的Immutable对象。

  (2)不可变数据实现的原理是:   

    Persistent Data Structure(持久化数据结构),也就是使用旧数据创建新数据时，要保证旧数据同时可用且不变。
    同时为了避免deepCopy把所有节点都复制一遍带来的性能损耗，Immutable使用了Structural Sharing（结构共享）
    即如果对象树中一个节点发生变化，只修改这个节点和受它影响的父节点，其它节点则进行共享。  

--
  <img src="./immutable.gif" alt="immutable" style="width:613px;"/>

--

  (3)Immutable优缺点:  

    优点：  
      1>Immutable 降低了 Mutable 带来的复杂度  
      2>节省内存  
      3>时间旅行这些功能做起来小菜一碟  
      4>并发安全  
      5>拥抱函数式编程  

    缺点：  
      1>需要学习新的 API  
      2>增加了资源文件大小  
      3>容易与原生对象混淆  
      4>侵入性强  
--

  (4)目前流行的 Immutable 库:  
    > immutable.js
    > seamless-immutable.js

--

  3.测试驱动开发：mocha、测试脚本、断言库.   


    mocha:  
      (1)用途：运行测试代码的工具  
      (2)支持：在浏览器和Node环境都可以使用。  
      (3)常用命令：  
         1>默认运行根目录下的test目录下的测试脚本  
         2>--recursive:  
         3>--reporter:  
         4>--growl:  
         5>--watch:  
         6>--bail:  
         7>--compilers: 

    测试脚本：  
      describe：测试套件  
      it：测试用例  
      测试脚本的命名：.spec.js、.test.js  
      断言库：chai  

    详情可参考：http://www.ruanyifeng.com/blog/2015/12/a-mocha-tutorial-of-examples.html
--

  4.实现核心应用逻辑：  

    (1)setEntries： 加载条目(用来提供应用的初始化状态)   

    (2)next：开始投票(在状态树创建中一个投票map，该map有拥有一个 pair 键，值为投票条目中的前两个元素，并从之前的条目列表中清除这两个元素).  

    (3)vote：投票(当用户产生投票行为后，每当用户给某个条目投了一票后， vote 将会为这个条目添加 tally 信息)

--

  5.引入redux中的reducer:
    
    作用：根据特定的action和当前state来调用指定的核心函数。 

    action：Action是一个描述应用状态变化发生的简单数据结构.  

--

  6.引入redux的store:

    作用：用来存储应用的状态，并派发action.   

    action的来源：用户操作、远程调用等。  

--

  7.配置Socket.io服务:

    开启一个websokte服务。

--
  存在的情况：

    (1)在store状态发生变化的时候把当前状态发送给链接的客户端。

    (2)有新客户端链接到服务端的时候把当前状态发送给链接的客户端。  

    (3)当接到客户端发来的action时，对客户端的action进行处理。  

--

### 浏览器端：

  1.准备工作：

    (1)需要的工具：除服务端需要的工具外，再额外添加处理jsx语法的配置和一个可以访问页面的服务  
    (2)写代码前考虑浏览器端的state结构  

--

  浏览器端的state结构

    entries:[]
    vote:
      pair:[x1,x2]
      tally:{
        x1:0,
        x1:1
      }
    winner:""
    hasVoted:

--

  需要展示的界面：

    voting : 
      vote:
      winner:
    result :
      vote :  

--

  2.技术实现：  

    (1)按照服务端同样的方式实现核心业务逻辑  
    (2)实现需要展示的页面  
    (3)使用react-router组织需要展示的页面  
    (4)引入react-redux将redux和react桥接起来 







  



