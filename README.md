# goindex
Google Drive Directory Index

## 功能：
部署在 CloudFlare Workers的小程序。  
可以将 Google Drive 文件以目录形式列出，并直连下载。  
流量走 CloudFlare ，网速由 CloudFlare 决定。

## Demo
[https://index.gd.workers.dev/](https://index.gd.workers.dev/)  


## 安装部署方案1  
1、在本地安装 rclone   
2、按照 https://rclone.org/drive/ 流程进行授权。  
3、执行 rclone config file 查看 rclone.conf 路径。找到root_folder_id和refresh_token记录下来。  
4、下载 https://github.com/donwa/goindex 中的 index.js  并填入 root 和 refresh_token  
5、复制代码 到 CloudFlare 部署。  


## 安装部署方案2  
作者不会记录refresh_token，但为避免纠纷，建议有条件的同学使用方案1进行部署  
1、访问[https://install.gd.workers.dev/](https://install.gd.workers.dev/)  
2、授权认证后，生成部署代码。  
3、复制代码 到 CloudFlare 部署。  

## 文件夹密码：
在google drive 文件中放置 `.password` 文件来设置密码。  
密码文件只能保护该文件不被列举，不能保护该文件夹的子文件夹不被列举。  
也不保护文件夹下文件不被下载。  
  
程序文件中 `root_pass` 只为根目录密码，优先于 `.password` 文件  


## 更新日志  
1.0.2  
优化前端逻辑  
添加文件预览功能(临时)  
添加前端文件缓存功能  
  
1.0.1  
添加 README.md 、 HEAD.md 支持  
  
1.0.0  
前后端分离，确定基本架构  
添加.password 支持  

------
1.自己的git fork一份 https://github.com/5Lin/goindex

2.自己的git-goindex - 发布release 版本号自定，可以为1.0.6可以为其他比如 15

3.替换15行代码

原来 //cdn.jsdelivr.net/combine/gh/jquery/jquery@3.2/dist/jquery.min.js,gh/donwa/goindex@${authConfig.version}/themes/${authConfig.theme}/app.js

替换为

//cdn.jsdelivr.net/combine/gh/jquery/jquery@3.2/dist/jquery.min.js,gh/自己git名/goindex@第二步发布的release的版本号/themes/${authConfig.theme}/app.js

*注意仓库public
-----
fork一份，cfworker中找出23行
cdn.jsdelivr.net/combine/gh/jquery/jquery@3.2/dist/jquery.min.js,gh/xxxxx/goindex
xxxxx改成自己Github的库
比如cdn.jsdelivr.net/combine/gh/jquery/jquery@3.2/dist/jquery.min.js,gh/Reves/goindex
