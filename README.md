# 前端需求

## 前言

背景说明

app已经上线，现在需要做一个类似的web版本

https://apps.apple.com/cn/app/id1509047602

功能类似。页面做到响应式兼容 手机与ipad，pc。兼容chrome  火狐 和 Safari 最新版

https://sabaki.yichuanshen.de/web/  可以看看这个

```
简单描述，即web端 通过websocket 发送数据给服务器，服务器返回数据，渲染到web。web已经现有很多库。

https://github.com/SabakiHQ/Sabaki 

已经实现了通过本地进程通信方式完成核心功能

理论上只需要做成web版本，把进程通信 改成 websocket通信即可。
参考 https://sabaki.yichuanshen.de/web/
```







产品参考链接

http://www.19x19.com/

https://www.zbaduk.com/smartreview



围棋棋盘可参考 库 

https://github.com/SabakiHQ/Shudan

落子树可参考库

https://github.com/SabakiHQ/immutable-gametree

sgf解析库参考库

https://github.com/SabakiHQ/sgf

整体参考

https://sabaki.yichuanshen.de/web/



## 功能

### 对弈

1.用户选择ai 进行对弈，与ai一对一下棋

2.下完棋保存sgf棋谱到本地。

3.下完可以选择进行复盘

4.对弈可选显示胜利率

### 联棋对弈

1.选择对手ai，队友ai

2.开始对弈

3.其他同对弈。普通对弈是联棋的一种特殊情况，即无ai队友

### 自由分析

1.用户自己摆黑白子

2.ai会给出推荐位置，计算量。

3.绘制胜利率曲线图

4.保存sgf 包含分析数据

### sgf分析

1.加载sgf

2.播放sgf，如果sgf已经存在数据，则绘制 曲线图和选点（app里围棋识谱）

3.选择ai进行实时分析，通过ws与服务器通信，返回数据解析绘制图表

4.自己选点落子。（自由分析是sgf分析的特殊情况，即空sgf分析）

### 鹰眼功能

1.加载已经分析好的sgf

2.一次性计算出 最佳手，恶手，胜利率曲线，ai评分，标准差，方差等（算法暂定，我在研究）

3.sgf分析时候可以打开鹰眼功能，同步更新数据。

### 离线分析

1.用户上传sgf到服务器（服务器api未开发）

2.服务器分析

3.下载分析好的sgf （此时 用户可以播放改sgf查看复盘数据）

参考 https://katago.gitee.io/?id=1

## 付费部分

微信支付宝购买vip和游戏币



## 功能模块抽象

1.围棋棋盘 可以使用 preact库  https://github.com/SabakiHQ/Shudan

2.落子树 https://github.com/SabakiHQ/immutable-gametree

3.sgf解析 https://github.com/SabakiHQ/sgf

该库无法解析 lz 和kata标签，改标签非标准sgf。需要自己解析。

kata标签内容 参考 https://github.com/lightvector/KataGo/blob/master/docs/GTP_Extensions.md

解析规则 具体细节问我

4.websocket 通信

下棋，复盘均使用ws通信，web与服务器使用gtp命令进行通信。

gtp命令参考 https://www.lysator.liu.se/~gunnar/gtp/ 不懂问我

5.鹰眼算法

待定

