# lua引擎里的RSA算法

## 描述
ydlua内置了一套 sha1算法 以及 rsa算法 这篇文字教你们如何使用。


先看以下代码

```lua

local bignum = require "jass.bignum"

local rsa = {}

-- RSA公钥
rsa.e = "00010001"
rsa.n = "A6040BC5737510DFF2E4DF965D50338855E151AABF8DE41854B129F862438DB933427C7006210C6B73A4846C2422C490808A45E1119FC5DEE4F9B8AC9B0657D65CBB09BC1B3E71872F998A307542BF9F5D31C8559EB070128805D8C75E3D0F7604C9A3DD7B37A87A8746F7F92678198946A46F22ED60987B6110D4382EB4EB6D8B857216CD5CFBF5F396D6E19D2B4E140AAF850E3EDC0851E47B83F7678D1F706CE4A15B11205540811DE28EFA1426C2CB4F1A35C4256AB5AFEAA32FAB25675334530D8B8ACA71AD8AD3ED4B3B02895F4CEEA7F97B2E6E41655262147D5D5A7ED69E4E7D4A132691E1BD8728F648DE468787312A62DA4DFC5E3DC008F6A87CB1"

-- RSA私钥
local suc, key = pcall(require, '(ppk)')
rsa.d = suc and key

function rsa:init()
    if self.e then self.e_bn = bignum.new(bignum.bin(self.e)) end
    if self.n then self.n_bn = bignum.new(bignum.bin(self.n)) end
    if self.d then self.d_bn = bignum.new(bignum.bin(self.d)) end
end

function rsa:encrypt(c)
    local c_bn = bignum.new(c)
    local m_bn = c_bn:powmod(self.e_bn, self.n_bn)
    return tostring(m_bn)
end

function rsa:decrypt(m)
    local m_bn = bignum.new(m)
    local c_bn = m_bn:powmod(self.d_bn, self.n_bn)
    return tostring(c_bn)
end

rsa:init()

local sha1 = bignum.sha1

--生成签名
--	文本
function rsa:get_sign(content)
	return self:decrypt(sha1(content))
end

--验证签名
--	文本
--	签名
function rsa:check_sign(content, sign)
	return sha1(content) == self:encrypt(sign)
end

```

上面这段代码 是 英萌里原本的例子 现在教你们如何使用这段代码

    rsa.e = 公钥指数

    rsa.n = 公钥模数 

    rsa.d = 私钥指数

在上面的代码中 公钥部分 是放在代码里 可以被公开的部分   用来验证的

私钥是放在自己安全的环境里 不开放给别人知道的


## rsa的加密方法如下 
    1. 使用 公钥指数 + 私钥指数  在自己的电脑或服务器上 对源文进行加密 得到密文
    2. 将密文保存传输
    3. 对方的电脑上  使用 公钥指数 + 公钥模数  对密文进行解密 得到源文


## 由于上面的 私钥并没有开放  故此我们可以自己生成一套 自己的 公私钥来做数据加密 验签

1. 先下载安装 openssl   32/64位都可以 下载地址 http://slproweb.com/products/Win32OpenSSL.html
2. 在安装目录里 bin/目录下 新建一个 make.bat
3. 在bat里编辑以下内容后保存运行

```
  openssl genrsa -out private_rsa.pem 1024

  openssl rsa -in private_rsa.pem -text -out private.txt

```

4. 打开运行后生成的 private.txt  这个文件保存了公私钥 如果使用记得自己保存好，不要丢失外放

5. 打开后 

    modulus: 下面的内容 就是  公钥模数   去掉 第一个00 再去掉空格换行冒号 就可以放在 最上面 rsa.n 的代码里

    publicExponent: 右边括号里 去掉0x  再补 3个0 就可以放到上面的 rsa.e里

    privateExponent: 下面的内容 就是 私钥指数  去掉空格换行冒号 就可以放在 最上面的 rsa.d 里 不过私钥 不能对外开放 不能随着代码一起发出， 切记小心。




