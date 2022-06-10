# 内置JAPI

地图内置japi插件的文档

网址 http://japi.war3rpg.top/  点击查看 可以收藏起来

仓库 https://github.com/w4454962/embedded-japi-plugin  可以随时获得文档的更新

lua交流 有需要的同学可以在群里讨论
旧群被封，新lua地图群1019770872

---

* 内置文档        阿七

* 域名/服务器维护  火鸟

* 服务器          天天RPG

---
内置lua引擎基于ydlua进行扩展, 请先阅读

* [ydlua引擎文档](lua-engine.md)
* [RSA加密算法](lua-rsa.md)
--- 
文档分类 所有接口都通用1.24e 1.26 1.27

* [Japi](Japi/_sidebar.md) 
* [Lua](Lua/_sidebar.md)
* [界面](Script/界面/_sidebar.md)
* [例子](Script/例子/_sidebar.md)
---

## 更新日志


内置1.48版本更新内容:
1. 新增 修改单位移动类型japi (刷新寻路视野飞行高度) * [点击这里](/1.48/修改单位移动类型)
2. 新增 修改单位碰撞体积大小japi (刷新寻路) [点击这里](/1.48/修改单位碰撞体积大小)
3. 新增 获取物品技能handle 的japi * [点击这里](/1.48/获取物品技能handle)
4. 新增 jass.message里 本地发布 物品命令 [*点击这里*](Script/例子/智能施法)
5. 修复 特效渲染， 必须在屏幕内的特效才会进行渲染
6. ui增强 FrameSetTexture 接口 可以修改SimpleTexture控件的图片
7. ui增强 FrameSetText 接口 可以修改SimpleString控件的文本
8. ui增强 FrameShow 接口 可以对Simple类型的控件使用 隐藏/显示原生ui
9. ui增强 FrameSetEnable 接口可以对 Simple类型的控件使用 屏蔽/恢复 事件
10. 新增 ui接口 获取框选按钮的japi 
11. 新增 ui接口 获取buff按钮的japi
12. 新增 ui接口 动态 绑定/解除 任意frame控件  在 原生魔兽ui simple类型控件下
13. 新增 ui接口 FrameIsShow 可以判断 simple/frame 控件是否显示
14. 新增 ui接口 获取左下角农民按钮的japi
15. 新增 ui接口 修改/获取 原生按钮贴图的japi
16. 新增 ui接口 修改/获取 Simple类型控件的 父控件
17. 新增 ui接口 获取技能按钮的 右下角ui接口
18. 新增 ui接口 获取技能按钮的 右下角数字文本控件ui接口
19. 重写 message.get_select_list() 从ui上进行异或获取框选单位 不会再有延迟了。

* [**1.48版本**](1.48/_sidebar)




---
内置1.47版本更新内容 
1. 新增 japi获取玩家11跟网易平台的uid接口
2. 新增 lua异步获取当前玩家选择单位列表
3. 新增 japi获取特效颜色的接口
4. 修复 japi设置特效颜色 ui设置模型颜色 接口的透明通道无效的问题
5. 新增 japi设置 单位、特效、ui模型 的 粒子缩放的接口
6. 新增 japi动态修改 ui frame控件 解锁、锁定 屏幕限制接口
7. 增强 所有特效接口都加一层类型保护， 防止填入错误的handle而崩溃，并隐藏渲染特效崩溃时提示
8. 修复 lua引擎 日志打印太长会崩溃的bug

* [**1.47版本**](1.47/_sidebar)


---
内置1.46版本更新内容
1. 新增 绑定特效接口
2. 新增 解除特效绑定接口
3. 修复 播放特效动画接口名字错误的问题 
4. 修复 获取ui文本控件宽高错误的bug
5. 增强 j2b加密的强度
6. 修复 先j2b再slk 部分地图丢失字符串的问题。
7. 修正 内置的api可以对simple控件设置位置 跟缩放
8. 重写 japi.FrameSetScale 使其对子控件生效
9. 修复 ui模型绑特效 绑点错误的bug
10. 去掉对xp支持， 放弃xp用户。
11. ui自动同步事件 进行合并 减少队列时长

 

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




