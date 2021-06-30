# 内置JAPI

地图内置japi插件的文档
网址 http://japi.war3rpg.top/  点击查看 可以收藏起来

魔兽lua地图 QQ群 692125060 有需要的同学可以在群里讨论

~~

---

内置japi 2016-2021

---
内置lua引擎基于ydlua进行扩展, 请先阅读

* [ydlua引擎文档](https://github.com/actboy168/jass2lua/blob/master/lua-engine.md)

---
关注 https://github.com/w4454962/embedded-japi-plugin 仓库 可以随时获得文档的更新

--- 
文档分类 所有接口都通用1.24e 1.26 1.27

* [Japi](Japi/_sidebar.md) 
* [Lua](Lua/_sidebar.md)
* [界面](Script/界面/_sidebar.md)

---



---
内置1.45版本更新内容
1. 新增 播放ui模型字符串动画
2. 新增 获取ui模型所有动画名 动画时长
3. 新增 添加ui模型绑点特效
4. 新增 移除ui模型绑点特效
5. 新增 播放 特效handle 的字符串名动画
6. 优化 ui滚动面板的效率
7. 修复 获取ui模型z轴 api错误的bug

---


---
内置1.44版本更新内容
1. 新增 获取frame 父控件（[点击查看](1.44/获取父控件)） 以及 遍历子控件的api （[点击查看](1.44/获取子控件)） 
2. 新增 新的3d ui模型控件 以及一系列api   （[点击查看](Script/界面/模型2)）
3. 新增 设置控件显示视口的方法 可以做遮罩 滚动面板 （[点击查看](1.44/设置控件视口)）
4. 新增 获取当前魔兽 是否窗口化（[点击查看](1.44/获取是否窗口化模式)）， 设置窗口大小 （[点击查看](1.44/设置窗口大小)）
5. 新增 获取当前鼠标指示器状态  （[点击查看](Lua/message/目标指示器)）
6. 新增 获取商店选择玩家的单位 （[点击查看](1.44/获取商店目标)）
7. 修复 部分用户 j2b加密时崩溃的bug
---




## 本地启动

本项目依赖nodejs，npm，[docsify](https://docsify.js.org/)。

```bash
npm i docsify-cli -g
docsify serve
```




