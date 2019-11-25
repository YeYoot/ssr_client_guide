# Ubuntu客户端使用说明

其他linux操作系统使用方法类似，请自行摸索。

建议Ubuntu版本大于等于16。

## 下载软件

切换到root用户，执行以下命令：

```
bash <(curl -L -s https://install.direct/go.sh)
```

注：当 yum 或 apt-get 可用的情况下，此脚本会自动安装 unzip 和 daemon。这两个组件是安装 V2Ray 的必要组件。如果你使用的系统不支持 yum 或 apt-get，请自行安装 unzip 和 daemon

## V2ray配置

### tcp协议

1. 修改/etc/v2ray/config.json文件内容，需要改的部分主要是outbounds中vnext的address,port,users这三部分，其中address为域名或IP，port为端口，users为UUID，根据实际情况修改填写即可：

```
{
  "inbounds": [{
    "port": 1080, 
    "listen":"127.0.0.1",
    "protocol": "socks",
    "settings": {
      "udp": true
        }
  }],
  "outbounds": [{
    "protocol": "vmess",
    "settings": {
     "vnext":[{
      "address":"www.xxx.xyz",
      "port":xxx,
      "users":[{"id":"xxx"}]
     }]
   }
  },{
    "protocol": "freedom",
    "settings": {},
    "tag": "direct"
  }],
  "routing": {
    "rules": [
      {
        "type": "field",
        "ip": ["geoip:private"],
        "outboundTag": "direct"
      }
    ]
  }
}
```

2. 修改完成后重启v2ray，分别执行以下命令：

   ```
   service v2ray stop
   service v2ray start
   # 查看一下是否启动成功
   service v2ray status
   ```

### mKCP协议

待补充...

## 浏览器配置

打开firefox浏览器（其他浏览器类似）的设置，网络代理那一块，修改为手动设置代理，IP填127.0.0.1，端口填1080，协议选择socks5（和上面配置文件中的inbounds的对应）

## 测试

1. 尝试登陆以下网站测试是否成功
   - <https://www.google.com/>
   - <https://www.youtube.com/>
   - <https://www.facebook.com/>
   - <https://twitter.com/>
   - <https://www.instagram.com/>
2. 成功后可以上Youtube打开一个1080P视频看看速度如何。

注：不同地方情况不同，如果连接WIFI测试不成功尝试切换成手机流量再试一试