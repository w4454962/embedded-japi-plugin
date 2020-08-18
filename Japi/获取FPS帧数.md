
# 获取FPS帧数
```jass
function GetFps takes nothing returns real
```
# 描述
异步获取 玩家当前的帧数  
玩家比较卡时 帧数较低 可以异步空特效路径 以及 弹道模型 屏蔽特效来提高帧数。

# 返回值
类型|说明
--|--
实数|注意返回是异步的切记小心使用


# 例子

```jass

local real fps = GetFps()

```

```lua
local japi = require 'jass.japi'

local fps = japi.GetFps() 

```

