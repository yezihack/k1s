
# 1. k1s: kubernetes 快捷操作的辅助工具

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

k1s 主要是用于 kubernetes 管理的命令行工具。

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
k1s resources <param> action
```

### Resources 列表

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
| 16  | deployments              | deploy    | 控制器资源              |
| 17  | replicasets              | rs        | 副本集合资源            |
| 18  | statefulsets             | sts       | 有状态控制器            |
| 19  | horizontalpodautoscalers | hpa       | Pod 水平自动扩缩器      |
| 20  | cronjobs                 | bj        | 定时任务器              |
| 21  | jobs                     | vj        | 一次性任务器            |
| 22  | ingresses                | ing       | 对外负载器              |
| 23  | ingressclasses           | ingc      | Ingress 分类器          |
| 24  | clusterrolebindings      | crb       | RBAC 集群角色绑定       |
| 25  | serviceaccounts          | sa        | RBAC 服务帐号           |
| 26  | clusterroles             | cr        | RBAC 集群角色           |
| 27  | rolebindings             | rb        | RBAC 角色绑定           |
| 28  | roles                    | ro        | RBAC 角色               |

### Action 列表

> 不同的动作(action), 对应不同资源类型,见表格详情