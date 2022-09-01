# 1. k1s: kubectl 辅助工具

```text
     __    ____        
|  | _/_   | ______
|  |/ /|   |/  ___/
|    < |   |\___ \ 
|__|_ \|___/____  >
     \/         \/  by 百里(github.com/yezihack)
```

![](asset/k1s.gif)

## 1.1. 什么是k1s

k1s 主要是用于 kubernetes 管理的命令行工具。对 kubectl 命令实现快捷操作。

## 1.2. 安装

直接下载脚本，仅依赖 kubectl。

```sh
wget https://raw.githubusercontent.com/yezihack/k1s/master/k1s
chmod +x k1s
mv k1s /usr/local/bin
```

## 1.3. 功能

命令格式：

```sh
#  环境变量
k1s resources <param> action <extend>
```

### 1.3.1. Resources 列表(扩展功能)

| No  | Name    | Describe     |
| --- | ------- | ------------ |
| 1   | apply   | 开始部署 or 重新部署     |
| 2   | clean   | 清理无用 Pod |

### 1.3.2. Resources 列表(系统对应)

> 资源(Resources) 列表详情, 与 api-resources 显示一致,未全列出,只列出常用的资源名称.

| No  | Name                     | ShortName | Describe                |
| --- | ------------------------ | --------- | ----------------------- |
| 1   | componentstatuses        | cs        | k8s 组件健康状态        |
| 2   | configmaps               | cm        | 配置管理资源            |
| 3   | endpoints                | ep        | 端点                    |
| 4   | events                   | ev        | 事件                    |
| 5   | limitranges              | limits    | 为pod自定义资源管理限制 |
| 6   | namespaces               | ns        | 命名空间                |
| 7   | nodes                    | no        | 节点资源                |
| 8   | persistentvolumeclaims   | pvc       | 声明持久卷              |
| 9   | persistentvolumes        | pv        | 持久卷                  |
| 10  | pods                     | po        | k8s 管理最小单元        |
| 11  | replicationcontrollers   | rc        | 副本控制器              |
| 12  | resourcequotas           | quota     | 硬性资源限额            |
| 13  | secrets                  | sec       | 机密数据配置资源        |
| 14  | services                 | svc       | 服务负载资源            |
| 15  | daemonsets               | ds        | 守护进程资源            |
| 16  | deployments              | deploy,d    | 控制器资源              |
| 17  | replicasets              | rs        | 副本集合资源            |
| 18  | statefulsets             | sts       | 有状态控制器            |
| 19  | horizontalpodautoscalers | hpa       | Pod 水平自动扩缩器      |
| 20  | cronjobs                 | bj        | 定时任务器              |
| 21  | jobs                     | job        | 一次性任务器            |
| 22  | ingresses                | ing       | 对外负载器              |
| 23  | ingressclasses           | ingc      | Ingress 分类器          |
| 24  | clusterrolebindings      | crb       | RBAC 集群角色绑定       |
| 25  | serviceaccounts          | sa        | RBAC 服务帐号           |
| 26  | clusterroles             | cr        | RBAC 集群角色           |
| 27  | rolebindings             | rb        | RBAC 角色绑定           |
| 28  | roles                    | ro        | RBAC 角色               |

### 1.3.3. Action 列表

> 不同的动作(action), 对应不同资源类型,见表格详情

| No  | Name     | ShortName | Describe         | ENV                |
| --- | -------- | --------- | ---------------- | ------------------ |
| 1   | list     | ls        | 显示列表(默认显示)        |
| 2   | describe | desc      | 查看详情         |
| 3   | yaml     | y         | 查看 YAML        |
| 5   | exec     | e,auto         | 进入容器操作     |
| 6   | delete   | del       | 删除资源操作     |
| 7   | logs     | log       | 查看日志操作     |
| 8   | tail     | tail      | 查看 Pod 最近日  | K1S_TAIL 环境设置  |
| 9   | tailf    | tailf     | 监听日志变化     |
| 10  | since    | since     | 查看多少久的日志 | K1S_SINCE 环境设置 |

### Extend 扩展功能

| No  | Name           | ShortName | Describe         |
| --- | -------------- | --------- | ---------------- |
| 1   | wide     | w         | 查看更多信息     |
| 2   | container-name | -         | 选择不同容器名称 |

### 1.3.4. 环境变量

| No  | Name      | Default | Describe                             |
| --- | --------- | ------- | ------------------------------------ |
| 1   | K1S_NS    | default | 命名空间名称                         |
| 2   | K1S_PATH  | ~       | 构建目录，默认本用户目录下           |
| 3   | K1S_TAIL  | 50      | 设置日志显示最近条数，默认最近 50 条 |
| 4   | K1S_SINCE | 5m      | 最新时间内的日志，默认 5 分钟内      |

## 1.4. 使用说明

> 举例说明，只列举常用资源

### 资源查看

- 查看 pods 资源列表
  
```sh
# 简约列表
k1s po
# 详细列表
k1s po w
```

- 查看 nodes 资源列表

```sh
# 简约列表
k1s no
# 详细列表
k1s no w
```

- 查看 deamonsets 资源列表

```sh
k1s ds
```

### 1.4.1. 设置环境变量

```sh
# 设置命名空间名称
export K1S_NS=default

# 设置构建路径,以斜杆结尾 /
export K1S_PATH=/home/dev/

# 设置日志显示最近条数
export K1S_TAIL=100

# 设置日志最新时间内的日志,支持使用 5s, 2m, or 3h
export K1S_SINCE=30m
```
