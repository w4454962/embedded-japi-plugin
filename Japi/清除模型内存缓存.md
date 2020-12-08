
# 清除模型内存缓存
```jass
function ReleaseModel takes string model_path returns nothing
function ReleaseAllModel takes nothing returns nothing
function GetCacheModelCount takes nothing returns integer

```
# 描述

用来清空魔兽的模型文件缓存 降低内存占用
直到下一次读取 才会重新占用。


# 例子

```jass
call ReleaseModel("xxx.mdx")
```

```lua
local japi = require 'jass.japi'

if japi.GetCacheModelCount() > 100 then 
    japi.ReleaseAllModel()
end 
```

