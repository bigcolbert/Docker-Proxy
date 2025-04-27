<div style="text-align: center"></div>
  <p align="center">
  <img src="https://github.com/dqzboy/Docker-Proxy/assets/42825450/c187d66f-152e-4172-8268-e54bd77d48bb" width="230px" height="200px">
      <br>
      <i>使用 Claw Cloud 免费容器服务快速部署我们的Docker镜像加速服务.</i>
  </p>
</div>

---

[Docker Proxy-交流群](https://t.me/+ghs_XDp1vwxkMGU9) 

---


## 📦 部署
> 以下步骤需要有 Claw Cloud 账号，没有账号的需要先注册

- **提醒**： 点击下面链接注册账号，推荐使用注册时长超过180天的GitHub账号注册，GitHub账号超过180天的用户注册，可解锁每月5$


**1. 注册账号 [点击此处，注册账号](https://console.run.claw.cloud/signin?link=PZNPEDMUAT4G)**

<table>
    <tr>
        <td width="50%" align="center"><img src="https://cdn.jsdelivr.net/gh/dqzboy/Images/dqzboy-proxy/clawcloud-01.png?raw=true"></td>
    </tr>
</table>

<table>
    <tr>
        <td width="50%" align="center"><img src="https://cdn.jsdelivr.net/gh/dqzboy/Images/dqzboy-proxy/clawcloud-02.png?raw=true"></td>
    </tr>
</table>
<table>
    <tr>
        <td width="50%" align="center"><img src="https://cdn.jsdelivr.net/gh/dqzboy/Images/dqzboy-proxy/clawcloud-03.png?raw=true"></td>
    </tr>
</table>


**2. 创建服务**
<table>
    <tr>
        <td width="50%" align="center"><img src="https://cdn.jsdelivr.net/gh/dqzboy/Images/dqzboy-proxy/clawcloud-04.png?raw=true"></td>
    </tr>
</table>

<table>
    <tr>
        <td width="50%" align="center"><img src="https://cdn.jsdelivr.net/gh/dqzboy/Images/dqzboy-proxy/clawcloud-05.png?raw=true"></td>
    </tr>
</table>

**3. 选择以docker容器的方式部署，输入下面任一镜像地址**


| 镜像 | 平台 |
|-------|---------------|
| dqzboy/mirror-hub:latest   | docker hub
| dqzboy/mirror-gcr:latest      | Google Container Registry
| dqzboy/mirror-ghcr:latest     | GitHub Container Registry
| dqzboy/mirror-k8sgcr:latest  | Kubernetes Container Registry
| dqzboy/mirror-k8sreg:latest      | Kubernetes's container image registry
| dqzboy/mirror-quay:latest     | Quay Container Registry
| dqzboy/mirror-elastic:latest     | Microsoft Container Registry
| dqzboy/mirror-mcr:latest     | Elastic Stack

<table>
    <tr>
        <td width="50%" align="center"><img src="https://cdn.jsdelivr.net/gh/dqzboy/Images/dqzboy-proxy/clawcloud-06.png?raw=true"></td>
    </tr>
</table>

<table>
    <tr>
        <td width="50%" align="center"><img src="https://cdn.jsdelivr.net/gh/dqzboy/Images/dqzboy-proxy/clawcloud-07.png?raw=true"></td>
    </tr>
</table>


<table>
    <tr>
        <td width="50%" align="center"><img src="https://cdn.jsdelivr.net/gh/dqzboy/Images/dqzboy-proxy/clawcloud-08.png?raw=true"></td>
    </tr>
</table>


**4. 服务运行完成之后，等待一些时间后，使用外网域名进行访问，显示空白页面即表示正常**
<table>
    <tr>
        <td width="50%" align="center"><img src="https://cdn.jsdelivr.net/gh/dqzboy/Images/dqzboy-proxy/clawcloud-09.png?raw=true"></td>
    </tr>
</table>

## ✨ 如何使用

> 下面是以加速Docker Hub平台镜像下载举例

**1. 改`Docker的daemon.json`配置，配置你 Claw Cloud 分配的外网地址。修改后重启docker**

```shell
~]# vim /etc/docker/daemon.json
{
    "registry-mirrors": [ "https://your_ClawCloud_url" ],
    "log-opts": {
      "max-size": "100m",
      "max-file": "5"
    }
}
```
**2. 使用Claw Cloud服务地址替换官方的 Registry 地址拉取镜像**
```shell
# docker hub Registry
## 源：redis:latest
## 替换
docker pull your_ClawCloud_url/library/redis:latest
```

> **说明**：如果上面配置了docker的`daemon.json`，那么拉取镜像的时候就不需要在镜像前面加`Claw Cloud`了。【只针对拉取Docker Hub上的镜像有效】