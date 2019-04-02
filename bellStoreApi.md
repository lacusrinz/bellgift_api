# 贝尔商城接口

版本号 | 完成日期 |生效时间| 修改人 | 变更描述
---- | ------- | ----- | ----- | -------
1.0.1 | 2019.2.28 | 2019.2.28 15：00 | wdw | 1商品信息，2订单操作
1.0.2 | 2019.3.4 | 2019.3.4 12：00 | wdw | 3.Auth认证：sms/mobile login/wx register/wx login 
1.0.3 | 2019.3.4 | 2019.3.5 12：00 | wdw | 更新1.2（去掉hot）,1.1字段描述（specification） 删除1.3,添加banner
1.0.4 | 2019.3.5 | 2019.3.5 19：00 | wdw | 5.添加地址信息
1.0.5 | 2019.3.6 | 2019.3.6 14：20 | wdw | 6.添加购物车信息
1.0.6 | 2019.3.7 | 2019.3.8 10：00 | wdw | 1.1.添加优惠券信息（update）, 2.1显示下单商品信息,2.2下单(update),2.3取消订单（update), 2.5退换货图片上传 2.6退换货申请  5.6领取优惠券，5.7用户优惠券列表 
1.0.7 | 2019.3.12 | 2019.3.12 11：00 | wdw | 1.1 coupons中添加是否已领取 2.6可退换货列表  2.8退换货处理中列表 2.9退换货详情，2.4返回结果中添加 支付时间/完成时间/订单号
1.0.8 | 2019.3.20 | 2019.3.20 11：00 | wdw | 2.10 订单详情,2.4 2.6 2.8 
1.0.9 | 2019.3.29 | 2019.3.29 15：00 | wdw | 更新5.7 新增7.1
1.0.9 | 2019.3.29 | 2019.3.29 15：00 | wdw | 更新2.1,5.7 立即购买支持数组  更新2.4,2.6,2.8 新增resourceId

## API请求地址
#### http://182.92.3.98:4590
#### 请求头里面 token 身份认证
#### 返回 resultCode 为 0 时为正常调用


## 目录
[1.商品信息 (需登录)](#1)  
&nbsp; &nbsp; [ 1.1商品详情](#1.1)  
&nbsp; &nbsp; [ 1.2商品列表](#1.2)  

[2.订单操作（需登录）](#2)  
&nbsp; &nbsp; [ 2.1显示下单商品信息](#2.1)  
&nbsp; &nbsp; [ 2.2下单](#2.2)  
&nbsp; &nbsp; [ 2.3取消订单](#2.3)  
&nbsp; &nbsp; [ 2.4订单列表](#2.4)  
&nbsp; &nbsp; [ 2.5退换货图片上传](#2.5)  
&nbsp; &nbsp; [ 2.6可退换货列表](#2.6)  
&nbsp; &nbsp; [ 2.7退换货申请](#2.7)  
&nbsp; &nbsp; [ 2.8退换货处理中列表](#2.8)  
&nbsp; &nbsp; [ 2.9退换货详情](#2.9)  
&nbsp; &nbsp; [ 2.10订单详情](#2.10)

 

[3.AUTH (无需登录)](#3)   
&nbsp; &nbsp; [ 3.1wxUuid验证是否存在](#3.1)  
&nbsp; &nbsp; [ 3.2微信登录](#3.2)    
&nbsp; &nbsp; [ 3.3获取短信验证码](#3.3) 

[4.Banner (需登录)](#4)  
&nbsp; &nbsp; [ 4.1Banner列表](#4.1)  

[5.用户管理 (需登录)](#5)  
	&nbsp; &nbsp; [ 5.1地址添加](#5.1)  
	&nbsp; &nbsp; [ 5.2地址删除](#5.2)  
	&nbsp; &nbsp; [ 5.3地址修改](#5.3)   
  	&nbsp; &nbsp; [ 5.4地址列表](#5.4)   
	&nbsp; &nbsp; [ 5.5区域列表](#5.5)  
	&nbsp; &nbsp; [ 5.6优惠券领取](#5.6)  
	&nbsp; &nbsp; [ 5.7用户优惠券列表](#5.7)  

[6.购物车管理 (需登录)](#6)  
&nbsp; &nbsp; [ 6.1添加购物车](#6.1)  
&nbsp; &nbsp; [ 6.2查询购物车](#6.2)  
&nbsp; &nbsp; [ 6.3删除购物车](#6.3)  
&nbsp; &nbsp; [ 6.4更新购物车](#6.4)  

[7.邮费管理 (需登录)](#7)  
&nbsp; &nbsp; [ 7.1计算邮费](#7.1) 

# <h2 id='1'>1.商品信息 (需登录)</h2>
## <h3 id='1.1'>1.1商品详情</h3>
#### URL:   * /api/commodity/detail*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
commodityId **  | long | 商品id | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
data  | map | 见商品详情 | 
 
### 商品详情 
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
commodityId **  | long | 商品id | 1
subjectPicture |string | 主图 | http://qimg.hxnews.com/2019/0130/1548847547525.jpg
title |string | 名称 | 贴纸
subtitle |string | 副产品副标题（特点） | `自主品牌 | 包换包退 | 官方直售`
label |string | 主产品标签 | 课程配套教具
sales |int | 总销量 | 1234
activityTitle |string | 活动 | 下单即随机附送贝尔小礼物
showPrice |int | 产品价格,单位分 | 37800
context | string |商品描述 | `<p><img src="http://preqiniu.beecloud.cn/1dcc0d473dd1426087addf302fe4c2b5"/></p><p><span style="text-decoration: underline;">三扥结婚</span></p><ol class=" list-paddingleft-2" style="list-style-type: decimal;"><li><p>23</p><p>&nbsp; &nbsp; &nbsp;三扥看带坑距</p></li></ol><p>sdf<span style="color: rgb(118, 146, 60);">sdfsdf<span style="color: rgb(255, 255, 0);">dsfgdfg<span style="color: rgb(36, 64, 97);">dsg</span></span></span><br/></p><p><br/></p>` 
resources | array |见商品资源详情 | 
specifications |array |见产品参数 | 
colorNum| string | 色号| 颜色/尺寸等
coupons | array |见优惠券信息 |

### 商品资源详情 
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
type  | string | 名称 | 材质
value  | string | 值 | 毛绒

### 商品资源详情 
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
commodityId **  | long | 商品id | 1
price |int | 产品价格,单位分 | 37800
thumbnail |string | 缩率图 | http://qimg.hxnews.com/2019/0130/1548847547525.jpg
stock |int | 库存 | 2344
properties| string | 属性| 绿色

### 优惠券信息
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
couponId **  | long | 优惠券id | 125
title  | string | 名称 | 用于贝尔商城各类实物商品的购买。
describe | string | 说明 | 贝尔商城优惠券2
type  | string | 优惠券类型 | STORE
num  | int | 优惠金额 | 5000 分
fullPrice  | int | 满多少可减| 10000 分
startTime  | long | 优惠券可以使用的起始日期，毫秒| 1551369600000
endTime  | long | 优惠券可以使用的截止日期，毫秒 | 1553961600000
receive | boolean | 是否已领取 | false
 
            
## <h3 id='1.2'>1.2商品列表</h3>
#### URL:   * /api/commodity*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
limit | int |查询总数，默认20 | 否
skip | int | 分页用到 | 否
type | int | 商品列表必填,默认全部 STATIONERY/TOY | 否
sorts | array | 排序方式 | 否

### 排序方式
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
orderField | string | 排序方式，默认创建时间排序 PRICE/SALES/HOT | 否
orderType | string | 升序/降序，默认降序 ASC/DESC| 否

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
data  | map | 见data描述 |

### data描述
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
total  | long |总数 |
list  | array |商品列表，具体见商品概述 |

### 商品概述
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
commodityId **  | long | 商品id | 1
thumbnail |string | 缩率图 | http://qimg.hxnews.com/2019/0130/1548847547525.jpg
title |string | 名称 | 贴纸
subtitle |string | 副产品副标题（特点） | `自主品牌 | 包换包退 | 官方直售`
label |string | 主产品标签 | 课程配套教具
showPrice |int | 产品价格,单位分 | 37800
sales |int | 销量 | 100



# <h2 id='2'>2.订单操作 (需登录)</h2>
## <h3 id='2.1'>2.1显示下单商品信息</h3>
#### URL:   * /api/order/show *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
orders | array | 订单详情，描述见传入参数订单详情 | 立即购买必填
shoppingCartIds | array |购物车id列表 |购物车结算必填
shoppingCart | string |BUYNOW/SHOPPINGCART 购物车或者立即购买 |是

### 传入参数订单详情
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
commodityId | long | 商品id |立即购买必填
resourceId |long | 资源id |立即购买必填
num | int | 购买数量 | 立即购买必填

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
list  | array | 见商品描述 |  [{},{}] 
commodityId | long | 商品id |1
resourceId |long | 资源id |1
num | int |购买数量 | 2
shoppingCartIds | array |购物车id列表 | [1,2]
shoppingCart | string |BUYNOW/SHOPPINGCART | SHOPPINGCART

### 商品描述
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
commodityId  | long | 商品id  | 1
resourceId  | long | 资源 id  | 1
colorNum  | string |色号 | 颜色
shoppingCartId | long |购物车id | 1
title | string |名称 | 台湾weplay原装进口幼儿童早教平衡幼儿园感统教具豌豆荚豆荳夹
thumbnail | string |缩率图 | http://preqiniu.beecloud.cn/7077109cbc2e47a2bc4432ea00ca2792
properties | string |型号 | 红色
price | int |商品价格 | 23800
num | int |商品数量 | 1

## <h3 id='2.2'>2.2下单</h3>
#### URL:   * /api/order/create*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
addressId | long | 用户收件地址id | 是
shoppingCart | string |BUYNOW/SHOPPINGCART 直接购买/从购物车|是
source | string | 来源 | 否
remark | string |备注 | 否
couponIds | array |优惠券集合 | 否
commodityId| long |商品id | 直接购买必填
resourceId | long | 资源id |直接购买必填
num | int | 购买数量 | 直接购买必填
shoppingCartIds | array | 购物车ids | 从购物车购买时必填


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
orderNo | string | 订单号 | BSP9F4H5A7K688U0U8
payAmount | int |支付费用 | 29900
  
## <h3 id='2.3'>2.3取消订单</h3>
#### URL:   * /api/order/cancel *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
orderNo | string | 订单号 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----

## <h3 id='2.4'>2.4订单列表</h3>
#### URL:   * /api/order *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
orderStatus | string |订单状态 PAYING(待付款)/CANCEL(已取消)/PAID（待发货）/SENT（已发货）/COMPLETED（已完成） | 是
skip |int | 从第几条查询，默认0|否
limit| int |查询总数，默认20 | 否

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
total  | long |总数 | 10
list  | array |具体见商品列表 |

### 商品列表
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
orderNo | string |订单号 | BS3332L028Q9B952E3
payAmount  | int | 支付金额 |2000 
createTime | long | 订单创建时间 | 1551860588000
paidTime | long | 订单支付时间 | 1551860588000
finishTime | long | 订单完成时间 | 1551860588000
orderStatus | string |订单状态 | PAID
deliveryNo | string|物流号 | RSA723UIDE
deliveryName | string |物流名 |中通
name | string |收件人 | 小明
phone | string |收件人手机号 |123459087233
orderCommodities | array|见orderCommodities

### orderCommodities
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
commodityId | long | 商品id|2
resourceId | long | 资源id|12
title| string |标题 |贴纸
thumbnail|string |缩略图 |http://qimg.hxnews.com/2019/0130/1548847547525.jpg
colorNum |string |型号 |颜色
properties|string | 内容 | 百变方块
num| int |件数|4
price|long | 价格 | 233

## <h3 id='2.5'>2.5退换货图片上传</h3>
#### URL:   * /api/order/return/upload *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | string | token |是
file |file | 图片文件 |是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
url|string |图片上传地址 |http://preqiniu.beecloud.cn/9ff9ebb1555249028a7659a67f6f15a5


## <h3 id='2.6'>2.6可退换货列表</h3>
#### URL:   * /api/order/canreturn *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
data  | array |见商品列表 | 

### 商品列表
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
orderNo | string |订单号 | BS3332L028Q9B952E3
payAmount  | int | 支付金额 |2000 
createTime | long | 订单创建时间 | 1551860588000
paidTime | long | 订单支付时间 | 1551860588000
finishTime | long | 订单完成时间 | 1551860588000
orderStatus | string |订单状态 | PAID
deliveryNo | string|物流号 | RSA723UIDE
deliveryName | string |物流名 |中通
name | string |收件人 | 小明
phone | string |收件人手机号 |123459087233
orderCommodities | array|见orderCommodities

### orderCommodities
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
commodityId | long | 商品id|2
title| string |标题 |贴纸
thumbnail|string |缩略图 |http://qimg.hxnews.com/2019/0130/1548847547525.jpg
colorNum |string |型号 |颜色
properties|string | 内容 | 百变方块
num| int |件数|4
price|long | 价格 | 233

## <h3 id='2.7'>2.7退换货申请</h3>
#### URL:   * /api/order/return/apply *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
imgs | array | 图片链接|是
mobile |string | 申请人手机号 | 是
name | string | 申请人姓名 | 是
orderNo | string | 单号 |是
reason | string |退换货原因 |是
type | string |RETURN/EXCHANGE 退货/换货 |是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
## <h3 id='2.8'>2.8退换货处理中列表</h3>
#### URL:   * /api/order/return/dealing *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
status | string | 申请中/已完成:APPLYING/COMPLETED | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
data  | array |见商品列表 | 

### 商品列表
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
orderNo | string |订单号 | BS3332L028Q9B952E3
payAmount  | int | 支付金额 |2000 
createTime | long | 订单创建时间 | 1551860588000
finishTime | long | 订单完成时间 | 1551860588000
paidTime | long | 订单支付时间 | 1551860588000
orderStatus | string |订单状态 | PAID
deliveryNo | string|物流号 | RSA723UIDE
deliveryName | string |物流名 |中通
name | string |收件人 | 小明
phone | string |收件人手机号 |123459087233
orderCommodities | array|见orderCommodities


### orderCommodities
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
commodityId| long |商品id |1
resourceId | long | 资源id|12
title| string |标题 |贴纸
thumbnail|string |缩略图 |http://qimg.hxnews.com/2019/0130/1548847547525.jpg
colorNum |string |型号 |颜色
properties|string | 内容 | 百变方块
num| int |件数|4
price|long | 价格 | 233

## <h3 id='2.9'>2.9退换货详情</h3>
#### URL:   * /api/order/return/detail *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
orderNo | string | 订单号| 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
type |string | 退货/换货 RETURN/EXCHAGE | RETURN
imgs | array | 图片列表 | ["http://img3","http://img1", "http://img2"]
reason | string | 退货理由 | 不喜欢
phone | string | 申请手机号 | 15289765432
name | string | 申请人 | 小明
status | string | 申请状态 申请中APPLYING/申请通过PASS/处理完成COMPLETED| APPLYING
result | string | 申请结果 |

## <h3 id='2.10'>2.10订单详情</h3>
#### URL:   * /api/order/detail *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
orderNo | string | 订单号| 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
orderNo | string |订单号 | BS3332L028Q9B952E3
payAmount  | int | 支付金额 |2000 
createTime | long | 订单创建时间 | 1551860588000
paidTime | long | 订单支付时间 | 1551860588000
finishTime | long | 订单完成时间 | 1551860588000
deliveryNo | string|物流号 | RSA723UIDE
deliveryName | string |物流名 |中通
orderStatus | string |订单状态 | PAID
name | string |收件人 | 小明
phone | string |收件人手机号 |123459087233
city| String | 城市 | 工业园区
country| String | 国家 | 苏州市
province| String | 省份 | 江苏省
detail| String | 地址详情 | 纳米大学科技园
remark | String | 备注| 
totalNum | int | 购买商品总数 | 1
disAmount | int | 优惠金额，单位分| 0
freightCost | int | 邮费，单位分 | 2000
orderCommodities | array|见orderCommodities


### orderCommodities
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
commodityId| long |商品id |1
title| string |标题 |贴纸
thumbnail|string |缩略图 |http://qimg.hxnews.com/2019/0130/1548847547525.jpg
colorNum |string |型号 |颜色
properties|string | 内容 | 百变方块
num| int |件数|4
price|long | 价格 | 233

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


# <h2 id='3'>3. AUTH (无需登录)</h2>

## <h3 id='3.1'>3.1 微信wxUuid验证是否存在</h3>
#### URL:   */api/auth/wxuuidcheck*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
wxUuid | String | 微信wxUuid|是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
isHave | boolean | 是否存在 true:存在，false:不存在，需要授权后先获取手机号码|



## <h3 id='3.2'>3.2 微信登录</h3>
#### URL:   * /api/auth/wxlogin *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
wxUuid | String | 微信unionid | 是
avatar| String | 头像 | 否
city| String | 城市 | 否
country| String | 国家 | 否
province| String | 省份 | 否
sex| int | 性别 性别 0:女 1：男 | 否
mobile| String | 手机号码 | 1.8 false 未注册过必传
code| String | 手机验证码 | 1.8 false 未注册过必传
nickname | String | 昵称 | 否

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
token  | String | token | 79767d55b2544d2c8594fecf1c21fa15 
accountId  | long | 用户id | 123456 


## <h3 id='3.3'>3.3 获取短信验证码</h3>
#### URL:   * /api/auth/sms *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile | String | 手机号码|是

# <h2 id='4'>4.Banner (需登录)</h2>
## <h2 id='4.1'> 4.1Banner列表 </h3>
#### URL:   * /api/banner*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
bannerId ** | long | banner标识 |1
picture | string | 图片url|http://baidu.com.img1
link | string | link地址 |
type | string | 类型 | AD


# <h2 id='5'>5.地址管理 (需登录)</h2>
## <h2 id='5.1'> 5.1地址添加 </h3>
#### URL:   * /api/account/address/create *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
provinceId| long | 省id | 是
cityId| long | 市id | 是
countyId |long| 县id | 是
defaultAddress | long | 是否默认.1 默认|否
detail |string| 详细地址 |否
mobile |string| 手机号 | 是
name |string| 收件人 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


## <h2 id='5.2'> 5.2地址删除 </h3>
#### URL:   * /api/account/address/delete *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
addressId **| long | addressId | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


## <h2 id='5.3'> 5.3地址修改 </h3>
### URL:   * /api/account/address/edit *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
provinceId| long | 省id | 否
cityId| long | 市id | 否
countyId |long| 县id | 否
defaultAddress | long | 是否默认.1 默认| 否
detail |string| 详细地址 |否
mobile |string| 手机号 | 否
name |string| 收件人 | 否
addressId ** | long | addressId | 是
`推荐参数都填`

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


## <h2 id='5.4'> 5.4地址列表 </h3>
#### URL:   * /api/account/address/list *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
data | array |参见地址详情 | 

### 地址详情
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
addressId **| long | addressId | 4
provinceId| long | 省id | 410000
cityId| long | 市id | 411600
countyId |long| 县id | 411602
province| string | 省 | 河南省
city| string | 市 | 周口市
county | string | 县 | 川汇区
detail | string | 详细地址 | 周口某某庄
defaultAddress | long | 是否默认.1 默认| 1
mobile |string| 手机号 | 18230909090
name |string| 收件人 | wdw



## <h2 id='5.5'> 5.5区域列表 </h3>
#### URL:   * /api/account/region/list *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
data | array |参见区域详情 | 

### 区域详情
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
subRegions| array | 见区域详情 | 
code| long | 编号| 110000
name| string | 名称 | 北京

## <h2 id='5.6'> 5.6优惠券领取 </h3>
#### URL:   * /api/account/receive/coupon *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
couponId | long | 优惠券id|是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----

## <h2 id='5.7'> 5.7用户优惠券列表 </h3>
#### URL:   * /api/account/coupons *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
addressId | long | 地址id |必填
orders | array | 订单详情，描述见传入参数订单详情 | 立即购买必填
shoppingCartIds | array |购物车id列表 |购物车结算必填
shoppingCart | string |BUYNOW/SHOPPINGCART 购物车或者立即购买 |是


### 传入参数订单详情
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
commodityId | long | 商品id |立即购买必填
resourceId |long | 资源id |立即购买必填
num | int | 购买数量 | 立即购买必填

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
id | long | 优惠券id| 414
title| string | 名称|贝尔商城2
describe| string | 描述 |贝尔商城优惠券2
num |int |优惠金额（分）| 500
fullPrice|int |满多少可使用（分）| 1000
startTime|long |活动开始时间| 1551369600000
endTime|long |活动结束时间| 1553961600000
satisfyUseCoupon | boolean | 是否满足满减 | true

`satisfyUseCoupon目前根据商品总价判断。即使优惠券针对某个产品，单个商品不满足条件，但是总价满足即可使用`
 


# <h2 id='6'>6.购物车管理 (需登录)</h2>
## <h2 id='6.1'> 6.1添加购物车 </h3>
#### URL:   * /api/shopcart/add *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
commodityId| long | 商品id | 是
resourceId| long | 资源id | 是
num |int| 商品数量| 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


## <h2 id='6.2'> 6.2查询购物车 </h3>
#### URL:   * /api/shopcart/list *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
data | array |购物车信息 | 

### 购物车信息
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
shoppingCartId ** | long |购物车id | 3
commodityId| long | 商品id | 1
thumbnail | string | 缩率图 | http://qimg.hxnews.com/2019/0130/1548847547525.jpg
title | string | 标题 | 早教游戏55关百变方块智力拼图儿童动手动脑益智幼教玩具礼物
colorNum | string | 色号 | 颜色
resourceId | long | 标题 | 1
properties | string | 属性 | 百变方块
price | long | 售价 | 1600
num |int| 商品数量| 4


## <h2 id='6.3'> 6.3删除购物车 </h3>
#### URL:   * /api/shopcart/delete *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
shoppingCartIds ** | array | 购物车id列表 | 

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----

## <h2 id='6.4'> 6.4更新购物车 </h3>
#### URL:   * /api/shopcart/update *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
shopCartCommodities| array | 见购物车信息 |
 
### 购物车信息
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
shoppingCartId **| long | 购物车id | 是
num| int | 商品数量 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----

   
# <h2 id='7'>7.邮费管理 (需登录)</h2>
## <h3 id='7.1'>7.1计算邮费</h3>
#### URL:   * /api/postage/calculation *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
addressId  | long | 地址id | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
data  | int | 邮费 | 2000
 

  
 














 










 


      
   




