# Linux

当前只支持Ubuntu，其他的自行摸索..

## 使用说明

### 第一次安装过程

1. 安装shadowsocks

   ```
   sudo apt-get install python-gevent python-pip
   sudo pip install shadowsocks
   ```

2. 安装后需要对Shadowsocks进行配置，在/etc目录下新建shadowsocks.json文件，添加以下内容。

   ```
   {
   "server": "your server ip",
   "server_port": 15216,
   "local_address": "127.0.0.1",
   "local_port": 1080,
   "password": "your password",
   "method": "aes-256-cfb",
   "fast_open": true,
   "workers": 1
   }
   ```

   注意：server填我发的服务器IP，sever_port填端口号，local_address本地ip（127.0.0.1不改），local_part本地端口（1080不改），password填密码，method是加密方式（aes-256-cfb不改），其他不改保存。
   （如果权限不够不能保存，记得加sudo，即sudo vi shadowsocks.json)

3. 启动

   ```
   sslocal -c /etc/shadowsocks.json
   ```

   注意：启动后不要关闭终端。

4. 配置为全局代理

   1. 系统设置 >> 网络 >> 网络代理 >> 方法 >> 手动
   2. 最下面有一行 Socks主机，IP填入127.0.0.1,后面端口填：1080，然后点击应用到整个系统。
   3. 如果使用的是谷歌浏览器，则此时已经成功，可以进行测试了；如果是火狐浏览器：
      1. 打开浏览器的设置（有的翻译为：首选项）>> 滑到最下面的网络代理，点设置>>点手动代理设置>>下面有一行 Socks主机，IP填入127.0.0.1,后面端口填：1080 >>勾选：使用 SOCKS v5 代理 DNS>>然后点确定>>重启浏览器就可以了。
      2. 关闭的话，打开浏览器的设置（有的翻译为：首选项）>> 滑到最下面的网络代理，点设置>>选择：使用系统代理设置>> 然后点确定>>重启浏览器就可以了。

5. 使用完关闭

   1. 关闭第三步时打开的终端
   2. 关闭全局代理（否则此时无法正常上网）：系统设置 >> 网络 >> 网络代理 >> 方法 >> 自动  然后点击应用到整个系统。

### 已安装后使用

1. 启动

   ```
   sslocal -c /etc/shadowsocks.json
   ```

2. 配置为全局代理：系统设置 >> 网络 >> 网络代理 >> 方法 >> 手动，最下面有一行 Socks主机，IP填入127.0.0.1,后面端口填：1080，然后点击应用到整个系统。

3. 如果是火狐浏览器（chrome则不管此步）：

   1. 打开浏览器的设置（有的翻译为：首选项）>> 滑到最下面的网络代理，点设置>>点手动代理设置>>下面有一行 Socks主机，IP填入127.0.0.1,后面端口填：1080 >>勾选：使用 SOCKS v5 代理 DNS>>然后点确定>>重启浏览器就可以了。
   2. 关闭的话，打开浏览器的设置（有的翻译为：首选项）>> 滑到最下面的网络代理，点设置>>选择：使用系统代理设置>> 然后点确定>>重启浏览器就可以了。

4. 使用完关闭：参考上面

## 测试

1. 尝试登陆以下网站测试是否成功
   - <https://www.google.com/>
   - <https://www.youtube.com/>
   - <https://www.facebook.com/>
   - <https://twitter.com/>
   - <https://www.instagram.com/>
2. 成功后可以上Youtube打开一个1080P视频看看速度如何。

注：不同地方情况不同，如果连接WIFI测试不成功尝试切换成手机流量再试一试