
# 🕹️ PlayBook (极客图鉴)

> A semantic-driven gaming community built on Neo4j and BERT. The "Xiaohongshu" (Little Red Book) for hardcore gamers.
> 
> 硬核玩家的“小红书” —— 基于 Neo4j 图谱与 BERT 语义路由构建的下一代智能社区。

[![Python 3.8+](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![PyTorch](https://img.shields.io/badge/PyTorch-BERT-orange.svg)](https://pytorch.org/)
[![Neo4j](https://img.shields.io/badge/Database-Neo4j-blue.svg)](https://neo4j.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 💡 Philosophy (设计方法)


传统游戏论坛正深陷于“信息高熵”之中：标签混乱、关键词搜索严重丢失上下文、数据孤岛化。**PlayBook** 彻底重构了内容分发逻辑：
我们拒绝机械的关键词匹配，而是利用微调后的 BERT 模型进行语义降维；我们摒弃了传统关系型数据库，利用 Neo4j 将用户、帖子、标签构建为一张可无限拓展的图谱网络。

## 🏗️ Core Architecture (核心架构)

- **NLP Engine (`model.py` & `nlp.py`):** Fine-tuned BERT model for Multi-label Classification. It automatically extracts implicit semantic tags from raw user posts.
  *(基于微调的 BERT 模型，自动为用户产生的大段非结构化帖子打上精准的“多维主题标签”。)*
- **Graph Database (`neo.py`):** Data persistence via Neo4j. Solves the "query explosion" problem in traditional many-to-many relationship mapping.
  *(放弃复杂的 SQL JOIN 操作，将多对多关系下的内容推荐下放给图数据库的遍历算法，实现极低延迟的网状检索。)*
- **Gateway (`app.py`):** Lightweight backend gateway built with Flask, providing clean RESTful APIs.
  *(使用 Flask 构建轻量级后端网关。)*

## 📂 Project Structure (项目目录)

```text
PlayBook/
├── app.py          # Flask backend entry point (后端路由入口)
├── neo.py          # Neo4j connection pool and graph queries (图数据库交互层)
├── nlp.py          # BERT inference and semantic routing (语义分析网关)
├── model.py        # PyTorch model definitions (神经网络架构)
├── model.th        # Pre-trained/Fine-tuned model weights (模型权重)
├── vocab.json      # Tokenizer vocabulary (专有名词词典)
├── extfunc.py / utils.py # Utility functions (辅助工具链)
├── templates/      # Frontend HTML templates (前端模板)
└── static/         # Static assets (静态资源)
```

## 🚀 Quick Start (快速启动)

### 1. Requirements
Ensure you have Python 3.8+ and a running Neo4j instance.
```bash
# Clone the repository
git clone [https://github.com/Aurorageek/PlayBook.git](https://github.com/Aurorageek/PlayBook.git)
cd PlayBook

# Install dependencies
pip install -r requirements.txt
```

### 2. Configuration
Update your Neo4j credentials in `neo.py` or your local environment.
*(请在配置文件或环境变量中更新您的图数据库连接账密。)*

### 3. Run the Service
```bash
python app.py
```


