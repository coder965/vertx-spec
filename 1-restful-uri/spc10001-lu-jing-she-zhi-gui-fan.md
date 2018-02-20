# SPC10001 - 路径设置规范

鉴于路径参数本身的特殊性，书写相关路径规范，主要为Restful设计提供良好的参考，该路径规范主要涉及以下几点：

* Restful常用Api的固定命名规范
* 针对特殊场景的命名规范
* 解决路径参数容易混淆的问题。

路径本身应该具有自描述性、语义性、并且保证每个资源地址没有二义性。

## 1. 鉴权模式/开放模式

Api的顶级操作主要分为鉴权模式和开放模式两种，鉴权模式意味着提交请求必须提供身份令牌相关信息，一般的基础规范如下：

```shell
# 鉴权模式API
地址前缀：/api/*
支持的Http方法：*

# 开放模式API
地址前缀：/*
支持的Http方法：*
```

一般情况下，开放模式的API中包含了鉴权模式相关API，通过路径设计来区分不同模式下的基础Restful请求，鉴权模式的特殊API路径设计如：

```shell
# 鉴权：第三方开放型API
地址前缀：/open/*
支持的Http方法：*

# 鉴权：第三方系统集成专用API
地址前缀：/tp/{name}/*
支持的Http方法：*
```

整体API开放模式如下（所有条目都支持全部Http方法）：

| 路径前缀 | 模式 | 作用说明 |
| :--- | :--- | :--- |
| /\* | 开放模式 | 所有可公开资源的专用API，为整个系统的Restful超集。 |
| /api/\* | 鉴权模式 | UI前端专用API，一般为直接对接的内部系统专用Restful鉴权模式前缀。 |
| /open/\* | 鉴权模式 | 第三方应用App专用API，一般走OAuth通道，对接外部App的专用Restful前缀。 |
| /tp/{name}/\* | 鉴权模式 | 系统集成专用API，认证模式根据集成场景而定，{name}参数用于描述集成的第三方应用的名称，tp为third part缩写。 |

## 2. CRUD系列Api

CRUD主要用于描述常用的Api操作：`添加、删除、查询、修改、搜索、分页、排序`等，该系列Api根据模块名称不同提供不同的基础访问，主要解决路径参数的一些特殊问题。

> 以实体company为例，提供相关例子来描述不同的Api，模型名称为：company

### 2.1.路径参数冲突

路径参数冲突问题是常见问题，如下：

```shell
/api/crud/room/by/:type
/api/crud/room/by/:name
```

上述两个Api会出现：`Duplicated`模式，即当前端真正发送请求：`/api/crud/room/by/xxx`过后，后端和前端请求匹配上的路径信息会有两个路径信息，所以路径参数模式不可按照这种方式设计。

* 单数操作：company
* 复数操作：companies

### 2.2.CRUD专用API（写）

| 路径前缀 | Http方法 | 参数类型 | 该API说明 |
| :--- | :--- | :--- | :--- |
| /api/company | POST | JsonObject | 添加一个完整的company。 |
| /api/company/:id | PUT | Path, JsonObject | 更新一个company |
| /api/company/:id | DELETE | Path | 删除一个company |
| /api/companies | POST | JsonArray, E = JsonObject | 批量添加company |
| /api/companies | PUT | JsonArray, E = JsonObject | 批量更新company |
| /api/companies | DELETE | JsonArray, E = ID List | 批量删除company |

### 2.3.CRUD专用API（读）

| 路径前缀 | Http方法 | 参数类型 | 该Api说明 |
| :--- | :--- | :--- | :--- |
| /api/search/companies | POST（Post查询） | JsonObject：核心四参数sorter, criteria, projection, pager。 | 用于处理搜索company专用Api，该Api支持：分页、排序、返回过滤、条件查询，返回值格式：{list:\[\],count:0} |
| /api/existing/company | POST存在判断 | JsonObject：提供可解析的criteria格式字符串 | 判断当前company是否存在 |
| /api/companies | GET | 无 | 读取所有的company列表，不带任何条件 |
| /api/company/:id | GET | Path | 根据ID读取一个company |
| /api/company/:field/:value | GET | Path | 根据field=value查询唯一的company，单字段查询，返回为JsonObject |
| /api/companies/:field/:value | GET | Path | 根据company中的某个字段field读取该字段：field=value下的所有company，返回值为JsonArray，单字段查询 |

### 2.4.JsonObject返回API（读）





