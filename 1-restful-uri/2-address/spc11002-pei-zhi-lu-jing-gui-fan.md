# D11002 - 配置路径规范

配置路径规范为Zero专用的服务配置目录基本规范。

## 1. 服务名称

使用前缀法标识不同服务类型

* `rs-name`：Restful服务名称
* `ipc-name`：Rpc服务名称
* `sock-name`：WebSocket服务名称
* `api-name`：路由服务名（后期进入K8S后可删除）

## 2. Etcd配置路径说明

```shell
/zero                                    # Etcd对于Zero专用配置路径
    /{app1}                              # Etcd对于Application1专用配置路径
        /endpoint                        # Rs服务根路径
            /services                    # Rs服务状态
                {name}:{ip}:{port}       # Rs描述服务状态：RUNNING、STOPPED
            /routes                      # Rs服务路由
                {name}:{ip}:{port}       # Rs服务路由信息，每个值为JsonArray
        /ipc                             # Ipc服务根路径
            /services                    # Ipc服务状态
                {name}:{ip}:{port}       # Ipc描述服务状态：RUNNING、STOPPED
            /routes                      # Ipc服务路由
                {name}:{ip}:{port}       # Ipc服务路由信息，每个值为JsonArray
    /{app2}                              # Etcd对于Application2专用配置路径
        ......                            

```



