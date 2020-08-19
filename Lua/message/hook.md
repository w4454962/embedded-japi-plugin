
# 异步事件的hook 

### 返回nil 或者 false 可以屏蔽事件


```lua

    local event_map = {

        --异步选择单位事件 该事件只是捕获大头像变化 不能屏蔽 用来做UI刷新用的
        ['select_unit'] = function (msg)
            local handle = msg.unit 
        
            return true
        end,

        --补充了原本ydlua 没有右键单位事件
        ['mouse_down'] = function (msg) --鼠标在 按下 单位或地面时
            local code = msg.code   -- 左键为 1  右键为 4
            local x, y = msg.x, msg.y --鼠标世界坐标


            return true 
        end,

        ['mouse_up'] = function (msg) --鼠标弹起

            return true 
        end,



        ['mouse_item'] = function (msg) --当鼠标点击物品按钮事件
            local ability_id = msg.ability 
            local order_id = msg.order

            return true
        end,


        ['mouse_ability'] = function (msg) --当鼠标点击技能按钮事件
            local ability_id = msg.ability 
            local order_id = msg.order

            return true
        end,



        ['key_down'] = function (msg) --键盘按下事件  不会跟聊天框冲突 
            local code = msg.code --整数 键码 

            local state = msg.state -- 默认为0  判断组合键用 alt + 字母键 时  为 4  当 ctrl + 字母键时 为 2 

            --修改 msg.code 可以进行改键
            msg.code = code 

            return true
        end,

        ['key_up'] = function (msg) --键盘弹起事件  不会跟聊天框冲突 
            local code = msg.code --整数 键码 

            local state = msg.state -- 默认为0  判断组合键用 alt + 字母键 时  为 4  当 ctrl + 字母键时 为 2 

            --修改 msg.code 可以进行改键
            msg.code = code 
            
            return true
        end,
    }
    function message.hook(msg)
        local info = event_map[msg.type]

        if info then 
            return info(msg)
        end
        return true 
    end

```