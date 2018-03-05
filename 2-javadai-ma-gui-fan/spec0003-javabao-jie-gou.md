# SPEC0003 - Java包结构

| 版本 | 作者 | 修订时间 | 备注 |
| :--- | :--- | :--- | :--- |
| 0.1 | Lang | 2018.02.22 | 草稿 |

## 1. 基本设计

和Java语言一样，如公司为：`www.kingxunlian.com`的地址，则顶级包使用`com.kingxunlian`为前缀，包的基本规范主要包含以下几种项目类型：

* **Platform**：平台本身的包，以模块为中心，并且可通过Maven的pom.xml设置相关依赖，不包含业务。
* **Internal**：内部App专用，以服务为中心，不通过Maven的pom.xml设依赖，包含内部主流业务。
* **External**：（推荐规范）外部App专用，同Internal类型的规范，只是拥有更加特殊的外部App独有的业务。

> 不同类型的项目在不同的Project中，并不在一个项目中

该包中的子包结构如下。

[【表代号：TB0004】](/6-kuai-su-cha-xun-biao/tb0004-bao-jie-gou-biao.md)

| 子包名 | 该包项目类型 | 包说明 |
| :--- | :--- | :--- |
| constant | Internal | 常量文件包。 |
| exception | Internal | 当前Service使用的异常，异常本身从抽象异常中继承。 |
| domain.model | Internal | DTO的POJO专用包【可生成】 |
| domain.dao | Internal | DAO层专用包【可生成】 |
| micro.{service} | Internal | 这里{service}是服务名称，一个项目中可能包含多个{service}，这里的service不表示“微服务”概念，粒度比它更细，可定义为：微服务中针对某个实体的业务逻辑层。 |
| ipc | Internal | 内部“微服务”相互通讯专用包，用于写内部服务通讯组件。 |
| tp | Internal | 第三方集成专用，后期这部分可转移到平台内部，只在此处调用TpClient模式来完成第三方接口的访问。 |
| constant | Platform | 平台常量包 |
| exception | Platform | 平台专用异常信息（一般为抽象异常） |
| infix.{plugin} | Platform | 平台插件包，用于管理平台中的插件信息，插件可根第三方开源项目走。 |
| fn | Platform | 预留，用于处理代码流程的函数式模型，以Fn作为主类开放。 |
| tool | Platform | 抽象工具类Util作为主类，用于处理通用的工具方法，可统一从此包内的信息访问第三方。 |

## 2. 书写原则

* 常量包中的常量文件尽可能使用接口常量代替类常量，并禁用“接口常量模式”引用常量，只通过接口名称在代码中引用。
* 每一个service目录下的信息为不带包结构的信息，即service目录下只包含Controller/Service两种组件。
* Spring中的Repository放到domain包中去，充当了dao层，domain和dao合并的目的是domain和dao这两层可自动生成，比较模式化，且dao层不遇到特殊业务不会大力度修改。



