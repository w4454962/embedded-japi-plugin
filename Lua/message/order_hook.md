# 本地命令的捕获跟屏蔽  

### 返回nil 或者 false 可以屏蔽本地命令的发出

* 可以用来做 不打断的失控
* 可以让 主动技能 不能施法 变成被动技能
* 可以屏蔽玩家丢弃物品 或者 移动物品操作

```lua
    local message = require 'jass.message'
    local japi = require 'jass.japi'

    local event_map = {

        --本地发布无目标命令
        ['order_immediate'] = function (unit_handle, info)
            --当框选一群单位发布命令时 flag 会变化
            local name, order_id, unknow, flag = table.unpack(info)
            

            return true
        end,

        --本地发布点命令
        ['order_point'] = function (unit_handle, info)
            --当框选一群单位发布命令时 flag 会变化
            local name, order_id, unknow, x, y, flag = table.unpack(info) 
          
            
            return true
        end,

        --本地发布目标命令
        ['order_target'] = function (unit_handle, info)
            --当框选一群单位发布命令时 flag 会变化
            --当对地面发布命令时 handle 为0
            local name, order_id, unknow, x, y, handle, flag = table.unpack(info) 
          
            
            return true
        end,

        --本地右键单位发布命令
        ['order_smart'] = function (unit_handle, info)
            --当框选一群单位发布命令时 flag 会变化
            local name, order_id, unknow, handle, flag = table.unpack(info) 

            return true
        end,

        --本地物品丢弃事件
        ['order_discard'] = function (unit_handle, info)
            local name, order_id, unknow, x, y, unit, handle, flag = table.unpack(info) 

            return true
        end,

    }

    function message.order_hook(info)
        local unit_handle = japi.GetRealSelectUnit() 
        local event = event_map[info[1]]
        if event then 
            return event(unit_handle, info)
        end 
        return true 
    end

```