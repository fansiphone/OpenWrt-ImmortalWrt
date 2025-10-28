router主路由
gateway旁路由

# OpenWrt-Builder
基于 [ImmortalWrt](https://github.com/immortalwrt/immortalwrt) 定制编译的主路由、旁路网关，跟随 ImmortalWrt 代码更新自动编译。

## 支持的 ImmortalWrt 版本
* [x] ImmortalWrt-24.10

## 定制内容
### 精简
1. 精简全部音频组件。

### 添加
1. 升级 golang 版本（geodata、xray 等依赖高版本 go）。
2. 更换 argon 主题。
3. 添加 ttyd 终端。
4. 添加 docker 服务。
5. 添加 upnp 服务。
6. 添加 kms 服务。
7. 添加 passwall。
9. 添加多功能定时任务。
10. 添加 iStore 应用市场。

## 安装
此处不再赘述。

## 配置
1. 默认账号 `root`，密码 ``。
2. 默认 LAN 口 IP 为 `192.168.1.2`。通过 `/etc/config/network` 修改，重启后生效。
3. 推荐单独部署高级 DNS 服务。可参考 [NestingDNS](https://github.com/217heidai/NestingDNS)，一款尝试 AdGuardHome、MosDNS、SmartDNS 套娃使用最佳实践的 DNS 服务。


# 旁路网关
***仅能虚拟机安装（精简了实体卡驱动）。***

## 定制内容
### 精简
本着够用原则，非必要组件全部精简。
1. 精简 block-mount、automount 磁盘挂载相关组件。
3. 精简 ppp 拨号组建。旁路网关不负责拨号。
3. 精简全部音频组件。
4. 精简全部 usb 组件。

### 添加
1. 升级 golang 版本（geodata、xray 等依赖高版本 go）。
2. 更换 argon 主题。
3. 添加 upnp 服务。
4. 添加定时重启。
5. 添加 passwall。


## 配置
1. 默认账号 `root`，密码 ``。
2. 默认 LAN 口 IP 为 `192.168.1.2`。通过 `/etc/config/network` 修改，重启后生效。
3. LAN 口网关修改为主路由 IP 地址。
4. LAN 口 DNS 修改为主路由 IP 地址。推荐单独部署高级 DNS 服务，将旁路网关的 DNS 指过去即可。可参考 [NestingDNS](https://github.com/217heidai/NestingDNS)，一款尝试 AdGuardHome、MosDNS、SmartDNS 套娃使用最佳实践的 DNS 服务。
5. 作为旁路网关，需关闭 LAN 口 DHCP，由主路由进行 DHCP。（如开启 DHCP 服务，则变为旁路路由模式）
