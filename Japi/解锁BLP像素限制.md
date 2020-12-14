
# 解锁BLP像素限制
```jass
function UnlockBlpSize takes boolean is_unlock returns nothing
```
# 描述
解锁blp贴图的像素上限 原本魔兽高清图片也会被限制在512p之内


# 参数
类型|名字|说明
--|--|--
布尔值|is_unlock| 填true解锁 填false恢复


# 例子

```jass

call UnlockBlpSize(true)

```

```lua
local japi = require 'jass.japi'

japi.UnlockBlpSize(true)

```

