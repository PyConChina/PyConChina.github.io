# 

cn.pycon.org/2014 官方网站 发布 仓库

发布网站为 http://con.pychina.org

## 简介

- 用 [PyConChina/MkDoc4PyCon](https://gitcafe.com/PyConChina/MkDoc4PyCon) 生成静态布面
- 网站 host 在 Linode 上

## 本地

### 安装并使用虚拟环境

```sh
pip install virtualenv fabric
mkdir pycon && cd pycon
virtualenv env
source env/bin/activate
```

### 克隆代码

```sh
git clone git@gitcafe.com:PyConChina/staticpycon.git
```

### 启动本地服务器

```sh
cd staticpycon
python bin/app.py
```

这时在浏览器里访问 http://localhost:8080 就能看到效果了. 

修改某个页面的 markdown 源文件之后, 
会自动重新生成 html 页面, 只需要刷新浏览器就能看到效果. 

## 布署到 con.pychina.org

在本地作了修改之后,发布到 con.pychina.org 的步骤如下:

- 在工作目录以外 clone 当前仓库

```sh
git clone git@gitcafe.com:PyConChina/PyConChina.git
cd PyConChina
git checkout gitcafe-pages
```


- 回到工作目录,建立目录链接

```sh
cd /path/2/staticpycon
ln -s ../PyConChina out
```


- 发布到 `gitcafe-pages` 空间

```sh
fab pub2cafe
```

ps:

有关资源/资料文件的发布/管理/增补, 不建议直接通过 git 仓库,
参考: [我们是如何使用7牛云储存的 | GDG Livin ZhuHai Life;-)](http://blog.zhgdg.org/2013-08/usage7niu/)

通过各自或是相同 bucket 中不同的专用目录来完成快速发布.

## 参考

基于 [[2012/10/31]GitCafe正式推出的Pages服务](http://blog.gitcafe.com/116.html)
发布方案,
因为,没有足够的灵活度,
仅作为复本,备用.

## 进展

- 140728 DAMA 快速用 MkDoc 完成轻量级静态网站
- 140715 Limodou 完成 UliWeb 部分静态化功能
- 140701 PyConChina 列表内部发动
