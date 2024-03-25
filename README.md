# chatGPT_Wechat

如今各类chatGPT衍生产品已经够多了，为何还要在微信里跑一个呢？

主要是爱折腾啊。微信里藏个AI还是挺方便的。

![](/img/8554040404524076021.jpg)

## 准备
* 一个微信小号（这意味着，你必须要有不少于两个微信）
* 一台运行在家里或者公司的Linux。
* [申请个免费chatGPT Token](https://github.com/chatanywhere/GPT_API_free)。

## 运行

1. 先别急着运行，看看环境要求
```
$ docker-compose version
Docker Compose version v2.20.2

$ docker version
Client: Docker Engine - Community
 Version:           24.0.7
```
2. 请使用不重要的微信小号扫码登录，以免封号给您带来损失。
3. 请勿在云服务器上折腾，以免微信封号。
4. 请不要在重要服务器上升级docker。
5. 最新版compose[下载地址](https://github.com/docker/compose/releases) 注意不能选低于我的版本的。
6.
  ```
 git clone https://github.com/77409/chatGPT_Wechat.git
 cd chatGPT_Wechat
docker network create e4ting --subnet=172.24.0.0/24 -o com.docker.network.bridge.name=e4ting
docker-compose up
```
7. 用不重要的`微信小号`扫码登录。

## 使用
- 这个微信（机器人）被人`拍一下`，就会自动开始应答对方的`文字`消息。
- 关闭回复也是`拍一下`。

## 几个重要环境变量的用法
- `LOGIN_API_TOKEN=x1233456`                     # 尽量换掉，以免不安全
- `HTTPS_PROXY=http://xxx:xxx@127.0.0.1:8080`    # 配置代理，不是必须的
- `API_KEY=sk-Eulduu4sllVkevjK23s4Z6GO9PBzkdYQmPdStp9FItavfdD7`  # chatGPT的token，可以用我的，也可以去[这里](https://github.com/chatanywhere/GPT_API_free)申请个免费的
- `BASE_URL=https://api.chatanywhere.tech/v1`                    # chatGPT的代理地址，不必改它
- `AUTO_REPLAY=start`   # start/stop , stop : 不会调用chatGPT做任何回复

改完后记得执行一下
```
docker-compose up -d api
```

## 常见报错
1. docker直接报compose文件语法错误；
    这说明你的docker版本太低了，里面有些语法，低版本docker不支持。
2. 如果报错`httpcore.ConnectTimeout: _ssl.c:989: The handshake operation timed out`
    可能还是需要设置代理，尝试设置下`HTTPS_PROXY`。
    使用clash的朋友注意下，如果持续报错，尝试切换到美国线路。

## 特别感谢

* https://github.com/chatanywhere/GPT_API_free 提供的免费Token
* https://github.com/danni-cool/wechatbot-webhook 开发的微信API
