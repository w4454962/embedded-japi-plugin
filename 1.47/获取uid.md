
# 获取uid
```jass
function GetUserId takes nothing returns integer 

function GetUserIdEx takes nothing returns string 

```
# 描述
异步获取 当前玩家在11或网易平台游戏时的uid， 本地返回0

返回值是异步的 建议先同步后再使用

这2个接口一般情况下 返回值都是一致的 有万分之一局的概率 2个接口会返回不一致， 自己验证使用吧。

# 返回值
类型|说明
--|--
integer|整数类型uid 
string|字符串类型uid 


# 例子

```jass

local string strId = GetUserIdEx()

local integer uid = GetUserId()

```

```lua


local japi = require 'jass.japi'


local strId = japi.GetUserIdEx()

local uid = japi.GetUserId()

```

