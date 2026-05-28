# AI 掘金头条后端

一个基于 FastAPI 的新闻头条后端项目，包含新闻分类、新闻列表、新闻详情、用户登录注册、收藏和浏览历史等接口。

## 技术栈

- Python
- FastAPI
- SQLAlchemy Async
- MySQL
- Redis
- Pydantic
- Uvicorn

## 项目结构

```text
headline-backend/
├── cache/          # 缓存相关逻辑
├── config/         # 数据库、Redis 配置
├── crud/           # 数据库操作封装
├── models/         # SQLAlchemy 数据模型
├── routers/        # API 路由
├── schemas/        # Pydantic 数据模型
├── utils/          # 通用工具
├── main.py         # FastAPI 应用入口
└── requirements.txt
```

## 主要功能

- 新闻分类查询
- 新闻列表分页查询
- 新闻详情查询
- 用户注册、登录
- 用户信息查询与修改
- 修改密码
- 新闻收藏、取消收藏、收藏列表
- 浏览历史新增、查询、删除、清空
- Redis 缓存新闻数据

## 本地运行

1. 创建并激活虚拟环境

```bash
python -m venv .venv
.venv\Scripts\activate
```

2. 安装依赖

```bash
pip install -r requirements.txt
```

3. 启动 MySQL 和 Redis

默认配置：

```text
MySQL: mysql+aiomysql://root:123456@localhost:3306/news_app?charset=utf8mb4
Redis: localhost:6379/0
```

如需修改连接信息，可以编辑：

- `config/db_conf.py`
- `config/cache_conf.py`

4. 启动服务

```bash
uvicorn main:app --reload
```

启动后访问：

- 接口服务：http://127.0.0.1:8000
- Swagger 文档：http://127.0.0.1:8000/docs

## 接口概览

### 新闻

- `GET /api/news/categories`：获取新闻分类
- `GET /api/news/list`：获取新闻列表
- `GET /api/news/detail`：获取新闻详情

### 用户

- `POST /api/user/register`：用户注册
- `POST /api/user/login`：用户登录
- `GET /api/user/info`：获取当前用户信息
- `PUT /api/user/update`：修改用户信息
- `PUT /api/user/password`：修改密码

### 收藏

- `GET /api/favorite/check`：检查是否收藏
- `POST /api/favorite/add`：添加收藏
- `DELETE /api/favorite/remove`：取消收藏
- `GET /api/favorite/list`：获取收藏列表
- `DELETE /api/favorite/clear`：清空收藏

### 浏览历史

- `POST /api/history/add`：添加浏览历史
- `GET /api/history/list`：获取浏览历史
- `DELETE /api/history/delete/{history_id}`：删除指定历史
- `DELETE /api/history/clear`：清空浏览历史

## 说明

当前项目用于 FastAPI 后端学习和练习，数据库表结构需要根据 `models/` 目录中的模型自行创建或迁移。
