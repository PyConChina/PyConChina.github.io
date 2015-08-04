# PyConChina.github.io
the root. repo for PyConChina official sites 

## bg

- 2011~2013 base UliWeb dynamic site
- 2014~ base static site, gen. by staticpycon 
    https://github.com/PyConChina/staticpycon

## deploy

base Nginx:

    upstream pycon-frontends {
        server 127.0.0.1:12306      weight=10 max_fails=4 fail_timeout=30s;
        server SS1:12306   weight=5  max_fails=4 fail_timeout=30s;
        server SS2:12306   weight=5  max_fails=4 fail_timeout=30s;
        server SS3:12306    weight=3  max_fails=4 fail_timeout=30s;
        server pyconchina.github.io weight=3  max_fails=4 fail_timeout=30s;
        }

usage multi-sites as upstream re-pub static sites for PyCon2011~2015China

in upstream hosts usage `crontab` auto sync site contents as:

> */2 * * * * root /opt/cron/deploy.sh >/dev/null 2>&1

so for all co-developer, just base github's pull-request flow,
push new contents into github, everythings will publish auto.

## (￣▽￣)

- 150803 Zoom.Quiet init.
