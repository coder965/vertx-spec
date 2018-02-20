# SPC10002 - 鉴权专用路径规范

本章节主要用于描述Restful Api在处理认证、授权模式下的专用命名Api规范。

## 1. 认证API

> 认证API一般为开放式API，即位于`/*` 之下的核心API，在发送认证请求时不需要提供Authorization认证头。

### 1.1. 普通认证

| 路径前缀 | Http方法 | 参数类型 | API说明 |
| :--- | :--- | :--- | :--- |
| /login | POST | JsonObject | 登陆专用API |
| /code | GET | 无 | 验证码专用API，以Stream流的模式输出，可构造成验证码图片。 |



