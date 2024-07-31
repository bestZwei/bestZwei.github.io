---
layout:     post
title:      "CF Pages/Vercel部署基于Deeplx的翻译网页"
subtitle:   "Windows设备管理多个git账号"
date:       2024-07-31
author:     "Zwei"
catalog:    true
header-style: text
tags:
    - 技术
    - Pages
    - Deeplx
    - translate
---

#### 项目地址 https://github.com/bestZwei/LibreTranslator

#### 效果展示：https://fy.is-a.dev

![jt](https://pics.sputnik.cloudns.ch/file/bf4c270e2bfb23cc6a07e.png)

### 部署

#### 1、使用 Cloudflare Pages 部署

1. Fork 本仓库。
2. 登录到 [Cloudflare](https://www.cloudflare.com/) ，在 Cloudflare Dashboard 中，选择 "Pages"。
3. 点击 "Create a Project"。
4. 连接到您的 GitHub 存储库，并选择该项目。
5. 在 "Configure your build" 步骤中，使用以下设置：
   - **Framework preset**: 
   - **Build command**: `npm run build`
   - **Build directory**: `build`
6. 点击 "Save and Deploy"。

#### 2、使用 Vercel 部署

1. Fork 本仓库。
2. 登录到 Vercel，点击 "New Project"。
3. 连接到您的 GitHub 存储库，并选择该项目。
4. Vercel 会自动检测到您使用的是 React 项目。您可以使用默认设置。
5. 点击 "Deploy"。

#### 所有部署方式都要配置环境变量

1. **REACT_APP_DEEPLX_API_URL**: `https://api.deeplx.org/<api-key>`  ，不带 `/translate`

   用于存储 DeepLx API 的 URL，以便在请求翻译时使用。`<api-key> `可以从 https://connect.linux.do/ 获取。

   或者你是Pro用户，参考 [DeepLx文档 ](https://deeplx.owo.network/endpoints/pro.html)使用 `/v1` 请求 ，`https://api.deeplx.org/v1`

2. **REACT_APP_PASSWORD（可选）**: 访问密码

   用于存储访问口令，限制其他人使用你部署的翻译网页。

3. **NODE_OPTIONS**:`--openssl-legacy-provider`   

   这个变量用于配置 Node.js 的选项，通常用于解决某些依赖包的兼容性问题，不设置则可能部署失败。

4. **REACT_APP_API_TOKEN（可选）**：按需修改，如果你是**自建的DeepLx服务**，参考请求链接是 `REACT_APP_DEEPLX_API_URL/translate?token=REACT_APP_API_TOKEN`，填写这两个环境变量。

   常用的请求格式