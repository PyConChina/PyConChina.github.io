# PyConChina.github.io
the root. repo for PyConChina official sites 

## bg

- 2011~2013 base UliWeb dynamic site
- 2014~ base static site, gen. by staticpycon 
    https://github.com/PyConChina/staticpycon

## deploy
基于 https://github.com/PyConChina/staticpycon


- 进入 staticpycon
- `fab build` 查阅本地编译效果
- `fab pub2hub` 发布编译成果到专用仓库
    + 检出 https://github.com/PyConChina/PyConChina.github.io
    + 将 `/2015` 链接为 https://github.com/PyConChina/staticpycon 当前工作仓库的 `out` 目录
    + 这样 `fabric` 将自动在本地完成编译,再将所有静态页面推送到对应的 github.io `pages` 发布仓库
    + 接着多个主机定期同步到 `pages` 仓库,完成官网的均衡发布

## publish
base Nginx:

    upstream pycon-frontends {
        server 127.0.0.1:12306      weight=10 max_fails=4 fail_timeout=30s;
        server SS1   weight=5  max_fails=4 fail_timeout=30s;
        server SS2   weight=5  max_fails=4 fail_timeout=30s;
        server SS3   weight=3  max_fails=4 fail_timeout=30s;
        server pyconchina.github.io weight=3  max_fails=4 fail_timeout=30s;
        }

usage multi-sites as upstream re-pub static sites for PyCon2011~2015China

in upstream hosts usage `crontab` auto sync site contents as:

> */2 * * * * root /opt/cron/deploy.sh >/dev/null 2>&1

so for all co-developer, just base github's pull-request flow,
push new contents into github, everythings will publish auto.

## (￣▽￣)

- 150803 Zoom.Quiet init.
