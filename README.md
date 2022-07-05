[![k1s](https://img.shields.io/badge/kubernetes-k1s-green?style=flat-square&logo=appveyor)](https://github.com/yezihack/k1s)
[![GitHub license](https://img.shields.io/github/license/yezihack/k1s?style=flat-square&logo=appveyor)](https://github.com/yezihack/k1s/blob/master/LICENSE)

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
k1s action <param01> <param02>
```

### 1.3.1. ☆ 部署

- 开始部署  (apply)
- 重新部署  (reapply)

### 1.3.2. ☀ 列表

- 查看 node 列表              ( node|nodes|n|ns)
- 查看 node 标签              ( label|labels|l|ls)
- 查看 deploy 列表           (deploy|deploys|dep|deps|d )
- 查看 pod 列表                (pod|pods|p|po|ps  [监听(w)|yaml(yml|y)])
- 查看 service 列表           (svc|svcs|s|ss )
- 查看 endpoints 列表      (ep|eps )
- 查看 daemonsets 列表   (ds|dss )
- 查看 statefulSet 列表     (sts)
- 查看 ingress) 资源列表    (ingress|ing [监听(w)、详情(desc)、yaml(yml|y)])
- 查看 pv 资源列表            (pv) *
- 查看 pvc 资源列表          (pvc) *
- 查看 all                          (all )

### 1.3.3. ✍ 详情

- 查看 node 详情         (desc-node|desc-nodes|dn|dns )
- 查看 deploy 详情       (desc-deploy|dd|dds )
- 查看 pod 详情     (desc-pod|dp|dps )
- 查看 endpoints 详情    (desc-ep|de|des )
- 查看 daemonsets 详情   (desc-ds|desc-dds )
- 查看 statefulSet 详情  (desc-sts )
- 查看 ingress 资源详情 (desc-ing）*

### 1.3.4. ♬ YAML

- 查看 pod YAML          (yaml-pod|yp )
- 查看 deploy YAML       (yaml-deploy|yd )
- 查看 service YAML      (yaml-svc|ys )
- 导出 deploy YAML       (ex-deploy|ed )
- 导出 service YAML      (ex-svc|es )

### 1.3.5. ☯ Pod

- 进入 pod 容器               (exec )
- 自动进入 pod 容器      (auto)
- 查看 pod 日志          (logs|log)
- 监听 pod 日志         (logsf|logf)

### 1.3.6. ✈ 删除

- 删除 pod 资源          (rm-pod|rmp)
- 删除 deploy 应用       (rm-deploy|rmd)
- 删除 service 应用           (rm-svc|rms )
- 删除 statefulSet 应用       （rm-sts|rmss)
- 删除 daemonSet 应用    (rm-ds|rmds)*
- 清理垃圾                    (clean|c {空间名称})

### 1.3.7. ❤ 帮助

- 查看 top 资源负载 (top) *
- 查看帮助  (help|h)

## 1.4. 使用方法

K1S脚本直接在计算机上运行。它具有以下命令行界面：

```sh
k1s [操作类型] [资源名称]
```

或设置环境变量，获得更多操作方式：

```sh
export K1S_NS=[空间名称]
# 设置路径时使用下划线结束 (/)
export K1S_PATH=[操作路径] 

k1s [操作类型] [资源名称]
```

- 操作类型 是必选
- 资源名称 是可选

### 1.4.1. 使用实例

假设需要部署的应用名称: nginx-test.yaml  

tip: apply, reapply 要求应用名称与文件名同名，方便操作识别。

- 设置环境变量

```sh
# 设置环境变量,路径必须以斜杆(/)结尾
export K1S_PATH=/home/sgfoot/
export K1S_NS=dev
```

- 部署 YAML 应用

```sh
k1s apply nginx-test
```

- 重新部署 YAML 应用

```sh
k1s apply nginx-test
```

- 查看 deploy 应用资源列表

```sh
# 查看所有的
k1s apply

# 查看单个资源
k1s apply nginx-test
```

- 查看 pod 资源列表

```sh
# 查看所有的
k1s pod

# 查看单个资源
k1s pod nginx-test
```

- 自动进入 POD 容器

```sh
# 只需要填写 deploy 资源名称，脚本自动查找 pod 的列表，默认选择第一个。
k1s auto-pod nginx-test
```

- 导出 deploy YAML 资源

如果设置 K1S_PATH 则保证在指定目录，如果没有设置则保存在当前目录。

```sh
# 导出当前操作空间下的所有 deploy 资源，每个资源一个YAML文件
k1s ex-deploy 

# 导出单个资源的 yaml
k1s ex-deploy nginx-test
```

- 清理垃圾

目前支持清理 UnexpectedAdmissionError 错误垃圾。

```sh
# 查看不同空间下统计的错误信息
k1s clean 

# 清理指定空间下的错误信息
k1s clean dev
```