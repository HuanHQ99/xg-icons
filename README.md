# xg-icons
## 介绍
使用ChatGpt糊的图标托管项目，基于PHP，可以实现自动抓取分组内的图标镜像展示，并且快速复制；
适合于托管自己的docker图标库等用途~
## 界面展示
![image](https://github.com/verkyer/xg-icons/blob/main/demo.png)
## 部署方式
### PHP
下载本项目，`/web`里面的文件丢到php环境的网站www根目录即可（例如宝塔、1Panel、AMH等php环境）

将你的JPG、PNG图标，放到`/images/分组名称`文件下；例如`/images/docker/1.png`，就会自动抓取分组名称、图标名称，展示到首页。
### docker
推荐使用 [trafex/php-nginx](https://hub.docker.com/r/trafex/php-nginx) 项目，部署后将本项目放到映射的 `/www/html` 目录

参照yaml：

```
version: "3.3"
services:
  php-nginx:
    container_name: php-nginx
    ports:
      - 19680:8080
    volumes:
      - ./www/html:/var/www/html
    image: trafex/php-nginx
```
自行按需修改端口、映射路径。
