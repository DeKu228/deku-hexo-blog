### 初始化博客

```bash
# 初始化博客
hexo init deku-hexo-blog
# 进入博客文件夹
cd deku-hexo-blog
# 配置安装所有的依赖包
npm install
npm install hexo-deployer-git --save
```

### 配置博客

#### 配置站点文件

```YML
# 博客基本信息
title: DeKu's Blog
subtitle: ''
description: 修身齐家治国平天下
keywords:
author: DeKu
language: zh-CN
timezone: Asia/Shanghai

# 主题选择
theme: next

# git配置
deploy:
  type: git
  repo: git@DeKu.github.com:DeKu228/deku-hexo-blog.git
  branch: master
```

#### 七牛云

```bash
npm install hexo-qiniu-sync --save
```

```yml
qiniu:
  offline: false
  sync: true
  bucket: deku-hexo-blog
  #这里将其注释掉，不注释，执行hexo g报错
  # secret_file: sec/qn.json or C:
  access_key: ptYWKYc5fqGjD8IqTlznHVhWSaD5uRO27lD1JK6e
  secret_key: iCvpxuFLt74nd38k1oxzEJht3WLEfACWGgGmtoKy
  #上传的资源子目录前缀.如设置，需与urlPrefix同步
  dirPrefix: static
  #外链前缀
  urlPrefix: http://q1ciolgbz.bkt.clouddn.com/static
  #使用默认配置即可
  up_host: http://upload.qiniu.com
  #本地目录
  local_dir: static
  #是否更新已经上传过的文件(仅文件大小不同或在上次上传后进行更新的才会重新上传)
  update_exist: true
  image:
    folder: images
    extend:
  js:
    folder: js
  css:
    folder: css
```

#### RSS

- 安装RSS插件

  ```bash
  npm install --save hexo-generator-feed
  ```

- 在 **站点配置文件** 末尾添加

  ```yml
  plugins: hexo-generate-feed
  ```

- 修改 **主题配置文件**

  ```yaml
  rss: /atom.xml
  ```

#### 文章置顶

- 安装置顶插件

  ```bash
  npm uninstall hexo-generator-index --save
  npm install hexo-generator-index-pin-top --save
  ```

- 修改站点目录下`scaffolds/post.md`

  ```yaml
  top: false
  ```

- 修改`themes/next/layout/_macro` 目录下面的 `post.swig` ，定位到 `<div class="post-meta">` 插入以下代码：

  ```html
  <div class="post-meta">
      {% if post.top %}
      <i class="fa fa-thumb-tack"></i>
      <font color=7D26CD>置顶</font>
      <span class="post-meta-divider">|</span>
      {% endif %}
      ...
      ...
  </div>
  ```

#### 站内搜索

- 安装插件

  ```bash
  npm install hexo-generator-searchdb --save
  ```

- 主题配置文件`/source/_data/next.yml`

  ```yaml
  local_search:
    enable: true
    trigger: auto  # 每次输入改变都执行搜索
    top_n_per_article: 3  # 每篇文章显示的搜索结果数量
    unescape: false
  ```

- 在 **站点配置文件** 添加以下字段

  ```bash
  search:
    path: search.xml
    field: post  # 指定搜索范围，可选 post | page | all
    format: html  # 指定页面内容形式，可选 html | raw (Markdown) | excerpt | more
    limit: 10000
  ```

- 效果

  ![QQ图片20191126144535](G:\WorkSpace\DeKu\deku-hexo-blog\static\images\QQ图片20191126144535.png)



### 必要插件

```
# git
npm install hexo-deployer-git --save
# rss
npm install hexo-generator-feed --save
# 站内搜索
npm install hexo-generator-searchdb --save

```

