---
icon: iconfont icon-api
order: 62
category:
  - Guide
tag:
  - Storage
  - Guide
  - 123 Open
sticky: true
star: true
author: 千石(okatu-loli)
---

# 123 Open（开放平台）

`123 Open` 是 123云盘推出的开放平台接口，可通过密钥鉴权的方式在 Alist 中实现挂载访问。

支持文件浏览、上传、预览、下载、管理等功能，并由 Alist 自动维护 token 生命周期。

::::: tabs#123 Open

@tab 获取刷新Token

## 获取刷新Token

调用 123Pan 官方第三方授权应用，自动刷新 Token，无需申请个人开发者。

---

@tab 接入说明

## 接入说明

要通过 `123 Open` 将 123云盘资源挂载到 Alist，请先完成以下准备工作：

### 开通条件

- 已注册并登录 123云盘账户
- 已在 [123云盘开放平台](https://www.123pan.com/developer) 创建应用，获取：
  - **Client ID**
  - **Client Key**
- （可选）开通「VIP」服务，以启用直链等高级功能

::: warning 注意事项
挂载过程中，Alist 将使用 `Client ID` 和 `Client Key` 自动获取访问凭证（Token），并在后台自动维护，无需用户干预。

该过程仅在本地进行，不涉及任何外部中转，因此**不存在隐私泄露风险**。  
但请务必妥善保管你的 `Client ID` 和 `Client Key`，避免泄露。
:::

---

@tab 直链设置

## 设置直链空间（用于预览/下载）

::: danger 请务必完成以下设置
未启用「直链空间」将导致 Alist 无法生成直链或预览链接。
:::

### 1. 开启直链空间

进入 [123云盘](https://www.123pan.com/)，按以下步骤操作：

1. 找到目标文件夹，点击右键
2. 点击 **启用直链空间**
3. 启用后该目录会显示直链图标 🔗

![直链空间](/img/drivers/123/open/123_link.png)

### 2. 获取 Folder ID

1. 进入该文件夹
2. 浏览器地址栏中，URL 的末尾即为 Folder ID
3. 在 Alist 中填写此 ID 作为挂载目录

---

@tab 功能支持

## 功能支持说明

以下为 `123 Open` 驱动当前支持的功能：

### ✅ 支持功能

- 📁 **浏览文件/文件夹**
- 📥 **下载 / 预览（需开启直链）**
- 📤 **上传文件（支持秒传、分片）**
- 🗂️ **新建文件夹**
- ✏️ **重命名**
- 🗃️ **移动文件/文件夹**
- 🗑️ **删除**
- 🔐 **token 自动获取与刷新**

::: tip 上传说明
如上传的文件未提供完整哈希，Alist 会自动缓存后计算 MD5 值。
:::

### ⚠️ 不支持功能

::: warning 当前暂不支持以下功能：

- ❌ 文件/文件夹复制
- ❌ 在线压缩、解压
- ❌ 打包下载  
  :::

::: danger 根目录限制

虽然可以将根目录（ID 为 0）作为挂载目录，但**无法在根目录使用直链功能**（如预览、视频播放、图片查看等）。

建议将挂载目录设置为已**开启直链空间的子文件夹**。
:::

---

:::::

## 默认使用的下载方式

```mermaid
---
title: 默认使用的下载方式
---
flowchart TB
    style a1 fill:#bbf,stroke:#f66,stroke-width:2px,color:#fff
    style a2 fill:#ff7575,stroke:#333,stroke-width:4px
    subgraph ide1 [ ]
    a1
    end
    a1[302]:::someclass====|默认|a2[用户设备]
    classDef someclass fill:#f96
    c1[本机代理]-.备选.->a2[用户设备]
    b1[代理URL]-.备选.->a2[用户设备]
    click a1 "../drivers/common.html#webdav-策略"
    click b1 "../drivers/common.html#webdav-策略"
    click c1 "../drivers/common.html#webdav-策略"
