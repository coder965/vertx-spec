| 子包名 | 该包项目类型 | 包说明 |
| :--- | :--- | :--- |
| constant | Internal | 常量文件包。 |
| exception | Internal | 当前Service使用的异常，异常本身从抽象异常中继承。 |
| domain.model | Internal | DTO的POJO专用包【可生成】 |
| domain.view | Internal | VO的POJO专用包 |
| domain.dao | Internal | DAO层专用包【可生成】 |
| micro.{service} | Internal | 这里{service}是服务名称，一个项目中可能包含多个{service}，这里的service不表示“微服务”概念，粒度比它更细，可定义为：微服务中针对某个实体的业务逻辑层。 |
| ipc | Internal | 内部“微服务”相互通讯专用包，用于写内部服务通讯组件。 |
| tp | Internal | 第三方集成专用，后期这部分可转移到平台内部，只在此处调用TpClient模式来完成第三方接口的访问。 |
| constant | Platform | 平台常量包 |
| exception | Platform | 平台专用异常信息（一般为抽象异常） |
| infix.{plugin} | Platform | 平台插件包，用于管理平台中的插件信息，插件可根第三方开源项目走。 |
| fn | Platform | 预留，用于处理代码流程的函数式模型，以Fn作为主类开放。 |
| tool | Platform | 抽象工具类Util作为主类，用于处理通用的工具方法，可统一从此包内的信息访问第三方。 |



