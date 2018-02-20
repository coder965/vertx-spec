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
    /{app1}                              # Etcd对于Application专用配置路径
        /endpoint                        # Restful服务根路径
            /services                    # 服务状态
                {name}:{ip}:{port}       # 描述服务状态：RUNNING、STOPPED
            /routes                      # 服务路由
                {name}:{ip}:{port}       # 服务路由信息，每个值为JsonArray
        /ipc                             # Ipc服务根路径
    /{app2}
```



