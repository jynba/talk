---
theme: ./
title: JY Share
favicon: mokkapps-logo.png
layout: cover
lineNumbers: true
---

# 使用 Nginx Proxy Manager 管理网站


<div class="pt-12">
  <span @click="next" class="px-2 p-1 rounded cursor-pointer hover:bg-white hover:bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

---
layout: section
---

# 什么是 Nginx Proxy Manager

Nginx Proxy Manager(NPM) 一个强大的Nginx可视化管理平台。

用于管理Nginx服务器的工具，主要功能包括一键配置Nginx反向代理、重定向、SSL认证、404错误页等等...

---

# 使用 docker 挂载网站

前置准备：开放对应端口

<img class="w-full" src="/port.png">

代码解释：新建一个nginx容器拷贝所需挂载的文件；运行nginx容器映射在4567端口

```bash
mkdir -p ./nginx/{logs,conf,html}
docker run -d --name nginx-test nginx
docker cp nginx-test:/etc/nginx/conf.d ./nginx/conf
docker cp nginx-test:/etc/nginx/nginx.conf ./nginx/conf/nginx.conf
docker cp nginx-test:/usr/share/nginx/html/index.html ./nginx/html/index.html
docker rm -f nginx-test

docker run -it -p 4567:80 --name nginx-handle \
-v ./nginx/conf/nginx.conf:/etc/nginx/nginx.conf \
-v ./nginx/html:/usr/share/nginx/html \
-v ./nginx/logs:/var/log/nginx \
-d nginx
```

将打包代码放在html文件中

---

# Nginx Proxy Manager

<img class="w-full" src="/banner.png">

[Nginx Proxy Manager官网](https://nginxproxymanager.com)

---

# Nginx Proxy Manager有啥用 ?

前置准备：添加对应子域名DNS记录
<img class="w-full" src="/handle.png">

[在线演示](https://npm.cvcvcvcv.com)
* 将端口访问改为https访问（配置SSL）
* 一键配置Nginx反向代理、重定向、404错误页
* 多用户管理
* 操作日志查看


<div class="abs-b mx-14 my-12">
  <span class="opacity-50">参考：</span>
  <Reference name="Nginx Proxy Manager的配置和使用" url="https://blog.fjy.zone/archives/nginx-proxy-manager" />
</div>

---
layout: iframe-right
url: "https://stackblitz.com/github/jynba/jynba.github.io?file=.github%2Fworkflows%2Fgenerate_readme.yml"
---

# 博客

github.io如何默认跳网站？网站如何cname到page？如何通过issue写博客？

[博客地址](https://jyblog.cvcvcvcv.com/timeline)

两个工作流： 
* 检测到issue[open]新增，执行工作流：1. 脚本生成md文件; 2. Push main
* 检测到main push，执行部署静态文件，cname到子域名

GitHub Action Bot [个人令牌](https://github.com/settings/tokens)


<div class="abs-b mx-14 my-12">
  <span class="opacity-50">参考：</span>
  <Reference name="利用Octokit与GitHub交互" url="https://jyblog.cvcvcvcv.com/timeline/issue-60" />
</div>


---
layout: iframe-right
url: "https://stackblitz.com/github/jynba/motui-uniapp?file=README.md"
---

# 组件库
[MotUI](https://motui.cvcvcvcv.com)

* 移动端组件在线预览 (iframe嵌入)
* npm包导入，支持[按需引入unplugin](https://uni-helper.js.org/vite-plugin-uni-components) 和 easycom 两种方式
* [vscode插件](https://github.com/jynba/motui-vscode-extension)支持：[智能提示补全](https://juejin.cn/post/7138308389595152420)；跳转组件文档;

<div class="abs-b mx-14 my-12">
  <span class="opacity-50">参考：</span>
  <Reference name="uni-helper 按需导入" url="https://uni-helper.js.org/vite-plugin-uni-components" />
  <Reference name="实现全局组件在代码编辑器中的智能提示" url="https://juejin.cn/post/7138308389595152420" />
  <Reference name="如何发布一个vscode插件" url="https://juejin.cn/post/7076649162653040647" />
  <Reference name="vscode插件管理" url="https://marketplace.visualstudio.com/manage/publishers/motui" />
</div>

---
layout: video
video: 'https://slidev.cvcvcvcv.com/go.mp4'
---

# 定向越野小程序

---
layout: iframe-right
url: "https://stackblitz.com/github/jynba/dxyy_project?file=subPackages%2Fpages%2Fgamemap%2Fgamemap.js"
---

# mqtt 发布订阅模式

发布订阅模式

<img class="w-full" src="/subscribe.png">

* topic：`roomId+update/get`作为topic
* subscribe：订阅对应topic 
* publish：发布自己当前的信息(坐标、头像...)
* on('message',()=>{})：接收数据,更新信息


<div class="abs-b mx-14 my-12">
  <span class="opacity-50">参考：</span>
  <Reference name="微信小程序接入MQTT" url="https://docs.emqx.com/zh/emqx/latest/connect-emqx/wechat-miniprogram.html" />
</div>

---
layout: center
---

# Thank you for listening!

<div class="abs-b mx-14 my-12">
  <Reference name="Repository" url="https://github.com/jynba" />
  <Reference name="Slides" url="https://slidev.cvcvcvcv.com" />
</div>

