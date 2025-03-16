# 前言

此知识库使用 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 创建

* `Material for MkDocs` 建立在 [mkdocs](https://www.mkdocs.org) 之上

## 使用

* `git clone` 此 repository
* `cd knowledge-base`

### 安装 `Material for MkDocs`

#### (可选) 使用任意 `python` 包管理工具, 来选择你最喜欢的 `python` 版本以及 `pip` 版本

#### 使用 `pip` 安装

`pip install mkdocs-material` - 最新版

### 在本地部署 `Material for MkDocs`

* `mkdocs serve` - 启动实时重新加载的文档服务器.
    + 通过 [http://127.0.0.1:8000/](http://127.0.0.1:8000/) 访问
* `mkdocs build` - 构建静态站点.
* `mkdocs -h` - 显示帮助信息并退出.

## Project layout

    mkdocs.yml    # 配置文件.
    docs/
        index.md  # 文档首页.
        ...       # 其他 markdown 页面, 图片及其他文件.
