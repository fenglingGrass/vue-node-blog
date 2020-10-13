# Vue + Node + Mongodb 开发一个完整博客流程

## 本地开发:
server端: localhost:3000

后台管理: localhost:8090

web端: localhost:8080


## 脚本命令
mongod // 启动 mongod

npm run start // 启动 adminMongo 可视化程序界面

npm run server  // 启动服务

npm run dev:admin // 本地开发后台管理

npm run dev:client // 本地开发前台页面

npm run build:admin // 项目打包 - 后台管理

npm run build:client // 项目打包 - 前台

npm run analyz  // 查看打包信息



## 注意事项： 
  1. mongodb 注册用户
  
    ```
    db.createUser({
      user: "admin",
      pwd: "123456",
      roles: [{
        db: "blog",
        role: "readWrite"
      }]
    })
    ```
    
  2. server/config.js 文件内配置连接数据库的账号密码
  
    ```
    mongodb: {
      username: 'admin',
      pwd: 123456,
      db: 'blog',
      address: 'localhost:27017'
    }
    ```
    
  3. blog 数据库先创建一个 users 集合并初始化一个账号，用于登录博客管理后台
  
    ```
    db.users.insert({
      "username" : "admin",
      "pwd" : e10adc3949ba59abbe56e057f20f883e, // 这里是 md5('123456') 后的数据
      "name" : "admin",
      "roles" : [
        "admin"
      ]
    })
    // 账号：admin  密码：123456
    // 登录后可立即修改数据
    ```
    
  4. `cnpm run server` 启动服务器
  5. `cnpm run dev:admin` 启动后台管理界面
  6. `cnpm run dev:client` 启动前台页面
  7. 后台管理界面录入数据


## mongodb 安装问题

1. mac端sudo open -e〜/ .bash_profile权限被拒绝：

   解决：`sudo chown username ~/.bash_profile`
   
2. mac端mongodb启动报错：Data directory /data/db not found., terminating

   解决：更改指定运行路径，`mongod --dbpath '新的可访问路径'`


**参考文章**
> [个人博客](http://dzblog.cn/article/5a69609c3c04164b0bd4b964)

> [基于Koa2搭建Node.js实战项目教程](https://github.com/ikcamp/koa2-tutorial)

> [手摸手，带你用vue撸后台](https://segmentfault.com/a/1190000010043013)
