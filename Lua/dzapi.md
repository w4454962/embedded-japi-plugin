# jass.dzapi 网易平台的接口

注意 本地要有平台插件 或者平台环境才能使用。

### 接口 

* 支持注册闭包回调
* 支持jass.hook 对dzapi 进行hook 重载

```lua
    local dzapi = require 'jass.dzapi'

    --异步鼠标移动事件
    dzapi.DzTriggerRegisterMouseMoveEventByCode(nil, false, function ()
        print(dzapi.DzGetMouseXRelative(), dzapi.DzGetMouseYRelative())
    end)

```

### 部分接口封装

```lua
    local dzapi = require 'jass.dzapi'
    local japi = requore 'jass.japi'

    
    ---设置 ${player} 的 ${option} 号平台功能为 ${enable}  
    ---1,锁定视距 2,显血/显蓝 3,智能施法
    rawset(dzapi,'DzAPI_Map_EnablePlatformSettings',function(whichPlayer,option,enable)
        return japi.RequestExtraBooleanData(43, whichPlayer, null, null, enable, option, 0, 0)
    end)

    ---使用商城道具（次数型）  
    ---使用 ${player} 名称 ${key} 的商城道具 ${value} 次  
    ---仅对次数消耗型商品有效，只能使用不能恢复，请谨慎使用
    rawset(dzapi,'DzAPI_Map_ConsumeMallItem',function(whichPlayer,key,count)
        return japi.RequestExtraBooleanData(42, whichPlayer, key, null, false, count, 0, 0)
    end)

    ---未知(推测是获取商城消耗类道具数量)
    rawset(dzapi,'DzAPI_Map_GetMallItemCount',function(whichPlayer,key)
        return japi.RequestExtraIntegerData(41, whichPlayer, key, null, false, 0, 0, 0)
    end)

    ---读取玩家服务器存档成功
    rawset(dzapi,'GetPlayerServerValueSuccess',function(whichPlayer)
        if(dzapi.DzAPI_Map_GetServerValueErrorCode(whichPlayer)==0)then
            return true
        else
            return false
        end
    end)

    ---获取玩家中游戏局数
    rawset(dzapi,'DzAPI_Map_PlayedGames',function(whichPlayer)
        return japi.RequestExtraIntegerData(45, whichPlayer, null, null, false, 0, 0, 0)
    end)

    ---评论次数(调用DzAPI_Map_CommentTotalCount)
    rawset(dzapi,'DzAPI_Map_CommentCount',function(whichPlayer)
        return japi.RequestExtraIntegerData(51, null, null, null, false, 0, 0, 0)

    end)

    ---好友数量
    rawset(dzapi,'DzAPI_Map_FriendCount',function(whichPlayer)
        return japi.RequestExtraIntegerData(47, whichPlayer, null, null, false, 0, 0, 0)

    end)

    ---鉴赏家
    rawset(dzapi,'DzAPI_Map_IsConnoisseur',function(whichPlayer)
        return japi.RequestExtraBooleanData(48, whichPlayer, null, null, false, 0, 0, 0)

    end)

    ---战网账号
    rawset(dzapi,'DzAPI_Map_IsBattleNetAccount',function(whichPlayer)
        return japi.RequestExtraBooleanData(49, whichPlayer, null, null, false, 0, 0, 0)

    end)

    ---本图作者
    rawset(dzapi,'DzAPI_Map_IsAuthor',function(whichPlayer)
        return japi.RequestExtraBooleanData(50, whichPlayer, null, null, false, 0, 0, 0)

    end)

    ---获取该图总评论次数
    rawset(dzapi,'DzAPI_Map_CommentTotalCount',function(whichPlayer)
        return japi.RequestExtraIntegerData(51, null, null, null, false, 0, 0, 0)

    end)

    ---"平台统计： ",whichPlayer,"，埋点key：",eventKey,"，子key：",不填,"，次数 ",value  
    ---"一般用于统计游戏里某些事件的触发次数，可在作者之家查看。【第二个子key是以后备用暂时不要填】"
    rawset(dzapi,'DzAPI_Map_Statistics',function(whichPlayer,eventKey,eventType,value)
        japi.RequestExtraBooleanData(34, whichPlayer, eventKey, "", false, value, 0, 0)
    end)

    ---是否回流/收藏过地图的用户  
    ---2,当前是平台回流用户 8,当前是地图回流用户 16,收藏过地图 1,曾经是平台回流用户 4,曾经是地图回流用户
    rawset(dzapi,'DzAPI_Map_Returns',function(whichPlayer,label)
        return japi.RequestExtraBooleanData(53, whichPlayer, null, null, false, label, 0, 0)
    end)

    ---签到系统  
    ---0,总签到天数 1,最高连续签到天数 2,连续签到天数
    rawset(dzapi,'DzAPI_Map_ContinuousCount',function(whichPlayer,id)
        return japi.RequestExtraIntegerData(54, whichPlayer, null, null, false, id, 0, 0)
    end)

    ---是玩家
    rawset(dzapi,'DzAPI_Map_IsPlayer',function(whichPlayer)
        return japi.RequestExtraBooleanData(55, whichPlayer, null, null, false, 0, 0, 0)
    end)


```