# ChatbotRAG - 基于B站视频的RAG聊天机器人

## 项目概述

ChatbotRAG是一个结合了检索增强生成(RAG)技术的聊天机器人应用，允许用户上传文件（如PDF等），然后基于这些文件内容与AI进行对话。系统会从上传的文件中提取相关信息，用于增强AI的回答质量和准确性。

## 技术栈

* 前端: Next.js 15.1.3, React 19, TailwindCSS
* 后端: Next.js API Routes
* 数据库: SQLite (通过Drizzle ORM)
* 向量存储: Pinecone
* AI模型: DeepSeek Chat
* 文件处理: React-Dropzone, PDF-Parse

## 主要功能

### 1. 文件上传和管理

* 支持拖放文件上传
* 显示已上传文件列表
* 支持PDF文件的解析和内容提取

### 2. 智能聊天

* 基于上传文件内容的AI辅助回答
* 实时聊天界面，支持历史消息查看
* 使用DeepSeek Chat模型生成回答

### 3. 检索增强生成(RAG)

* 利用Pinecone向量数据库实现相似内容检索
* 将用户问题转换为向量进行相似度搜索
* 将检索到的相关内容作为上下文提供给AI模型

## 项目结构

text

Apply

**/**

**├── src/                    # 源代码目录**

**│   ├── app/                # Next.js应用页面和API路由**

**│   │   ├── api/            # API路由**

**│   │   │   ├── chat/       # 聊天API**

**│   │   │   ├── upload/     # 文件上传API**

**│   │   │   └── get-files/  # 获取文件列表API**

**│   │   ├── page.tsx        # 主页面**

**│   │   └── layout.tsx      # 应用布局**

**│   ├── components/         # React组件**

**│   │   ├── ChatContainer.tsx   # 聊天界面组件**

**│   │   └── UploadContainer.tsx # 文件上传组件**

**│   ├── db/                 # 数据库相关**

**│   └── lib/                # 工具库**

**├── database.sqlite         # SQLite数据库文件**

**├── drizzle.config.ts       # Drizzle ORM配置**

**└── package.json            # 项目依赖和脚本**

## 安装与设置

### 前置条件

* Node.js 18以上
* NPM或Yarn
* Pinecone账号
* DeepSeek API密钥

### 环境变量

在项目根目录创建.env文件并配置以下变量：

text

Apply

**DEEPSEEK_API_KEY=your_deepseek_api_key**

**PINECONE_API_KEY=your_pinecone_api_key**

**PINECONE_ENVIRONMENT=your_pinecone_environment**

### 安装步骤

1. 克隆仓库

   bash

   Apply

   Run

   **git** **clone** **[**仓库地址**]**

   **cd** **chatbot**
2. 安装依赖

   bash

   Apply

   Run

   **npm** **install**

   **# 或**

   **yarn** **install**
3. 运行开发服务器

   bash

   Apply

   Run

   **npm** **run** **dev**

   **# 或**

   **yarn** **dev**
4. 访问应用

打开浏览器访问 http://localhost:3000

## 使用方法

### 上传文件

1. 在左侧面板，点击上传区域或拖拽文件到上传区域
2. 等待文件上传和处理完成
3. 上传成功后，文件将显示在上传区域下方的列表中

### 进行对话

1. 在右侧聊天面板的输入框中输入您的问题
2. 点击"Submit"按钮或按回车发送问题
3. AI将基于上传的文件内容生成回答
4. 聊天历史会保留在聊天面板中

## 技术实现细节

### 文件处理流程

1. 用户上传文件
2. 后端接收并存储文件
3. 解析文件内容（如PDF）
4. 将内容分割为适当大小的块
5. 对这些块进行向量化并存储到Pinecone

### 聊天流程

1. 用户发送问题
2. 将问题转换为向量
3. 在Pinecone中搜索相似内容
4. 检索到的内容作为上下文提供给DeepSeek模型
5. 生成的回答流式返回给前端

## 待改进功能

1. 支持更多文件格式（Word, Excel, 音视频等）
2. 添加用户认证和个人空间
3. 实现多聊天会话管理
4. 优化向量检索算法提高相关性
5. 添加聊天历史的导出功能
6. 优化移动端响应式设计

## 许可证

本项目采用MIT许可证 - 详见LICENSE文件

---

希望这份README.md文档对你有所帮助！如果你需要对文档进行任何调整或者有其他需求，请随时告诉我。
