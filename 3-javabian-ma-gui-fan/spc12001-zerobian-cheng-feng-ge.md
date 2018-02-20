# SPC12001 - Zero编程专用规范

官方地址：[Programming Style](http://www.vertxup.cn/doc/vertx-zero-tutorial/d10044-programming-styles.html), [Interface Style](http://www.vertxup.cn/doc/vertx-zero-tutorial/d10044-recommend-interface-mode-only.html)

## 1. 基本法则

Zero编程中摒弃掉原始的`Controller, Service, Dao`的命名风格，直接使用新架构下的新命名风格，方便记忆、管理。

基本流程：

```shell
Api -> Actor -> ( Event Bus ) -> Worker -> Stub -> Service
```

接口风格流程：

```shell
Api -> ( Event Bus ) -> Worker -> Stub -> Service
```

省略Worker风格（仅用于基础无逻辑的CRUD，试验性阶段）

```shell
Api -> ( Event Bus ) -> Worker
```

### 1.1. 包结构

根包名遵循Java原始的domain法则，如项目：hotel的名称为`htl`，那么根包名使用：`com.htl`。

| 子包名 | 特殊类 | 用途说明 |
| :--- | :--- | :--- |
| com.htl.cv | Interface - Addr | 用于管理Event Bus地址接口常量 |
| com.htl.cv | 无 | 常量文件专用包 |
| com.htl.exception | 无 | 异常专用包 |
| com.htl.ipc | XXXJet | （Rpc Server）服务内部通讯专用包，ipc为Internal Rpc的简称，建议该包下的文件数量不宜太多。 |
| com.htl.domain | 无 | DTO专用包（如果使用Jooq、Hibernate、Mybatis则包含了Dao层类） |
| com.htl.micro.{name} | 无 | 微服务专用包 |

## 2. micro包中的类命名

| Java命名 | 类型 | 职责说明 | 运行线程 |
| :--- | :--- | :--- | :--- |
| XXIrApi | Interface | 查询专用Restful Api | Event Loop |
| XXApi | Interface | Crud专用Restful Api | Event Loop |
| XXIrActor | Class | 查询专用Actor | Event Loop |
| XXActor | Class | Crud专用Actor | Event Loop |
| XXWorker | Class | 查询/Crud专用Worker | Worker Pool |
| XXStub | Interface | 业务逻辑层接口 | Worker Pool |
| XXService | Class | 业务逻辑层实现类 | Worker Pool |

## 3. 方法名处理

### 3.1. Actor/Worker部分（Sender/Consumer）

实例中MODEL为`A`，可以是`USER, COMPANY, ROOM` 等，`AS`则表示A的复数形式

| Actor/Api方法名 | Addr地址变量 | Event Bus值名 | Worker方法名 |
| :--- | :--- | :--- | :--- |
| post | A\_POST | EVENT://ADDR/A/POST | post |
| get | A\_GET | EVENT://ADDR/A/GET | get |
| put | A\_PUT | EVENT://ADDR/A/PUT | put |
| delete | A\_DELETE | EVENT://ADDR/A/DELETE | delete |
| getAll | AS\_GET | EVENT://ADDR/AS/GET | getAll |
| batchPost | AS\_POST | EVENT://ADDR/AS/POST | batchPost |
| batchPut | AS\_PUT | EVENT://ADDR/AS/PUT | batchPut |
| batchDelete | AS\_DELETE | EVENT://ADDR/AS/DELETE | batchDelete |
| searchAdvanced | AS\_SEARCH\_ADVANCED | EVENT://ADDR/AS/SEARCH | searchAdvanced |
| search | AS\_SEARCH | EVENT://ADDR/AS/SEARCH/GET | search |
| existingAdvanced | A\_EXISTING\_ADVANCED | EVENT://ADDR/A/EXISTING | existingAdvanced |
| existing | A\_EXISTING | EVENT://ADDR/A/EXISTING/GET | existing |
| uniqueBy{Field} | A\_GET\_BY\_{FIELD} | EVENT://ADDR/A/GET/BY/{FIELD} | uniqueBy{Field} |
| listBy{Field} | AS\_GET\_BY\_{FIELD} | EVENT://ADDR/AS/GET/BY/{FIELD} | listBy{Field} |
| listIn{Field} | AS\_IN\_{FIELD} | EVENT://ADDR/AS/POST/IN/{FIELD} | listIn{Field} |
| listIn{Field}Raw | AS\_IN\_{FIELD}\_RAW | EVENT://ADDR/AS/POST/IN/{FIELD}/RAW | listIn{Field}Raw |
| listAnd | AS\_AND | EVENT://ADDR/AS/POST/AND | listAnd |
| listOr | AS\_OR | EVENT://ADDR/AS/POST/OR | listOr |
| uniqueAnd | A\_AND | EVENT://ADDR/A/POST/AND | uniqueAnd |

### 3.2. Stub/Service部分方法名

| Worker方法 | Stub/Service方法 | Stub/Service返回值 |
| :--- | :--- | :--- |
|  |  |  |





