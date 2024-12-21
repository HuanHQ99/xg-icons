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

参照Yaml：

```
version: "3.8"
services:
  xg-icons:
    container_name: xg-icons
    image: ghcr.io/verkyer/xg-icons:latest
    ports:
      - "28080:80" #端口号，按需修改
    volumes:
      - ./images:/var/www/html/images 
      #图标存放文件夹，里面需要再添加分组文件夹，如：/images/docker/1.png
    environment:
      - SITE_NAME=My Icons # 自定义网站名称
      #- LOGO_IMG=logo.png # 自定义logo,同目录下或网址
    restart: unless-stopped
```
自行按需修改。
