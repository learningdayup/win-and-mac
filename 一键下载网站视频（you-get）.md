---
一键下载各大网站视频(you-get)
---



## 推荐一个神器you-get！！！
最近，想下载b站视频，然后电脑上没有缓存按钮，网上查了半天，都是一个一个下载的，然而我想批量，于是乎就有了you-get！


1.首先安装python
2.安装you-get

```
pip install you-get
```

3.执行命令

```
you-get -o 存储位置 网址
```

然而，一切并不是那么顺利，执行完第三步之后，发现报错了

```
# 报错信息
you-get: [error] oops, something went wrong. 
you-get: don't panic, c'est la vie. please try the following steps: 
you-get: (1) Rule out any network problem. 
you-get: (2) Make sure you-get is up-to-date. 
you-get: (3) Check if the issue is already known, on 
you-get: https://github.com/soimort/you-get/wiki/Known-Bugs 
you-get: https://github.com/soimort/you-get/issues 
you-get: (4) Run the command with '--debug' option, 
you-get: and report this issue with the full output. 
```

打开浏览器一看，我的天这么多人有这个问题，然而并没有解决办法（欲哭无泪）！


**找到了一个mac上的解决办法：**

找到bilibili.py文件所在的位置，如果是brew安装的you-get的话，mac系统的位置应该是在/usr/local/Cellar/you-get/0.4.1011_1/libexec/lib/python3.6/site-packages/you_get/extractors
在该目录下找到bilibili.py，打开文件，在代码的70行进行修改。

```
# 使用第三行的代码替换第二行代码
xml_str = get_content(api_url)
xml_str = get_content(api_url, headers={'referer': self.url, 'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_12_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.3239.84 Safari/537.36'})
```

再用--debug试一下，

```
you-get -i 视频地址 --debug
```

perfect！

**win解决办法：**

```
you-get -o 存储位置 -l 网址
```

ok,完事！

测试了一下，发现下载速度还挺快。



