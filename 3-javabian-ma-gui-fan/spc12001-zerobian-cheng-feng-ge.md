# SPC12001 - Zero编程专用规范

官方地址：[Programming Style](http://www.vertxup.cn/doc/vertx-zero-tutorial/d10044-programming-styles.html), [Interface Style](http://www.vertxup.cn/doc/vertx-zero-tutorial/d10044-recommend-interface-mode-only.html)

### 1. 基本法则

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

## 2. Zero中的角色和职责

| Java命名 | 类型 | 职责说明 | 运行线程 |
| :--- | :--- | :--- | :--- |
| XXIrApi | Interface | 查询专用Restful Api | Event Loop |
| XXApi | Interface | Crud专用Restful Api | Event Loop |



