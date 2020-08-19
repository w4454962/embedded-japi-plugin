# jass.code 跟jass进行交互 

jass里面 有2种函数  

* 1是 native 在common.j 里的接口 简称cj  
* 2是 blizzard.j 以及war3map.j 里的 自定义函数 简称bj


### lua调用cj 
* 原ydlua 功能

```lua
    local jass = require 'jass.common'

    jass.DisplayTextToPlayer(jass.Player(0), 0, 0, "hello world!")
```


### 重载cj jass调用lua  
* 原ydlua 功能 

* 由于cj 参数类型 参数数量 返回值 都是固定的 不便做扩展

```lua
    local jass = require 'jass.common'
    local hook = require 'jass.hook'

    local DisplayTextToPlayer = DisplayTextToPlayer
    function hook.DisplayTextToPlayer(player, x, y, msg)
        print(player, x, y, msg)
        DisplayTextToPlayer(player, x, y, msg)
    end
```

### 遍历cj 函数
* 原ydlua 功能 

```lua
    local jass = require 'jass.common'
    for name, func in pairs(jass) do 
        print(name, func)
    end

```

### lua调用bj 
* 内置lua 功能
* 要注意优化混淆j文件后的名字

```lua
    local code = require 'jass.code'

    code.BJDebugMsg("hello world!")

```

### 重载bj jass调用lua
* 内置lua 功能
* bj可以自定义扩展参数类型 参数数量 
* 要注意优化混淆j文件后的名字

```jass
    function add takes integer a, integer b returns integer 
        call GetTriggeringTrigger() //随便调用一句jass 防止 空函数被jass虚拟机内联优化掉
        return 0
    endfunction

    function test takes nothing returns nothing
        call BJDebugMsg(I2S(add(10, 20)))
    endfunction
```

```lua
    local code = requore 'jass.code'

    function code.add(a, b)
        return a + b
    end 

    function code.BJDebugMsg(msg)
        print(msg)
    end 


    code.test() --控制台将会输出 30 而游戏内屏幕不会打印。

```

### 遍历bj 函数
* 内置lua 功能

```lua
    local code = require 'jass.code'
    for name, func in pairs(code) do 
        print(name, func)
    end

```