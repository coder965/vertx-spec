# SPC10002 - 鉴权专用路径规范

本章节主要用于描述Restful Api在处理认证、授权模式下的专用命名Api规范。

## 1. 安全API

> 认证API一般为开放式API，即位于`/*` 之下的核心API，在发送认证请求时不需要提供Authorization认证头，鉴权认证部分则一般位于/api/\*之下，请求时必须加上Authorization认证头。

### 1.1. 开放认证部分

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

### 1.2. 鉴权认证部分

| 路径前缀 | Http方法 | 参数类型 | API说明 |
| :--- | :--- | :--- | :--- |
| /api/profile | GET | Path | 读取当前登录账号的API信息，用户账号在Authorization中提供Token身份令牌处理 |



