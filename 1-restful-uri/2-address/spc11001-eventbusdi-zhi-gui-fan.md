# SPC11001 - 地址规范

该规范用于处理地址专用规范，地址主要涉及以下几个部分内容：

* EventBus地址——专用命名：`EVENT://ADDR`前缀
* Rpc地址——专用命名：`IPC://ADDR`前缀
* Mq消息队列——专用命名：`MQ://ADDR`前缀

本文主要介绍所有

## 1. Crud地址转换

基本地址规范使用：`URI + METHOD`的全大写模式，如：

```
URI: /company
Method: POST

对应的EventBus地址为：
EVENT://ADDR/COMPANY/POST
```

## 2. 特殊地址

对于服务端的专用地址规范，则使用特殊前缀`EVENT://ADDR/OUT`，请求本身由服务端发送结果。

## 3. 代码基本命名参考

> 本示例以前端地址为例，结合Restful Uri规范处理，模型名称同样使用company

| URL（Http方法名） | Java方法名 | Addr地址值 |
| :--- | :--- | :--- |
| /api/company（POST） | post | EVENT://ADDR/COMPANY/POST |
| /api/company/:id（GET） | get | EVENT://ADDR/GET/COMPANY |
| /api/company/:id（PUT） | put | EVENT://ADDR/PUT/COMPANY |
| /api/company/:id（DELETE） | delete | EVENT://ADDR/DELETE/COMPANY |
| /api/companies（GET） | getAll | EVENT://ADDR/GET/COMPANIES |
| /api/companies（POST） | batchPost | EVENT://ADDR/POST/COMPANIES |
| /api/companies（PUT） | batchPut | EVENT://ADDR/PUT/COMPANIES |
| /api/companies（DELETE） | batchDelete | EVENT://ADDR/DELETE/COMPANIES |
| /api/search/companies（POST） | searchAdvanced | EVENT://ADDR/SEARCH/COMPANIES |
| /api/search/companies（GET） | search | EVENT://ADDR/SEARCH/COMPANIES/GET |
| /api/existing/company（POST） | existingAdvanced | EVENT://ADDR/EXISTING/COMPANY |
| /api/existing/company（GET） | existing | EVENT://ADDR/EXISTING/COMPANY/GET |
| /api/company/:field/:value（GET） | uniqueByField | EVENT://ADDR/GET/COMPANY/BY/{FIELD} |
| /api/companies/:field/:value（GET） | listByField | EVENT://ADDR/GET/COMPANIES/BY/{FIELD} |
| /api/in/companies/:field | listInField | EVENT://ADDR/POST/COMPANIES/IN/{FIELD} |
| /api/in/companies/:field/raw | listInFieldRaw | EVENT://ADDR/POST/COMPANIES/IN/{FIELD}/RAW |
| /api/and/companies | listAnd | EVENT://ADDR/POST/COMPANIES/AND |
| /api/or/companies | listOr | EVENT://ADDR/POST/COMPANIES/OR |
| /api/and/company | uniqueAnd | EVENT://ADDR/POST/COMPANY/AND |

## 4. Summary

以上是目前版本中需要使用到的各种基本命名规范

