# 贝尔商城接口

版本号 | 完成日期 |生效时间| 修改人 | 变更描述
---- | ------- | ----- | ----- | -------
1.0.1 | 2019.2.28 | 2019.2.28 15：00 | wdw | 1商品信息，2订单操作
1.0.2 | 2019.3.4 | 2019.3.4 12：00 | wdw | 3.Auth认证：sms/mobile login/wx register/wx login 
1.0.3 | 2019.3.4 | 2019.3.5 12：00 | wdw | 更新1.2（去掉hot）,1.1字段描述（specification） 删除1.3,添加banner

## API请求地址
#### http://182.92.3.98:4590
#### 请求头里面 token 身份认证
#### 返回 resultCode 为 0 时为正常调用


## 目录
[1.商品信息 (需登录)](#1)  
 &nbsp; &nbsp; [ 1.1商品详情](#1.1)  
 &nbsp; &nbsp; [ 1.2商品列表](#1.2)  
 
[2.订单操作（需登录）](#2)  
&nbsp; &nbsp; [ 2.1下单](#2.1)  
&nbsp; &nbsp; [ 2.2取消订单](#2.2)  
&nbsp; &nbsp; [ 2.3订单列表](#2.3)  

[3.AUTH (无需登录)](#3)  
 &nbsp; &nbsp; [ 3.1获取短信验证码](#3.1)  
 &nbsp; &nbsp; [ 3.2手机登录](#3.2)   
 &nbsp; &nbsp; [ 3.3微信注册](#3.3)  
 &nbsp; &nbsp; [ 3.4微信登录](#3.4)  
 &nbsp; &nbsp; [ 3.5wxUuid验证是否存在](#3,5)
 
 [4.Banner (需登录)](#4)  
 &nbsp; &nbsp; [ 4.1Banner列表](#4.1)  


# <h2 id='1'>1.商品信息 (需登录)</h2>
## <h3 id='1.1'>1.1商品详情</h3>
#### URL:   * /api/commodity/detail*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
id  | long | 商品id | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
data  | map | 见商品详情 | 
 
### 商品详情 
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
id  | long | 商品id | 1
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

### 商品资源详情 
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
type  | string | 名称 | 材质
value  | string | 值 | 毛绒

### 商品资源详情 
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
id  | long | 商品id | 1
price |int | 产品价格,单位分 | 37800
thumbnail |string | 缩率图 | http://qimg.hxnews.com/2019/0130/1548847547525.jpg
stock |int | 库存 | 2344
properties| string | 属性| 绿色
 
            
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
id  | long | 商品id | 1
thumbnail |string | 缩率图 | http://qimg.hxnews.com/2019/0130/1548847547525.jpg
title |string | 名称 | 贴纸
subtitle |string | 副产品副标题（特点） | `自主品牌 | 包换包退 | 官方直售`
label |string | 主产品标签 | 课程配套教具
showPrice |int | 产品价格,单位分 | 37800
sales |int | 销量 | 100


# <h2 id='2'>2.订单操作 (需登录)</h2>
## <h3 id='2.1'>2.1下单</h3>
#### URL:   * /api/order/create*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
addressId | long | 用户收件地址id | 是
remark | string |备注 | 否
couponId | long |使用优惠券id | 否
orders | array | 见商品资源信息 | 是

### 商品资源信息 
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
commodityId | long |商品id | 是
resourceId | long | 商品资源id | 是
num | int |数量 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
orderNo | string | 订单号 | BSP9F4H5A7K688U0U8
payAmount | int |支付费用 | 29900
  
## <h3 id='2.2'>2.2取消订单(暂时不用)</h3>
#### URL:   * /api/order/cancel *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
orderId | long | 订单号 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----

## <h3 id='2.3'>2.3订单列表</h3>
#### URL:   * /api/order *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
orderStatus | string |订单状态 PAYING(待付款)/CANCEL/PAID（待发货）/SENT（已发货）/COMPLETED（已完成） | 是
skip |int | 从第几条查询
limit| int |查询总数

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
total  | long |总数 |
list  | array |具体见商品列表 |

### 商品列表
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
orderNo | string |订单号 | BS3332L028Q9B952E3
leftTime | int | 剩余支付时间| 60 
payAmount  | int | 支付金额 |2000 
orderCommodities | array|见orderCommodities

### orderCommodities
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
title| string |标题 |贴纸
thumbnail|string |缩略图 |http://qimg.hxnews.com/2019/0130/1548847547525.jpg
colorNum |string |型号 |颜色
properties|string | 内容 | 百变方块
num| int |件数|4
price|long | 价格 | 233



# <h2 id='3'>3. AUTH (无需登录)</h2>

## <h3 id='3.1'>3.1 获取短信验证码</h3>
#### URL:   * /api/auth/sms *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile | String | 手机号码|是

<h3 id='3.2'>3.2 手机登录</h3>

#### URL:   * /api/auth/login *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile | String | 手机号码|是
code| String | 短信验证码|是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
token  | String | token | 79767d55b2544d2c8594fecf1c21fa15 
accountId  | long | 用户id | 123456 


## <h3 id='3.4'>3.4 微信登录</h3>
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
sex| int | 性别 性别 0:女 1：男 | 是
mobile| String | 手机号码 | 1.8 false 未注册过必传
code| String | 手机验证码 | 1.8 false 未注册过必传
nickname | String | 昵称 | 否

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
token  | String | token | 79767d55b2544d2c8594fecf1c21fa15 
accountId  | long | 用户id | 123456 


## <h3 id='3.5'>3.5 微信wxUuid验证是否存在</h3>
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

# <h2 id='4'>4.Banner (需登录)</h2>
## <h2 id='4.1'> 4.1Banner列表 </h3>
#### URL:   * /api/banner*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
id | long | |是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
id | long | banner标识 |1
picture | string | 图片url|http://baidu.com.img1
link | string | link地址 |
type | string | 类型 | AD



  

   

  
 














 










 


      
   




