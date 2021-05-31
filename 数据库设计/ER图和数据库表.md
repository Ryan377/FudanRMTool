# ER图和数据库表

## 概述

本项目采用关系数据库进行数据库设计，数据库设计满足第三范式。



## ER图

![数据库ER图](https://gitee.com/freemansonary/markdown-pic-bed/raw/master/Typora/20210529222745.png)



## 数据库表说明

用户表User：

记录一个用户的基本信息

| 字段名       | 解释         | 类型        | 备注 |
| ------------ | ------------ | ----------- | ---- |
| UserID       | 用户编号     | varchar(20) | 主键 |
| UserName     | 用户名称     | varchar(20) |      |
| UserPwd      | 用户密码     | varchar(20) |      |
| LastSignTime | 最后登陆时间 | datetime    |      |

角色表Role：

使用权限的基本单位，拥有一定数量的权限，通过角色赋予用户权限

| 字段名   | 解释         | 类型        | 备注 |
| -------- | ------------ | ----------- | ---- |
| RoleID   | 角色编号     | varchar(20) | 主键 |
| RoleName | 角色名称     | varchar(20) |      |
| RoleNote | 角色信息描述 | varchar(20) |      |

用户-角色关系表UserRole：

一个用户可以有多种角色，一个角色可以有多个用户

| 字段名     | 解释         | 类型        | 备注 |
| ---------- | ------------ | ----------- | ---- |
| UserRoleID | 用户角色编号 | varchar(20) | 主键 |
| UserID     | 用户编号     | varchar(20) | 外键 |
| RoleID     | 角色编号     | varchar(20) | 外键 |

权限表Permission：

根据角色获得对程序某些功能的操作，例如文件的读写等

| 字段名         | 解释         | 类型        | 备注 |
| -------------- | ------------ | ----------- | ---- |
| PermissionID   | 权限编号     | varchar(20) | 主键 |
| PermissionName | 权限名称     | varchar(20) |      |
| PermissionNote | 权限信息描述 | varchar(20) |      |

角色·权限关系表RolePermission：

一个角色可以有多种权限，一个权限可以有多个角色

| 字段名           | 解释         | 类型        | 备注 |
| ---------------- | ------------ | ----------- | ---- |
| RolePermissionID | 角色权限编号 | varchar(20) | 主键 |
| RoleID           | 角色编号     | varchar(20) | 外键 |
| PermissionID     | 权限编号     | varchar(20) | 外键 |

项目表Project：

| 字段名      | 解释         | 类型        | 备注 |
| ----------- | ------------ | ----------- | ---- |
| ProjectID   | 项目编号     | varchar(20) | 主键 |
| UserID      | 创建者编号   | varchar(20) | 外键 |
| ProjectNote | 项目描述     | text        | 外键 |
| ProjectTime | 项目创建时间 | datetime    |      |

模块表Module：

| 字段名     | 解释         | 类型        | 备注 |
| ---------- | ------------ | ----------- | ---- |
| ModuleID   | 模块编号     | varchar(20) | 主键 |
| UserID     | 创建者编号   | varchar(20) | 外键 |
| ProjectID  | 项目编号     | varchar(20) | 外键 |
| ModuleNote | 模块描述     | text        |      |
| ModuleTime | 模块创建时间 | datetime    |      |

文档表Doc：

| 字段名   | 解释         | 类型        | 备注 |
| -------- | ------------ | ----------- | ---- |
| DocID    | 文档编号     | varchar(20) | 主键 |
| UserID   | 创建者编号   | varchar(20) | 外键 |
| ModuleID | 模块编号     | varchar(20) | 外键 |
| DocNote  | 文档描述     | text        |      |
| DocTime  | 文档创建时间 | datetime    |      |

评论表Comment：

评论是具体用户针对具体文档做出的评论

| 字段名      | 解释     | 类型        | 备注 |
| ----------- | -------- | ----------- | ---- |
| CommentID   | 评论编号 | varchar(20) | 主键 |
| DocID       | 文档编号 | varchar(20) | 外键 |
| UserID      | 用户编号 | varchar(20) | 外键 |
| CommentNote | 评论内容 | text        |      |
| CommentTime | 评论时间 | datetime    |      |

更改Change：

更改记录用户对文档的更改

| 字段名     | 解释     | 类型        | 备注 |
| ---------- | -------- | ----------- | ---- |
| ChangeID   | 更改编号 | varchar(20) | 主键 |
| DocID      | 文档编号 | varchar(20) | 外键 |
| UserID     | 用户编号 | varchar(20) | 外键 |
| ChangeTime | 更改时间 | datetime    |      |
| OldNote    | 原内容   | text        |      |
| NewNote    | 新内容   | text        |      |



## 数据库初始化示例

