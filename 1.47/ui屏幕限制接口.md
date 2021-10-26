
# ui屏幕限制接口
```jass
function SetFrameLimitScreen takes boolean is_limit returns nothing 

```
# 描述
内置默认是 解锁frame控件的 屏幕限制的 就是可以随便移动到屏幕之外的位置， 但是有个别用户  依赖这个限制 用网易的接口写了ui 导致加了内置之后 位置变了， 故此新增这个接口 自行决定是否解锁。
# 参数
类型|名字|说明
--|--|--
布尔值|is_limit| 填true 是锁定  填false 是解锁


# 例子

```jass

call SetFrameLimitScreen(true) //重新锁定
```


```lua


local japi = require 'jass.japi'

japi.SetFrameLimitScreen(true) //重新锁定

```

