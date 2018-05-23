> 一切皆是KEY

# 对象类型
- key-value
- List
- set
- zset
- hash

# 对象编码类型
- INT类型
- hashTable
- linkedlist
- intset
- skiplist
- sds
- zipmap
- ziplist

# 功能
- 初始化
- 事件循环
- 网络通信
- 定时任务
- 协议解析
- 命令执行
- 阻塞命令
- 主从复制
- lua支持
- 慢查询

# 模块划分
- 数据结构：dict,dictEntry,hashTable,zipList,adlist
- 协议解析: network redis协议的编解码实现
- 网络通信: aenet 封装不同同步差异
- 对象抽象：object ：将list,hash,keyvalue,set等统一抽象为redisObject
- 服务器大对象: redisServer,整个redis的上下文基本都在这里
- 定时任务：redisCron 清keys，广播,rehash,aof,复制

# redis协议
- 文本协议：紧凑
- 请求应答方式

# 整体内存布局
- redisServer
- redisDb 默认16个
- dict
- hashTable 2个，方便rehash
- dictEntry

# redisDb布局
- dict
- 过期的key集合
- 阻塞的key状态
- 就绪的key集合
- id
- ttl

# 数据流
- main 初始化
- aeMain 主调度
- aeProcessEvents 事件循环
- 处理IO事件
- 处理定时任务

# 初始化
-

# IO事件处理
- 连接事件处理：创建redisClient，初始化redisClient的各种资源
- 读事件处理
- 写事件处理

# 处理连接事件
- 创建redisClient
- 准备处理handler
- 准备readQueryFromClient

# 读事件处理
- read input buffer
- processCommand
- lookupCommand
- call
- cmd->process
- addReply

# 写事件处理
- addReply
- prepareClientToWrite
- createEvent
- 响应写事件
- 写buffer

# 优点
- 为了快，把commandlist放到hash表里面去了。  
- 通过lua,可以实现组合原子操作

# 问题
- 内存是如何布局的
- 如何存储不同的数据结构
- 事件模型
- 时间事件是如何搞的
- key失效是什么机制
- redis有哪些对象类型和编码类型

