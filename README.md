# Micro Service微服务代码规范

## 版本历史

| 版本号 | 作者 | 修订时间 | 备注 |
| :--- | :--- | :--- | :--- |
| 0.1 | Lang | 2018.02.22 | 草稿 |

### 基本原则和约束

* 约束一：在查找文件过程遵循基本字典序法则，使得文件检索对开发人员变得简易。
* 约束二：使用统一的业务命名法则来限定业务逻辑层的动词，主要牵涉到CRUD操作以及最终的查询操作。
* 约束三：对于整个平台的路径，统一使用路径命名规范限定资源部分的路径访问。
* 约束四：对于容错系统，统一制定容错机制，以遵循系统容错基本法则。
* 约束五：引用防御式编程法则，用于处理不同情况的异常、错误以及日志机制。

### 文档说明

* 草稿：当前文档为作者首次修订版本，暂不投入到使用。
* 实验版本：当前文档为基本版本，投入到开发过程试运行（试运行不引入所有开发人员）。
* 正式版：可发布给所有人使用的版本。

### 文档前缀说明

* SPEC：代码规范开发规约专用文档
* KM：知识库专用文档
* ENV：环境说明文档
* TP：第三方接口文档
* BUS：业务规范文档
* TB：快速查询表，用于快速查询规范信息

## 0. 环境说明文档

## 1. Restful路径规范

* [SPEC0001 - Restful基础URI规范](/1-restfullu-jing-gui-fan-shuo-ming/11-ji-chu-uri-gui-fan.md)
* [SPEC0002 - Restful业务URI规范](/1-restfullu-jing-gui-fan-shuo-ming/spec0002-restfulye-wu-dui-xiang-gui-fan.md)

## 2. Java代码规范

* [SPEC0003 - Java包结构](/2-javadai-ma-gui-fan/spec0003-javabao-jie-gou.md)
* [SPEC0004 - Java命名规范](/2-javadai-ma-gui-fan/spec0004-javaming-ming-gui-fan.md)
* [SPEC0005 - 业务术语规范](/2-javadai-ma-gui-fan/spec0005-ye-wu-zhu-yu-gui-fan.md)

## 3. 配置规范

## 4. 数据库SQL规范

## 5. 工程构建规范

## 6. 快速查询表

* [TB0001 - URI分类表](/6-kuai-su-cha-xun-biao/tb0001-urifen-lei-biao.md)
* [TB0002 - Http状态含义对照表](/6-kuai-su-cha-xun-biao/tb0002-httpzhuang-tai-han-yi-dui-zhao-biao.md)
* [TB0003 - Restful业务URI对照表](/6-kuai-su-cha-xun-biao/tb0003-restfulye-wu-uri-dui-zhao-biao.md)
* [TB0004 - 包结构表](/6-kuai-su-cha-xun-biao/tb0004-bao-jie-gou-biao.md)
* [TB0005 - 微服务表service包](/6-kuai-su-cha-xun-biao/tb0005-wei-fu-wu-biao.md)
* [TB0006 - 微服务表domain包](/6-kuai-su-cha-xun-biao/tb0006-wei-fu-wu-biao-domain-bao.md)



