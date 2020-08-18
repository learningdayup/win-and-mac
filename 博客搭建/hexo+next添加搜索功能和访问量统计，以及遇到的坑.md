---
hexo+next添加搜索功能和访问量统计，以及遇到的坑
---

## 目录

1.添加搜索功能
2.添加访问量
3.所踩过的坑



### 1.添加搜索功能

**在博客根目录下，执行如下命令**

    npm install hexo-generator-searchdb --save


**修改站点配置文件**

修改根目录下_config.yml，在最底部添加如下配置

```
search:
    path: search.xml
    field: post
    format: html
    limit: 10000
```


**修改主题配置文件**
修改主体下的themes\next_config.yml配置文件，搜索local_search，修改enable为true

```
local_search:
    enable: true
```


## 2.添加访问量

这里使用的是**不蒜子**提供的阅读统计功能。

**添加是否开启统计功能的配置**

找到next主题的配置文件themes/next/_config.yml，找到原来的footer字段，加入一个配置，这里我们叫它counter吧，即

```	
footer:
    counter: true
```

**修改next主题的模板文件**
需要修改的模板文件是theme/next/layout/_partials/footer.swig。 

```
{% if theme.footer.counter %}
    <script async src="//dn-lbstatics.qbox.me/busuanzi/2.3/busuanzi.pure.mini.js"></script>

    <span id="busuanzi_container_site_pv">总访问量<span id="busuanzi_value_site_pv"></span>次</span>
    <span class="post-meta-divider">|</span>
    <span id="busuanzi_container_site_uv">总访客<span id="busuanzi_value_site_uv"></span>人</span>
    <span class="post-meta-divider">|</span>

{% endif %}
```

## 3.踩过的坑

### 3.1 忘记冒号添加空格；

```
错误提示：FATAL bad indentation of a mapping entry at line 52, column 3:
```

### 3.2 出现npm audit fix

此时按照错误提示一步一步操作即可

```
run `npm audit fix` to fix them, or `npm audit` for details html
```

按照控制台提示的命令，输入 npm audit fix；

之后提示

```
(use 'npm audit fix --force' to install breaking changes; or do it by hand)
```

输入 npm audit fix --force

之后重新输入 npm audit，一切正常。


