
# 新增ui接口
```jass

// 获取 框选按钮 slot 从0 ~ 11 
function FrameGetInfoSelectButton takes integer slot returns integer 

// 获取 下方buff按钮 slot 从0 ~ 7 
function FrameGetBuffButton takes integer slot returns integer 

// 获取 农民按钮 
function FrameGetUnitButton takes nothing returns integer 

// 获取 技能右下角数字文本控件 button = 技能按钮  返回值 = SimpleString 类型控件
function FrameGetButtonSimpleString takes integer button returns integer 

// 获取 技能右下角控件  button = 技能按钮  返回值 = SimpleFrame 类型控件
function FrameGetButtonSimpleFrame takes integer button returns integer 


// 判断控件是否显示
function FrameIsShow takes integer frame returns boolean 


// 修改/获取 原生按钮图片 button 可以是 技能按钮 物品按钮 英雄按钮 农民按钮 框选按钮 buff按钮
function FrameSetOriginButtonTexture takes integer button, string path returns nothing 

function FrameGetOriginButtonTexture takes integer button returns string 


// 修改/获取 simple类型控件的 父控件
function FrameGetSimpleParent takes integer SimpleFrame returns integer
function FrameSetSimpleParent takes integer SimpleFrame, integer parentSimple returns integer


// 为Simple绑定 frame类型的子控件
// 可以将任意frame类型 绑定到 原生ui下面 返回值 可以解除绑定
// 返回的是一个 SetupFrame值
function FrameSimpleBindFrame takes integer SimpleFrame, integer Frame returns integer 

// 解除绑定 解除后 frame跟simple 就不再关联
function FrameSimpleUnBindFrame takes integer SetupFrame returns nothing


```
# 描述
下面有个lua的例子


```lua


ac.game:event '玩家-聊天' (function (_, player, str)

    local frame 

    for i = 0, 7 do 
        frame = japi.FrameGetBuffButton(i)
        --print('buff按钮图标', japi.FrameGetOriginButtonTexture(frame))
        japi.FrameSetOriginButtonTexture(frame, "core\\texture.blp")
    end 


    --技能12个按钮
    for y = 0, 3 do 
        for x = 0, 2 do 
            frame = japi.FrameGetCommandBarButton(x, y)
            if frame > 0 then 
                local texture = japi.FrameGetOriginButtonTexture(frame)
                --print('技能图标', x, y, texture)
                --japi.FrameSetOriginButtonTexture(frame, "core\\texture.blp")
            end 
        end 
    end 

    local a = 0
    --物品6个按钮
    for i = 0, 5 do 
        frame = japi.FrameGetItemBarButton(i)
        if frame > 0 then 
            local texture = japi.FrameGetOriginButtonTexture(frame)
            --print('物品图标', i, texture)
            japi.FrameSetOriginButtonTexture(frame, "core\\texture.blp")
        end 
    end 



    --框选单位12个按钮
    for i = 0, 11 do 
        frame = japi.FrameGetInfoSelectButton(i)
        if frame > 0 then 
            local texture = japi.FrameGetOriginButtonTexture(frame)
            --print('框选图标', i, texture)
            japi.FrameSetOriginButtonTexture(frame, "core\\texture.blp")
        end 
    end 

    --英雄头像6个按钮
    for i = 0, 5 do 
        frame = japi.FrameGetHeroBarButton(i)
        if frame > 0 then 
            local texture = japi.FrameGetOriginButtonTexture(frame)
            --print('英雄图标', i, texture)
            japi.FrameSetOriginButtonTexture(frame, "core\\texture.blp")
        end 
    end 

    --农民头像按钮
    local frame = japi.FrameGetUnitButton()
    if frame > 0 then 
        local texture = japi.FrameGetOriginButtonTexture(frame)
       -- print('农民图标', texture)
        japi.FrameSetOriginButtonTexture(frame, "core\\texture.blp")
    end 


    --攻击按钮
    local attack = japi.SimpleTextureFindByName("InfoPanelIconBackdrop", 0)
    japi.FrameSetOriginButtonTexture(attack, "core\\texture.blp")

    --护甲按钮
    local armor = japi.SimpleTextureFindByName("InfoPanelIconBackdrop", 2)
    japi.FrameSetOriginButtonTexture(armor, "core\\texture.blp")
  
    --英雄属性按钮
    local attr = japi.SimpleTextureFindByName("InfoPanelIconHeroIcon", 6)
    --local texture = japi.FrameGetOriginButtonTexture(frame)
    --print('图标',  texture)
    japi.FrameSetOriginButtonTexture(attr, "core\\texture.blp")

end)



```