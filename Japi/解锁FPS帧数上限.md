
# 解锁FPS帧数上限
```jass
function UnlockFps takes boolean is_unlock returns nothing
```
# 描述
解锁帧数上限 突破60帧


# 参数
类型|名字|说明
--|--|--
布尔值|is_unlock| 填true解锁 填false恢复


# 例子

```jass

call UnlockFps(true)

```

```lua
local japi = require 'jass.japi'

japi.UnlockFps(true)

```

