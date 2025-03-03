# lcsv
lua bindings for csv.

# 依赖
- [lua](https://github.com/xiyoo0812/lua.git)5.3以上
- [luakit](https://github.com/xiyoo0812/luakit.git)一个luabind库
- [tinyxml2](https://github.com/leethomason/tinyxml2)，源码已经包含在内
- 项目路径如下<br>
  |--proj <br>
  &emsp;|--lua <br>
  &emsp;|--lcsv <br>
  &emsp;|--luakit

# 接口说明
```lua
local csv = require("lcsv")
--编码
--value: 输入的lua table
--res：输出csv字符串
--err：错误信息
local res, err = csv.encode(value)

--解码
--value: 输入的csv字符串
--res：输出lua
local res = csv.decode(value)

--保存到文件
--csvfile: 保存的csv文件名
--value: 输入的lua
--res：成功或者失败
local ok = csv.save("./bb.csv", xxlua)

--从文件读取
--csvfile: 读取的csv文件名
--res：输出csv字符串
--err：错误信息
local flua, ferr = csv.open("./bb.xml")

```

# 用法参考
```lua
--本示例使用了quanta引擎
--https://github.com/xiyoo0812/quanta.git

--csv_test.lua
--luacheck: ignore 631

require("lcsv")

local log_dump  = logger.dump

local csvdata = [[
a,b,c,d
1,2,,4
5,6,,8
]]

local xlua = csv.decode(csvdata, 1)
log_dump("lcsv decode csv:{}",  xlua)

local yxml = csv.encode(xlua)
log_dump("lcsv encode csv:{}", yxml)

local ok = csv.save("./bb.csv", xlua)
log_dump("lcsv save csv:{}", ok)

local flua = csv.read("./bb.csv")
log_dump("lcsv read csv:{}", flua)

```
