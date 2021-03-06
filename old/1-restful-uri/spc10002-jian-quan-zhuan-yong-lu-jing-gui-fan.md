# SPC10002 - 鉴权专用路径规范

本章节主要用于描述Restful Api在处理认证、授权模式下的专用命名Api规范。

> 认证API一般为开放式API，即位于`/*` 之下的核心API，在发送认证请求时不需要提供Authorization认证头，鉴权认证部分则一般位于/api/\*之下，请求时必须加上Authorization认证头。

## 1.开放认证部分

| 路径前缀 | Http方法 | 参数类型 | API说明 |
| :--- | :--- | :--- | :--- |
| /login | POST | JsonObject | 登陆专用API |
| /verify/image | GET | Query参数（用户名） | 验证码专用API，以Stream流的模式输出，可构造成验证码图片。 |
| /verify/mobile | GET | Query参数（手机号） | 手机验证码专用API，发送手机验证码信息，在后端处理。 |
| /verify/email | GET | Query参数（Email） | Email邮箱专用API，发送Email验证链接，在后端处理。 |
| /registry | POST | JsonObject | 注册专用API |
| /forget | POST | JsonObject | 找回密码专用API |
| /o/authorize | POST | JsonObject | OAuth专用读取临时授权码接口 |
| /o/token | POST | JsonObject | OAuth专用使用授权码交换Token令牌接口 |
| /o/refresh | POST | JsonObject | OAuth专用刷新授权码交换刷新令牌专用接口 |

## 2. 鉴权认证部分

| 路径前缀 | Http方法 | 参数类型 | API说明 |
| :--- | :--- | :--- | :--- |
| /api/profile | GET | Path | 读取当前登录账号的API信息，用户账号在Authorization中提供Token身份令牌处理 |
| /api/profile | POST | JsonObject | 更新当前登录账号的API信息，用户账号在Authorization中提供Token身份令牌处理 |
| /api/password | POST | JsonObject | 更改当前登录账号密码专用API信息，用户账号在Authorization中提供Token身份令牌处理 |
| /api/reset | GET | 无 | 后端发送Reset重置密码连接专用地址 |
| /api/user/:id/lock | GET | Path | 锁账号（普通管理员） |
| /api/user/:id/active | GET | Path | 激活账号（系统自动） |
| /api/user/:id/unlock | GET | Path | 解锁账号（普通管理员） |
| /api/user/:id/disable | GET | Path | 禁用账号（超级管理员） |
| /api/user/:id/enable | GET | Path | 启用账号（超级管理员） |

## 3. Summary

该部分暂时以已存在的认证为主，缺少授权部分的相关Api规范。



