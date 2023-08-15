# CHANGELOG

## 2.2.0

- 新增：nsenter 功能，实现进入 node 宿主机，方便调试。

## 2.1.4

- rm 实现：--force --grace-period=0 ok
- 查看上一次的日志：p, 显示出来。
- K1S_PATH 使用当前操作的目录
- 删除 Evicted 的 pod

## 2.1.3

- 修复 k1s help 提示

## 2.1.2

- 修复 apply 判断版本异常 BUG

## 2.1.1

- 添加 all 查看所有应用

## 2.1.0

- 添加编辑 YAML 功能
- 使用方式: `k1s po xx edit`

## 2.0.2

- 修改说明：apply 兼容 部署与重装

## 2.0.1

- 修复 apply 添加查看代码差异。
- 支持 `k1s d [名称] wide`。
- 去掉：`is_ns` 参数。

## 2.0.0

- 新版本发布 2.0.0
  