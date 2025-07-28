<div align="center">
    <a href="https://github.com/MarSeventh/CloudFlare-ImgBed"><img width="80%" alt="logo" src="static/readme/banner.png"/></a>
    <p><em>🗂️开源文件托管解决方案，支持 Docker 和无服务器部署，支持 Telegram Bot 、 Cloudflare R2 、S3 等多种存储渠道</em></p>
    <p>
        <a href="https://github.com/MarSeventh/CloudFlare-ImgBed/blob/main/README.md">简体中文</a> | <a href="https://github.com/MarSeventh/CloudFlare-ImgBed/blob/main/README_en.md">English</a> | <a href="https://cfbed.sanyue.de">官方网站</a>
    </p>
    <div>
        <a href="https://github.com/MarSeventh/CloudFlare-ImgBed/blob/main/LICENSE">
        <img src="https://img.shields.io/github/license/MarSeventh/CloudFlare-ImgBed" alt="License" />
        </a>
        <a href="https://github.com/MarSeventh/CloudFlare-ImgBed/releases">
        <img src="https://img.shields.io/github/release/MarSeventh/CloudFlare-ImgBed" alt="latest version" />
        </a>
        <a href="https://github.com/MarSeventh/CloudFlare-ImgBed/releases">
        <img src="https://img.shields.io/github/downloads/MarSeventh/CloudFlare-ImgBed/total?color=%239F7AEA&logo=github" alt="Downloads" />
        </a>
        <a href="https://hub.docker.com/r/marseventh/cloudflare-imgbed">
  		  <img src="https://img.shields.io/docker/pulls/marseventh/cloudflare-imgbed?style=flat-square" alt="Docker Pulls" />
		</a>
        <a href="https://github.com/MarSeventh/CloudFlare-ImgBed/issues">
          <img src="https://img.shields.io/github/issues/MarSeventh/CloudFlare-ImgBed" alt="Issues" />
        </a>
        <a href="https://github.com/MarSeventh/CloudFlare-ImgBed/stargazers">
          <img src="https://img.shields.io/github/stars/MarSeventh/CloudFlare-ImgBed" alt="Stars" />
        </a>
        <a href="https://github.com/MarSeventh/CloudFlare-ImgBed/network/members">
          <img src="https://img.shields.io/github/forks/MarSeventh/CloudFlare-ImgBed" alt="Forks" />
        </a>
    </div>
</div>





---

> [!IMPORTANT]
>
> **v2.0 版本升级注意事项请查看公告！**



<details>
    <summary>公告</summary>



## 置顶

1. 部署使用出现问题，请先仔细查阅文档、常见问题解答以及已有issues。

2. **注意**：本仓库为[Telegraph-Image](https://github.com/cf-pages/Telegraph-Image)项目的重制版，如果你觉得本项目不错，在支持本项目的同时，也请支持原项目。

## 2025.2.6  V2.0 版本升级注意事项

> v2.0 beta 版已发布，相较于 v1.0 版本进行了大量改动和优化，但 beta 版本可能存在潜在不稳定性，若您追求稳定，可选择暂缓更新。
>
> 由于**构建命令发生了变化**，此次更新需要您**手动进行**，请按照以下步骤进行操作：
>
> - 同步fork的仓库至最新版（若已自动同步可忽略）
>
> - 前往 pages 管理页面，进入`设置`->`构建`，编辑`构建配置`，在`构建命令`处填写`npm install`
>
> - 新版本所有设置项已**迁移至 管理端->系统设置 界面**，原则上无需再通过环境变量的方式进行设置，通过系统设置界面进行的设置将**覆盖掉**环境变量中的设置，但为了保证 **Telegram渠道的图片** 能够与旧版本相兼容，**若您之前设置了 Telegram 渠道相关的环境变量，请将其保留！**
>
> - 确保上述设置完成无误后，前往 pages 管理页面，进入`部署`，对最后一次不成功的部署进行`重试操作`

## 关于切换到 Telegram 渠道的通知


> 由于telegraph图床被滥用，该项目上传渠道已切换至Telegram Channel，请**更新至最新版（更新方式见第3.1章最后一节）**，按照文档中的部署要求**设置`TG_BOT_TOKEN`和`TG_CHAT_ID`**，否则将无法正常使用上传功能。
>
> 此外，目前**KV数据库为必须配置**，如果以前未配置请按照文档说明配置。
>
> 出现问题，请先查看第5节常见问题Q&A部分。

</details>




# 1. Introduction

免费文件托管解决方案，具有**上传**、**管理**、**读取**、**删除**等全链路功能，覆盖文件全生命周期，支持**鉴权**、**目录**、**图片审查**、**随机图**等各项特性（详见[功能文档](https://cfbed.sanyue.de/guide/features.html)）。

![CloudFlare](static/readme/海报.png)

# 2. [Document](https://cfbed.sanyue.de)

提供详细的部署文档、功能文档、开发计划、更新日志、常见问题解答等，帮助您快速上手。

[![更新日志](https://recent-update.cfbed.sanyue.de/cn)](https://cfbed.sanyue.de/guide/update-log.html)

# 3. Demo

**演示站点**：[CloudFlare ImgBed](https://cfbed.1314883.xyz/) 访问密码：`cfbed`

![image-20250313204101984](static/readme/202503132041511.png)

![image-20250313204138886](static/readme/202503132041072.png)

<details>
    <summary>其他页面效果展示</summary>

![image-20250313204308225](static/readme/202503132043466.png)

![image-20250314152355339](static/readme/202503141524797.png)

![image-20250313204325002](static/readme/202503132043265.png)



</details>


# 一.获取Telegram的Bot_Token和Chat_ID

1、在Telegram中，向@BotFather发送命令/newbot，根据提示依次输入您的机器人名称和用户名。成功创建机器人后，您将会收到一个TG_BOT_TOKEN，用于与Telegram API进行交互。

2、创建一个新的频道（Channel），进入该频道后，选择频道设置。将刚刚创建的机器人添加为频道管理员，这样机器人才能发送消息。

3、获取Chat_ID

通过@VersaToolsBot获取您的频道ID。向该机器人发送消息，按照指示操作，最后您将得到TG_CHAT_ID（即频道的ID）。

或者通过@GetTheirIDBot获取您的频道ID。向该机器人发送消息，按照指示操作，最后您将得到TG_CHAT_ID（即频道的ID）。

二、登录cloudflare创建pages
成功创建 fork 后来到 cloudflare 登录你的账号并打开仪表盘 点击侧边栏中的 Workers 和 Pages
然后选到 “Pages” 一栏，点击 “连接到 Git”
授权git之后选择该项目，什么都不用配置，直接点击部署
三、配置环境变量以及自定义域名
点击KV（在 Workers 和 Pages 菜单下），配置一个KV数据库，名称随意
点击R2 对象存储，配置一个R2存储桶，名称随意
绑定KV和R2 对象存储
依次点击Workers 和 Pages->概述->设置->绑定
依次点击添加->KV命名空间，选择自己创建的KV，名称设置为img_url
依次点击添加->R2存储桶，选择自己创建的R2 对象存储，名称设置为img_r2
依次点击Workers 和 Pages->概述->自定义域，输入自己托管在cloudflare的域名(如果没有可忽略这个步骤)
依次点击Workers 和 Pages->概述->设置->变量与机密
添加以下变量，其中TG_BOT_TOKEN和TG_CHAT_ID是必须添加的

构建命令：npm install

相关变量设置

AUTH_CODE = 前台的认证码

BASIC_USER = 用户名

BASIC_PASS = 密码

TG_CHAT_ID = 频道id

TG_BOT_TOKEN = 1544711526:AAHiQI  #机器人API
