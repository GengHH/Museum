#在linux中部署ghost(开源博客)
## 需求 ##

  - 1.node.js环境
  - 2.ghost自己改变的项目
  
### 安装nvm来管理node.js
  
  - curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash
  
   or Wget:

  - wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.32.1/install.sh | bash
  
### 列出所需要的版本
      nvm list-remote
###  返回结果如下
              ...
              v0.10.4
              ...
              v0.12.0
              v0.12.1
              v0.12.2
              v0.12.3
              v0.12.4
              ...
               v4.2.0
               v4.2.1
               v4.2.2
               v4.2.3
               v4.2.4
               v4.2.5
               v4.2.6
              v5.10.1
              v5.11.0
               v6.0.0
###    安装相应的版本
      nvm install v4.2.6
###    查看已安装的版本
      nvm list
      ->    v4.2.6
            system
###   切换版本
      nvm use v0.10.30
###   设置默认版本
      nvm alias default v0.10.30
      
      
      
  - 5使用forever守护进程

   + 1.使用npm安装forever
   
     npm install forever -g
     
   + 2.使用forever启动ghost
     NODE_ENV=production forever start index.js

     *NODE_ENV=production的意思是使用生产环境。*

   + 3.若想要关闭ghost可以使用
   
     forever stop index.js

**这样就可以启动完ghost去干别的事了。不过一般服务器不会向外暴露80以外的端口。我们可以使用nginx反向代理将80端口的请求转发到2368上。**


