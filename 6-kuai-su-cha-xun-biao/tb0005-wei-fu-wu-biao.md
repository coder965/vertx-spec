| 名称 | Spring组件 | Java类型 | 命名说明 |
| :--- | :--- | :--- | :--- |
| UserController | @Controller | class | 用于定义Restful接口的Controller接口。一般放：添加、删除、修改，如果查询则只放“单数”以及少数查询。 |
| UsersController | @Controller | class | 【存在批量方法时】如果存在批量操作则开这个接口处理/users中的写操作接口，主要针对批量操作的情况。 |
| UserIrController | @Controller | class | 【接口方法过多时】将查询和读取接口从本身的Controller中分离出来，Ir为Inquiry的缩写，分离时业务逻辑接口不分离，即不会出现UserIrService一说，而这个控制器主要用于定义返回值为Users的情况。 |
| UserService | 无 | interface | 【单】业务逻辑接口 |
| UserServiceImpl | @Service | class | 用于描述业务层的服务组件 |
| UsersService | 无 | interface | 【多】业务逻辑接口 |
| UsersServiceImpl | @Service | class | 用于描述业务层的服务组件 |

### 



