# Original author：sh1375
# Original project address： https://github.com/sh1375/v2ray-agent
# v2ray-agent

> [Thanks to JetBrains for providing a non-commercial open source software development license](https://www.jetbrains.com/?from=v2ray-agent)

> [Thanks for non-commercial open source development authorization by JetBrains](https://www.jetbrains.com/?from=v2ray-agent)

> [English Version](https://github.com/sh1375/v2ray-agent/blob/master/documents/en/README_EN.md)

- [Cloudflare Optimization plan](https://github.com/sh1375/v2ray-agent/blob/master/documents/optimize_V2Ray.md)
- [Traffic transit](https://github.com/sh1375/v2ray-agent/blob/master/documents/traffic_relay.md)
- [Manual self-built tutorial](https://github.com/sh1375/v2ray-agent/blob/master/documents/Cloudflare_install_manual.md)
- [ssh Getting started tutorial](https://www.v2ray-agent.com/2020-12-16-ssh%E5%85%A5%E9%97%A8%E6%95%99%E7%A8%8B)
- [TG group](https://t.me/technologyshare)、[TG Channel-Update notification](https://t.me/v2rayAgentChannel)、[Blog address](https://www.v2ray-agent.com/)
- **Please give one ⭐Support it**

* * *

# Table of contents

- [1.Script installation](#1vlesstcptlsvlesswstlsvmesstcptlsvmesswstlstrojan-Camouflage site-Eight-in-one coexistence script)
    - [Combination method] (#Combination method)
    - [Combination recommendation] (#Combination Recommendation)
    - [Feature](#Feature)
    - [Precautions] (#Precautions)
    - [Installation script] (#Installation script)

* * *

# 1.Eight-in-one coexistence script + camouflage site

- [Cloudflare Getting started tutorial](https://github.com/sh1375/v2ray-agent/blob/master/documents/cloudflare_init.md)

## characteristic
- support [Xray-core[XTLS]](https://github.com/XTLS/Xray-core)、[v2ray-core](https://github.com/v2fly/v2ray-core)
- support VLESS/Trojan Front[VLESS XTLS -> Trojan XTLS]、[Trojan XTLS -> VLESS XTLS]
- Support not Configuration files between the same core read each other
- support VLESS/VMess/trojan agreement
- support Debian、Ubuntu、Centos The system supports mainstream cpu architectures.
- Support any combination of installation, support multi-user management, support DNS Streaming media unlocking, support for adding multiple ports, [support for unlocking any door Netflix](https://github.com/sh1375/v2ray-agent/blob/master/documents/netflix/dokodemo-unblock_netflix.md)
- Support retention after uninstall tls certificate
- support IPv6，[IPv6 Precautions](https://github.com/sh1375/v2ray-agent/blob/master/documents/ipv6_help.md)
- support WARP Shunt、IPv6 Shunt
- support BT Download management, log management, domain name blacklist management, core management, camouflage site management
- [Support custom certificate installation](https://github.com/sh1375/v2ray-agent/blob/master/documents/install_tls.md)

## Supported installation types

- VLESS+TCP+TLS
- VLESS+TCP+xtls-rprx-direct
- VLESS+gRPC+TLS【support CDN、IPv6、Low latency】
- VLESS+WS+TLS【support CDN、IPv6】
- Trojan+TCP+TLS【**Recommended**】
- Trojan+TCP+xtls-rprx-direct
- Trojan+gRPC+TLS【support CDN、IPv6、Low latency】
- VMess+WS+TLS【support CDN、IPv6】

## Line recommendation

- [CN2 GIA](https://github.com/sh1375/v2ray-agent/blob/master/documents/donation_aff.md#1cn2-gia)
- Shanghai CN2+HK
- [AS9929](https://github.com/sh1375/v2ray-agent/blob/master/documents/donation_aff.md#2%E8%81%94%E9%80%9A-as9929a%E7%BD%91)
- [AS4837](https://github.com/sh1375/v2ray-agent/blob/master/documents/donation_aff.md#3%E8%81%94%E9%80%9A-as4837%E6%99%AE%E9%80%9A%E6%B0%91%E7%94%A8%E7%BD%91)
- [Unicom Japan Softbank](https://github.com/sh1375/v2ray-agent/blob/master/documents/donation_aff.md#4%E8%81%94%E9%80%9A-%E6%97%A5%E6%9C%AC%E8%BD%AF%E9%93%B6)
- Unicom + Taiwan TFN
- Unicom+NTT
- Wide shift/Bead shift+HKIX/CMI/NTT
- Wide shift/CN2+Cloudflare+global
- Wide shift/CN2/Southern Union +Hong Kong AZ+ Global
- Transit + cloudflare + landing machine [can pull the world]

## Combination recommendation

- Transit/gia/AS4837/AS9929 ---> VLESS+TCP+TLS/XTLS、Trojan
- Mobile broadband ---> VMESS+WS+TLS/VLESS+WS+TLS/VLESS+gRPC+TLS/Trojan+gRPC+TLS + Cloudflare
- cloudflare-> VLESS+gRPC+TLS/Trojan+gRPC+TLS[Multiplexing, low latency]

## Precautions

- **modify Cloudflare->SSL/TLS->Overview->Full**
- **Cloudflare ---> A The cloud that records the analysis must be gray [If it is not gray, it will affect the automatic renewal of the certificate for scheduled tasks]**
- **If you use CDN and use direct connection at the same time, turn off Cloud + optional IP, refer to the optional IP above [Cloudflare Optimization plan](https://github.com/sh1375/v2ray-agent/blob/master/documents/optimize_V2Ray.md)**
- **Use a pure system to install. If you have installed it using other scripts and you cannot modify the error by yourself, please reinstall the system and try to install again.**
- wget: command not found [**You need to install it manually here wget**]
  ，If not used Linux，[Click to view](https://github.com/sh1375/v2ray-agent/tree/master/documents/install_tools.md)Installation tutorial
- Does not support non-root account
- **If you find Nginx-related problems, please uninstall the self-compiled nginx or reinstall the system**
- **In order to save time, please bring detailed screenshots or follow the template specifications for feedback. Issues that do not have screenshots or do not follow the specifications will be closed directly.**
- **Not recommended for GCP users**
- **It is not recommended to use Centos and lower-version systems. If the Centos installation fails, please switch to Debian10 and try again. The script is no longer supported.Centos6、Ubuntu 16.x**
- **[If you don't understand the use, please check the script usage guide first](https://github.com/sh1375/v2ray-agent/blob/master/documents/how_to_use.md)**
- **Oracle Cloud There is an additional firewall that needs to be set up manually**
- **Oracle Cloud Only support Ubuntu**
- **If used gRPC pass cloudflare Forward, need to be in cloudflare Settings allow gRPC，path：cloudflare Network->gRPC**
- **gRPC It is currently in the testing phase and may not be compatible with the client you are using. If it cannot be used, please ignore it.**
- **The problem that the low-version script cannot start when upgrading to a high-version script, [Please click this link to view the solution](https://github.com/sh1375/v2ray-agent/blob/master/documents/how_to_use.md#4%E4%BD%8E%E7%89%88%E6%9C%AC%E5%8D%87%E7%BA%A7%E9%AB%98%E7%89%88%E6%9C%AC%E5%90%8E%E6%97%A0%E6%B3%95%E5%90%AF%E5%8A%A8%E6%A0%B8%E5%BF%83)**

## [Script usage guide](https://github.com/sh1375/v2ray-agent/blob/master/documents/how_to_use.md)、[Script directory](https://github.com/sh1375/v2ray-agent/blob/master/documents/how_to_use.md#5脚本目录)

## donate

[You can use my AFF to purchase VPS donation-blog](https://www.v2ray-agent.com/%E6%82%A8%E5%8F%AF%E4%BB%A5%E9%80%9A%E8%BF%87%E6%88%91%E7%9A%84AFF%E8%B4%AD%E4%B9%B0vps%E6%8D%90%E8%B5%A0)

[You can use my AFF to purchase VPS donation-Github](https://github.com/sh1375/v2ray-agent/blob/master/documents/donation_aff.md)

[Support donating to me through virtual coins](https://github.com/sh1375/v2ray-agent/blob/master/documents/donation.md)

## Installation script

- Support shortcut startup, after installation，shell input【**vasma**】You can open the script, the script execution path[**/etc/v2ray-agent/install.sh**]

- Latest Version【recommend】

```
wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/sh1375/v2ray-agent/master/install.sh" && chmod 700 /root/install.sh && /root/install.sh
```

- shadowsocks Dynamic IP whitelist mode【Beta】

```
wget -P /root -N --no-check-certificate "https://raw.githubusercontent.com/sh1375/v2ray-agent/dev_ss/install.sh" && chmod 700 /root/install.sh && /root/install.sh
```

# Example diagram

<img src="https://raw.githubusercontent.com/sh1375/v2ray-agent/master/fodder/install/install.jpg" width=700>

# license

[AGPL-3.0](https://github.com/sh1375/v2ray-agent/blob/master/LICENSE)

## Stargazers over time

[![Stargazers over time](https://starchart.cc/sh1375/v2ray-agent.svg)](https://starchart.cc/sh1375/v2ray-agent)
