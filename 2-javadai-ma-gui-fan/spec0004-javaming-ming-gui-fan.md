# SPEC0004 - Java命名规范

Java命名规范用语描述从最上层到下层的相关基本逻辑，以方便团队协同开发，包括每一层的方法名对应的业务信息都统一。

## 1. 类名基本规则

基本命名主要包含了类名的命名规则，以及在脚手架中应用的每一层的基本内容命名规则。

### 1.1. 常量包

常量定义位于`constant`子包中，变量名全部大写，且省略：`public static final`关键字（接口常量可省略），并且为了保证语义，在定义时尽可能用业务意义明确的常量，且两个单词之间用下划线连接。

```java
public interface Addr{
    /** 推送合同的消息地址 **/
    String MQ_CONTRACT_ADD_TOPIC = "TOPIC://CONTRACT_ADD";
}
```

### 1.2. 异常包

异常定义位于`exception`子包中，同一类异常可放在相同的子目录中，如果异常信息过多，则可以考虑按目录划分，如：

```shell
exception/
    web/
        _400RecordNotFoundException
    launcher/
        ConfigInvalidException
    app/
        FormatInvalidException
```

异常信息主要包含三大类，所有异常类名都以`Exception`结尾。

* **web异常**：单独命名规范，使用`_XXX`的前缀命名法，通过该名称可直接锁定这种异常需要返回到客户端的HTTP状态代码，且方便
* **launcher异常**：启动环境检查异常，如果出现这种异常则终止容器本身的启动，在后端记录详细日志以通知服务器为什么无法启动。
* **app异常**：平台中运行的app的启动异常，在启动过程通知该App无法正常启动的原因，对于app本身的接入，如果出现这种类型的异常则禁止app的接入。

> 以`User`的model名称为例，用来描述所有的代码文件信息

### 1.3. 微服务包

该命名规范为`service.{name}`中的类名基本规范，核心组件的命名规范如下：

[【表代号：TB0005】](/6-kuai-su-cha-xun-biao/tb0005-wei-fu-wu-biao.md)

| 名称 | Spring组件 | Java类型 | 命名说明 |
| :--- | :--- | :--- | :--- |
| UserController | @Controller | class | 用于定义Restful接口的Controller接口。一般放：添加、删除、修改，如果查询则只放“单数”以及少数查询。 |
| UsersController | @Controller | class | 【存在批量方法时】如果存在批量操作则开这个接口处理/users中的写操作接口，主要针对批量操作的情况。 |
| UserIrController | @Controller | class | 【接口方法过多时】将查询和读取接口从本身的Controller中分离出来，Ir为Inquiry的缩写，分离时业务逻辑接口不分离，即不会出现UserIrService一说，而这个控制器主要用于定义返回值为Users的情况。 |
| UserService | 无 | interface | 【单】业务逻辑接口 |
| UserServiceImpl | @Service | class | 用于描述业务层的服务组件 |
| UsersService | 无 | interface | 【多】业务逻辑接口 |
| UsersServiceImpl | @Service | class | 用于描述业务层的服务组件 |

### 1.4. 领域模型包

领域模型包一般不会自己去定义，使用Mybatis或Jooq都可自动生成全套领域模型需要使用的相关内容，那么此时的命名规则如下【如果是自动生成的情况则省略部分内容】：

[【表代号：TB0006】](/6-kuai-su-cha-xun-biao/tb0006-wei-fu-wu-biao-domain-bao.md)

| 包名 | 类名 | 职责 | 说明 |
| :--- | :--- | :--- | :--- |
| domain.user.model | UserDTO | 数据传输对象，DO/DTO |  |
| domain.user.model | UserVO | 视图对象，VO | 如果内容比较多则考虑将视图对象隔离出去。 |
| domain.user.model | UserBO | 业务规则对象，BO |  |
| domain.user.model | UserKey | 复合主键自定义组件 |  |
| domain.user.model | UserRoleRelation | 关联表对象，RO | 如果是Hibernate可省略，但对于存在多对多的关联表的情况，这种对象的有无根据具体场景来考虑。 |
| domain.user.dao | UserRepository, UserDao | 使用Spring时采用UserRepository，这种情况不需要实现 |  |
| domain.user.dao | UserDaoImpl | Dao层实现 |  |

## 2. 业务逻辑层扩展包（保留）

扩展包中包含了业务逻辑层比较复杂的情况的一些命名基本规范，如果是实现类则可以在后缀加入`Impl`来完成，包名可根据自己的意愿进行分类，如果不分默认放在：`domain.user.extension`中其内容如下：

| 类名 | 类型 | 说明 |
| :--- | :--- | :--- |
| UserScheduler | class | Java调度器 |
| UserSerializer | class | VO，DO转换器，若使用BeanCopier则省略，也可作为User和Json，XML数据格式之间的转换器 |
| UserResponser | class | 特殊响应格式处理器 |





