# 🎮 赢合系小程序 - README 📱
**fufubuff with okiqiiii**  
📅 2024-10-10

---

## 📑 目录
- [📌 项目简介](#-项目简介)
- [🛠️ 功能介绍](#️-功能介绍)
- [💻 开发环境与配置](#-开发环境与配置)
  - [1. 环境准备](#1-环境准备)
    - [1.1 下载并安装微信开发者工具](#11-下载并安装微信开发者工具)
    - [1.2 开通微信云开发环境](#12-开通微信云开发环境)
    - [1.3 数据库集合创建](#13-数据库集合创建)
  - [2. 项目配置](#2-项目配置)
    - [2.1 配置项目 `app.js` 文件](#21-配置项目-appjs-文件)
- [📱 主要页面与结构](#-主要页面与结构)
  - [1. 隐私政策页面](#1-隐私政策页面)
  - [2. 登录页面](#2-登录页面)
  - [3. 注册页面](#3-注册页面)
  - [4. 广场页面](#4-广场页面)
  - [5. 个人主页页面](#5-个人主页页面)
  - [6. 私信功能页面](#6-私信功能页面)
  - [7. 简历投放与招募页面](#7-简历投放与招募页面)
  - [8. 编辑个人资料页面](#8-编辑个人资料页面)
  - [9. 头像选择页面](#9-头像选择页面)
  - [10. 评价页面](#10-评价页面)
  - [11. 好友页面](#11-好友页面)
  - [12. 聊天页面](#12-聊天页面)
- [🌐 全局数据管理](#-全局数据管理)
  - [1. `app.js` 中的全局变量](#1-appjs-中的全局变量)
  - [2. 全局数据在页面中的使用](#2-全局数据在页面中的使用)
- [🎨 界面优化](#-界面优化)
- [🚀 如何运行项目](#-如何运行项目)
- [🤝 贡献指南](#-贡献指南)
- [📄 许可证](#-许可证)

---

## 📌 项目简介

**赢合系小程序** 是一个基于腾讯云开发的跨校组队平台，旨在为大学生提供便捷的组队与项目合作功能。🎓🤝 通过本小程序，用户可以发布个人简历、查找项目、私信其他用户、发布组队需求、展示自我介绍，与其他用户交流并组队合作，从而促进跨校交流与资源共享。🌟

---

## 🛠️ 功能介绍

1. **隐私政策同意** 📜
   - 首次进入小程序时，用户需要同意隐私政策才能继续使用。
   
2. **登录与注册** 🔐
   - 用户可以通过注册登录，创建个人账户并管理个人资料。
   
3. **广场** 🏞️
   - 用户可以在广场页面浏览和发布简历、查看他人发布的招募信息与组队需求。
     - **浏览简历**：查看其他用户的详细简历，包括专业、技能和项目经验。
     - **发布简历**：上传和编辑自己的简历，展示个人能力。
     - **查看招募信息**：浏览他人发布的项目招募信息，寻找合作机会。
   
4. **私信功能** 💬
   - 用户之间可以通过私信进行一对一交流，讨论项目或合作事宜。
   
5. **简历投放与招募查看** 📄🔍
   - 用户可以查看他人的简历信息或项目招募详情，并投递个人简历。
   
6. **个人资料管理** 🧑‍💼
   - 用户可以更新个人资料，选择并更换个人头像。
   
7. **评价功能** ⭐
   - 用户可以对其他用户进行合作评价，记录合作反馈。
   
8. **好友管理** 👥
   - 查看和管理好友列表，方便联系其他用户。
   
9. **聊天功能** 🗨️
   - 与好友进行实时聊天，讨论项目合作。
   
10. **头像选择** 🖼️
    - 选择或更换个人头像，展示个性化形象。

---

## 💻 开发环境与配置

### 1. 环境准备

#### 1.1 下载并安装微信开发者工具
- 前往 [微信开发者工具](https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html) 下载适合您系统的版本。🖥️
- 安装完成后，使用微信账号登录。🔑

#### 1.2 开通微信云开发环境
- 在微信开发者工具中打开您的小程序项目。📂
- 点击工具顶部导航栏中的 **云开发** 按钮。☁️
- 点击 **开通云开发**，并根据提示新建一个云开发环境。将该环境的 ID 记录下来，稍后在项目中会使用到。📝

#### 1.3 数据库集合创建
在微信云开发控制台中，按照以下说明创建数据库集合：📚

- **users**: 存储用户信息。
  - **字段示例**：
    - `openid`: String, 用户的唯一标识符
    - `nickname`: String, 用户昵称
    - `avatarUrl`: String, 用户头像链接
    - `createdAt`: Date, 账户创建时间

- **resumes**: 存储用户简历信息。
  - **字段示例**：
    - `userId`: Reference, 关联到 `users` 集合
    - `intendedProjects`: Array, 用户意向项目
    - `major`: String, 专业
    - `skills`: Array, 技能列表
    - `contactInfo`: String, 联系方式
    - `createdAt`: Date, 简历创建时间

- **recruitmentPosts**: 存储招募信息。
  - **字段示例**：
    - `title`: String, 项目标题
    - `description`: String, 项目描述
    - `tags`: Array, 标签
    - `recruitDate`: Date, 招募日期
    - `creatorId`: Reference, 发布者的 `userId`
    - `createdAt`: Date, 招募信息创建时间

- **cooperationReviews**: 存储用户之间的合作评价信息。
  - **字段示例**：
    - `reviewerId`: Reference, 评价者的 `userId`
    - `revieweeId`: Reference, 被评价者的 `userId`
    - `rating`: Number, 评分（如1-5）
    - `comment`: String, 评价内容
    - `createdAt`: Date, 评价时间

### 2. 项目配置

#### 2.1 配置项目 `app.js` 文件
在项目根目录中找到 `app.js` 文件，配置云开发环境 ID：

```javascript
wx.cloud.init({
  env: 'your-cloud-environment-id', // 替换为您在云开发控制台创建的环境 ID
  traceUser: true,
});



## 📱 主要页面与结构

### 1. 隐私政策页面 - `pages/privacy/privacy`
- **功能**：该页面向用户展示隐私政策内容，并要求用户在使用小程序前同意隐私政策。📄
- **交互**：
  - 用户可以阅读隐私政策的详细内容。
  - 用户必须同意隐私政策才能继续使用小程序。

### 2. 登录页面 - `pages/dengru/newpage`
- **功能**：用户可以通过该页面登录到小程序，登录后可访问更多功能。🔑
- **交互**：
  - 用户输入账号和密码进行登录。
  - 如果登录成功，用户将被重定向到主页面。

### 3. 注册页面 - `pages/register/register`
- **功能**：新用户可以通过该页面进行注册，填写个人资料并创建账户。📝
- **交互**：
  - 用户填写昵称、选择头像并设置密码完成注册。

### 4. 广场页面 - `pages/square/square`
- **功能**：广场页面是小程序的主页面，用户可以在此浏览发布的简历和招募信息。🏞️
- **交互**：
  - 用户可以浏览简历和招募信息，点击查看详情。

### 5. 个人主页页面 - `pages/profile/profile`
- **功能**：展示其他用户的个人资料页面，查看用户的简历、合作评价等信息。👤
- **交互**：
  - 用户可以查看其他用户的详细信息。

### 6. 私信功能页面 - `pages/chat/chat`
- **功能**：用户可以通过该页面与其他用户进行一对一聊天，讨论项目合作。💬
- **交互**：
  - 用户可以发送和接收消息。

### 7. 简历投放与招募页面 - `pages/add/add`
- **功能**：用户可以通过该页面添加新的简历或招募信息。📄🔍
- **交互**：
  - 用户填写信息并提交。

### 8. 编辑个人资料页面 - `pages/editProfile/editProfile`
- **功能**：用户可以通过该页面编辑和更新个人资料，包括修改头像、昵称、个性签名等。🧑‍💼
- **交互**：
  - 用户提交修改后的资料，并更新到数据库。

### 9. 头像选择页面 - `pages/avatarSelect/avatarSelect`
- **功能**：用户可以通过该页面选择或更换个人头像。🖼️
- **交互**：
  - 用户选择一个预设头像，并更新到个人资料中。

### 10. 评价页面 - `pages/evaluation/evaluation`
- **功能**：用户可以在该页面对其他用户进行评价，记录合作反馈。⭐
- **交互**：
  - 用户为其他用户提供合作评价，包括评分和评价内容。

### 11. 好友页面 - `pages/friends/friends`
- **功能**：用户可以在该页面查看和管理好友列表，联系其他用户。👥
- **交互**：
  - 用户可以与好友进行私信交流。

### 12. 聊天页面 - `pages/chat/chat`
- **功能**：用户可以通过该页面与其他用户进行一对一聊天，讨论项目合作。🗨️
- **交互**：
  - 用户可以发送和接收消息。



## 🌐 全局数据管理

### 1. `app.js` 中的全局变量

项目中的全局数据通过 `app.js` 进行管理，主要包括以下几个全局变量：

- **user_openid** 🆔
  - **描述**：存储当前用户的 `openid`，`openid` 是每个用户在微信生态中的唯一标识符，用于区分不同用户。
  - **用途**：用于执行数据库相关操作，例如根据 `openid` 查询用户信息、简历、招募信息等。
  - **获取方式**：通过 `wx.getStorageSync('user_openid')` 从本地存储获取用户 `openid`，并存储在全局变量中。

- **userInfo** 🧑‍💼
  - **描述**：存储当前用户的基本信息，如昵称、头像等。`userInfo` 在用户注册或登录成功后被获取并保存。
  - **用途**：用户的个人信息会展示在个人主页及相关页面中，另外用户头像、昵称等信息会用于发布简历或参与项目时展示。
  - **设置方式**：通过调用云数据库获取用户信息后，存储在 `userInfo` 中，并缓存到本地。

- **hasAgreedPrivacyPolicy** 📜✅
  - **描述**：标记用户是否已同意隐私政策。
  - **用途**：控制用户是否可以继续使用小程序。在用户首次使用小程序时，要求用户同意隐私政策。如果未同意，则无法访问主页面。
  - **设置方式**：当用户同意隐私政策后，调用 `wx.setStorageSync` 将状态保存到本地，并在 `app.js` 中的全局变量中更新状态。

### 2. 全局数据在页面中的使用

在页面中通过 `getApp()` 获取全局数据，`user_openid` 和 `userInfo` 主要用于：

- 获取用户的个人信息并展示在个人主页。
- 通过 `openid` 执行数据库查询，获取用户的简历、项目招募信息等。




## 🎨 界面优化

目前小程序的界面以chiikawa三个宝宝为主要元素，以提升视觉吸引力和用户体验。🎨✨ 以下是一些优化方向：

- **颜色主题** 🌈
  - 使用粉色蓝色我最喜欢的颜色和最喜欢的三个宝宝，符合年轻用户群体的喜好。
  
- **图标设计** 🖌️
  - 采用卡通化的图标，增加趣味性。
  
- **动画效果** 🎞️
  - 添加适当的动画效果，有点击效果！提升交互体验。



---
    
## 🚀 如何运行项目

在项目审核通过后，目前提交了很多版本都被腾讯打回，会努力，但是已经邀请了很多我的亲朋好友测试，欢迎联系我通过微信 **H3149374548** 申请成为测试人员。📲 测试名额有限，先到先得。如果有助教老师希望参与测试，也欢迎联系。我们非常期待您的反馈，以优化小程序界面并添加卡通风格元素，提升用户体验。😊

---
    
## 🤝 贡献指南

欢迎任何形式的贡献！🤗 请按照以下步骤进行：

1. **Fork 本仓库**。🔀
2. **创建您的功能分支** (`git checkout -b feature/新功能`)。🌱
3. **提交您的修改** (`git commit -am '添加新功能'`)。📝
4. **推送到分支** (`git push origin feature/新功能`)。🚀
5. **创建一个新的 Pull Request**。🔗

请确保您的代码遵循项目的编码规范，并通过所有测试。✅

---
    
## 📄 许可证

本项目使用 [MIT 许可证](LICENSE) 许可证。📜 详情请参阅 LICENSE 文件。


