

#  webKettleETL产品介绍
-------------------------    
   

-  精卫ETL平台，创造性的将平台构建为B/S架构的ETL模型设计以及集成用户专业调度管理的分布式ETL建模运维系统。
-  系统分为七大模块:模型、平台、任务、定时调度、日志、节点、用户.
-  模型模块进行ETL模型开发，在B/S系统中用拖拽的方式设计数据流逻辑。
-  其他六个模块为用户专业调度管理系统,更多是面向业务运维人员，关注于整个流程的执行情况和数据的导入导出细节信息,以及对任务的综合调度。完全支持集群和单机两种运行模式。并通过用户权限的管控让平台的资源分配变得更加专业。

# 模块展示
--------------------------
-  **平台** 

展示平台概况

![输入图片说明](https://git.oschina.net/uploads/images/2017/0608/145540_063bca4f_1097305.png)
-  **模型设计**

进行ETL模型设计调试

![输入图片说明](https://git.oschina.net/uploads/images/2017/0607/161330_3d1a33bc_1097305.png)
-  **任务管理**

对ETL任务进行综合的调度管理以及监控
![输入图片说明](https://git.oschina.net/uploads/images/2017/0613/142406_c1d1f25c_1097305.png)
![输入图片说明](https://git.oschina.net/uploads/images/2017/0613/114021_0c347905_1097305.png)
-  **日志**

ETL任务的执行日志模块
![输入图片说明](https://git.oschina.net/uploads/images/2017/0613/114003_eb22068b_1097305.png)
-  **节点管理**

ETL任务的执行引擎节点管理
![输入图片说明](https://git.oschina.net/uploads/images/2017/0613/113944_7213e6c1_1097305.png)
-  **定时调度**

定时ETL任务管理
![输入图片说明](https://git.oschina.net/uploads/images/2017/0613/144118_a5e252e8_1097305.png)
-  **用户管理**

精卫平台的用户权限管理系统
![输入图片说明](https://git.oschina.net/uploads/images/2017/0613/141826_599b8f09_1097305.png)

#  webKettleETL技术实现
------------------------- 
- 精卫ETL是基于流行的ETL工具kettle开发的B/S架构版本的ETL产品,所使用的底层引擎是调用kettle的api
- ETL任务以元数据的方式储存在资源库里面,精卫通过读取资源库元数据,对元数据进行解析后可将ETL任务通过MXGraph展现至B/S架构的精卫系统中,实现了在B/S架构上面开发ETL任务的功能,属于精卫系统的模型开发模块功能.
- 通过对元数据的操作可以对ETL任务进行综合性的管理以及监控,通过Quartz定时框架可以实现对任务的定时调度
- 根据kettle执行引擎可以部署多台服务器节点的特性,再通过精卫系统跟远程的节点发送HTTP请求,可以实现在多节点上分布式的执行ETL任务,并可以实现实时监控ETL的任务运行情况
- 基于高度自由化的B/S框架,可以嵌入多元化的需求,于是我们在精卫中添加了用户管理模块,通过用户权限的概念对所有的ETL任务进行人性化的运维管理
- 整个项目使用Maven进行构建管理,多模块之间低耦合,高拓展性

![输入图片说明](https://git.oschina.net/uploads/images/2017/0613/110502_61484bf4_1097305.png)


# webKettleETL整体功能流程
--------------------------
![输入图片说明](https://git.oschina.net/uploads/images/2017/0613/110741_c24e49f7_1097305.png)
![输入图片说明](https://git.oschina.net/uploads/images/2017/0825/094017_0fbeada5_1097305.png)
# 技术选型
--------------------------

- 核心框架：Spring Framework 
- 任务调度：Spring + Quartz
- 持久层框架：MyBatis 
- 会话管理：Spring-Session 
- 日志管理：Log4j
- 前端框架：EXTJS3.4+MXGraph2.3
- 项目管理: Maven3.2.3
- ETL底层引擎:kettle7.0

# 说明
--------------------------
1. 本系统采用单资源库模式，数据源连接在dispatch-servlet.xml中配置，系统启动后就会读取该资源库
2. 数据库脚本都在kettle-scheduler项目的scripts目录下
3. 数据库暂时只支持MySQL，本系统在MySQL5.5.20版本上测试，其他版本尚未测试
4. 本例使用Maven3.2.3构建，启动服务器后访问http://localhost:8080/
5. 支持IE9及以上、FireFox等浏览器，IE6-IE8需要做特殊化处理，其他浏览器未测试
6. jdk版本需要1.8以上



# 许可证
    Apache2
