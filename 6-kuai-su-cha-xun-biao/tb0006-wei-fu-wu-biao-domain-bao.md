| 包名 | 类名 | 职责 | 说明 |
| :--- | :--- | :--- | :--- |
| domain.user.model | UserDTO | 数据传输对象，DO/DTO |  |
| domain.user.model | UserVO | 视图对象，VO | 如果内容比较多则考虑将视图对象隔离出去。 |
| domain.user.model | UserBO | 业务规则对象，BO |  |
| domain.user.model | UserKey | 复合主键自定义组件 |  |
| domain.user.model | UserRoleRelation | 关联表对象，RO | 如果是Hibernate可省略，但对于存在多对多的关联表的情况，这种对象的有无根据具体场景来考虑。 |
| domain.user.dao | UserRepository, UserDao | 使用Spring时采用UserRepository，这种情况不需要实现 |  |
| domain.user.dao | UserDaoImpl | Dao层实现 |  |



