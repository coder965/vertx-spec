# SPC11001 - EventBus地址规范

该规范用于处理地址专用规范，地址主要涉及以下几个部分内容：

* EventBus地址——专用命名：`EVENT://ADDR`前缀
* Rpc地址——专用命名：`IPC://ADDR`前缀
* Mq消息队列——专用命名：`MQ://ADDR`前缀

本文主要介绍EventBus专用地址规范

## 1. Crud地址

基本地址规范使用：`METHOD + URI`的全大写模式，如：

```
URI: /o/authorize
Method: POST

对应的EventBus地址为：
EVENT://ADDR/POST/O/AUTHORIZE
```

## 2. 特殊地址

对于服务端的专用地址规范，则使用特殊前缀`EVENT://ADDR/OUT`，请求本身由服务端发送结果。

## 3. 代码基本命名

> 本示例以前端地址为例，结合Restful Uri规范处理



