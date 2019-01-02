# 幼教接口

版本号 | 完成日期 |生效时间| 修改人 | 变更描述
---- | ------- | ----- | ----- | -------
1.0.1 | 2018.12.12 | 2018.12.12 16：35 | 忠琪 | 去除登录返回的logininfo对象只返回token，宝宝列表添加字段kid，新增接口 2.12 绑定推荐人邀请码，AccountCacheBean 新增字段 askCode,recommendCode
1.0.2 | 2018.12.12 | 2018.12.12 20:00 | 忠琪 | 1.AccountBalanceBean 的useableAmount 改成 usableAmount 2.course >> unit courseItem >>lesson 涉及接口:2.1,4.1,5.1 
1.0.3 | 2018.12.13 | 2018.12.13 13:00 | 忠琪 | /api/config/index 添加跳转课包ids ,通过ids里面的id 向/api/unit/lessons 取课程 与后台数据交互统一
2.0.0|2018.12.23 | 2018.12.23 18:00 | 忠琪 | 1. 【2.9 用户优惠券列表丰富筛选条件】2.【7.1发现，4.1 课程列表 新增返回参数】 3.【重做 2.12 兑换码兑换 5.1 学习】99.【新增接口:1.7,2.13,2.14,2.15,2.16,2.17,4.2,7.2,8.1】
2.0.1 | 2018.12.24 | 2018.12.24 18:00 | 魏德旺 | 新增接口【1.6 微信授权，2.14 充值（包括微信app，支付宝app支付两种方式） 3.1 绘本列表 3.2 绘本下载 9.1获取微信appId】。更新【5.1 支持绘本学习，绘本解锁】

## API请求地址
#### https://bell.beecloud.cn
#### 请求头里面 token 身份认证
#### 返回 resultCode 为 0 时为正常调用

## 目录
[1.AUTH (无需登录)](#1)  
 &nbsp; &nbsp; [ 1.1获取短信验证码](#1.1)  
 &nbsp; &nbsp; [ 1.2手机登录](#1.2)  
 &nbsp; &nbsp; [ 1.3 获取微信跳转路径](#1.3)  
 &nbsp; &nbsp; [ 1.4 微信登录](#1.4)  
 &nbsp; &nbsp; [ 1.5 上传图片](#1.5)  
 &nbsp; &nbsp; [ 1.6 微信授权](#1.6)  
 &nbsp; &nbsp; [ 1.7 预约账户绑定](#1.7)  
 
 [2.账户操作](#2)  
&nbsp; &nbsp; [ 2.1 账户信息](#2.1)  
&nbsp; &nbsp; [ 2.2 添加宝宝](#2.2)  
&nbsp; &nbsp; [ 2.3 宝宝列表](#2.3)  
&nbsp; &nbsp; [ 2.4 切换宝宝](#2.4)  
&nbsp; &nbsp; [ 2.5 修改用户信息](#2.5)  
&nbsp; &nbsp; [ 2.6 修改宝宝信息](#2.6)  
&nbsp; &nbsp; [ 2.7 手机号码绑定](#2.7)  
&nbsp; &nbsp; [ 2.8 用户资金账户](#2.8)  
&nbsp; &nbsp; [ 2.9 用户优惠券列表](#2.9)  
&nbsp; &nbsp; [ 2.10 微信绑定](#2.10)  
&nbsp; &nbsp; [ 2.11 微信解绑](#2.11)  
&nbsp; &nbsp; [ 2.12 兑换](#2.12)  
&nbsp; &nbsp; [ 2.13 变更绑定手机号码](#2.13)  
&nbsp; &nbsp; [ 2.14 充值](#2.14)  
&nbsp; &nbsp; [ 2.15 充值列表](#2.15)  
&nbsp; &nbsp; [ 2.16 意见反馈](#2.16)  
&nbsp; &nbsp; [ 2.17 我的推荐信息](#2.17)  
&nbsp; &nbsp; [ 2.18 内购服务器订单验证](#2.18)  

 [3.绘本相关](#3)  
&nbsp; &nbsp; [ 3.1 绘本列表](#3.1)  
&nbsp; &nbsp; [ 3.2 绘本下载](#3.2)  
&nbsp; &nbsp; [ 3.3 绘本分享解锁](#3.3)  

 [4.课件相关](#4)  
&nbsp; &nbsp; [ 4.1 课程列表](#4.1)  
&nbsp; &nbsp; [ 4.2 课程下载](#4.2)  

 [5.宝宝相关](#5)  
&nbsp; &nbsp; [ 5.1学习/(获取/上传 学习记录)](#5.1)  

[6.配置相关(无需登录)](#6)  
&nbsp; &nbsp; [ 6.1 主页配置](#6.1)  

[7.文章 (无需登录)](#7)  
&nbsp; &nbsp; [ 7.1 发现列表](#7.1)  
&nbsp; &nbsp; [ 7.2 发现点击](#7.2)  

[8.订单 ](#8)  
&nbsp; &nbsp; [ 8.1 贝壳消费](#8.1)  




# <h2 id='1'>1. AUTH (无需登录)</h2>
## <h3 id='1.1'>1.1 获取短信验证码</h3>
#### URL:   */api/auth/sms*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile | String | 手机号码|是



## <h3 id='1.2'>1.2 手机登录</h3>
#### URL:   */api/auth/login*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile | String | 手机号码|是
code| String | 短信验证码|是
deviceId | String | 设备唯一id|否
deviceType | String | 设备类型 IOS/ANDROID |否


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
token  | String | token | 79767d55b2544d2c8594fecf1c21fa15 
accountId  | long | 用户id | 123456 



## <h3 id='1.3'>1.3 获取微信跳转路径</h3>
#### URL:   */api/auth/wxredirect*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
url  | String | 微信回调路径 | https://open.weixin.qq.com/connect/oauth2/authorize?appid=...... 


##  <h3 id='1.4'>1.4 微信登录</h3>
#### URL:   */api/auth/wxlogin*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
deviceId | String | 设备唯一id | 是
deviceType | String | 设备类型 IOS/ANDROID |是
openid | String | 微信授权登录id | 是
touristId |long | 游客Id,当前游客账号升级成手机用户,信息不丢失| 否
nickname | String | 昵称 | 否
avatar| String | 头像 | 否
city| String | 城市 | 否
country| String | 国家 | 否
province| String | 省份 | 否
sex| int | 性别 性别 0:女 1：男 | 是


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
token  | String | token | 79767d55b2544d2c8594fecf1c21fa15 
accountId  | long | 用户id | 123456 


##  <h3 id='1.5'>1.5 上传图片</h3>
#### URL:   */api/auth/uploadimg*
#### Method: *POST*
#### 请求参数格式: *form-data* !!!!!
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
file | File | 图片文件 | 是



### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
url  | String | 图片外链url | http://pisgc0usp.bkt.clouddn.com/69974402bc7647a084b46cbdac45201f 

## <h3 id='1.6'>1.6 微信授权</h3>
#### URL:   */api/auth/wxauth*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
code | String | 微信授权临时票据 | 是
deviceId | String | 设备唯一id | 是
deviceType | String | 设备类型。 可选值：IOS/ANDROID |是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
token  | String | token | 79767d55b2544d2c8594fecf1c21fa15 
accountId  | long | 用户id | 123456 

## <h3 id='1.7'>1.7 预约账户绑定</h3>
#### URL:   */api/auth/login*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile | String | 手机号码|是
code| String | 短信验证码|是
askCode | String | 推荐用户的邀请码 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


# <h2 id='2'>2.账户相关</h2>

## <h3 id='2.1'>2.1 账户信息</h3>
#### URL:   */api/account/info*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
info  | Object | 账户信息 | 参见附录 [AccountCacheBean](#AccountCacheBean)
balance | Objcet | 资金账户 | 参见 [AccountBalanceBean](#AccountBalanceBean)

## <h3 id='2.2'>2.2 添加宝宝</h3>
#### URL:   */api/account/addkid*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
nickname | String | 宝宝昵称 | 是
birthday | long | 宝宝生日 时间戳 | 是
sex  | Integer | 性别 0:女 1：男 | 是
avatar | String | 头像 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----

##  <h3 id='2.3'>2.3 宝宝列表</h3>
#### URL:   */api/account/kids*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
kids | List\<Object\> | 宝宝列表 | 宝宝参见附录 [KidBean](#KidBean)
kid | Object | 当前选中的宝宝信息| 宝宝参见附录[KidBean](#KidBean)

##  <h3 id='2.4'>2.4 切换宝宝</h3>
#### URL:   */api/account/switchkid*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
kidId | Long | 需要切换的宝宝Id | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


##  <h3 id='2.5'>2.5 修改用户信息</h3>
#### URL:   */api/account/update*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
nickname | String | 用户昵称 | 否 填写认为修改
avatar | String | 用户头像 | 否 填写认为修改

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----

##  <h3 id='2.6'>2.6 修改宝宝信息</h3>
#### URL:   */api/account/updatekid*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
kidId | Long | 宝宝id | 是
nickname | String | 宝宝昵称 | 否 填写认为修改
birthday | long | 出生日时间戳 | 大于 0 视为修改
sex | int | 性别 0:女 1：男 |  是
avatar | String | 宝宝头像 | 否 填写认为修改

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


##  <h3 id='2.7'>2.7 手机号码绑定</h3>
#### URL:   */api/account/mobilebinding*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile | String | 手机号码 | 是
code | String | 短信验证码 | 是


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----

## <h3 id='2.8'>2.8 用户资金账户</h3>
#### URL:   */api/account/balance*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
balance | Objcet | 资金账户 | 参见 [AccountBalanceBean](#AccountBalanceBean)

## <h3 id='2.9'>2.9 用户优惠券列表</h3>
#### URL:   */api/account/coupons*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
type |String | 优惠类型 COUPON:现金券 SALE:折扣券| 否
status | String | 优惠券状态 I:过期 A:正常  S:已使用| |否 
target | String | 使用范围 （优惠券可以精确到课包）,购买商品时精确帅选 UNIT:课包 PICTUREBOOK:绘本| 否 
targetId| String | 目标id 根据target  UNIT 课包id , PICTUREBOOK 绘本id|否


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
list | List\<Object\> | 优惠券列表 | 参见 [AccountCouponBean](#AccountCouponBean)




## <h3 id='2.10'>2.10 微信绑定</h3>
#### URL:   */api/account/wxbinding*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
openId |String | 微信openId| 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
 

## <h3 id='2.11'>2.11 微信解绑</h3>
#### URL:   */api/account/wxunbinding*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----

## <h3 id='2.12'>2.12 兑换</h3>
#### URL:   */api/account/exchange*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
exchangeCode| String| 兑换码 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
goodsName | String | 商品名称 | 10元优惠券一张

## <h3 id='2.13'>2.13 变更绑定手机号码</h3>
#### URL:   */api/account/changemobile*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile| String| 手机号码 | 是
code| String| 手机验证码 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


## <h3 id='2.14'>2.14 充值</h3>

#### URL:   */api/account/recharge*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | Header信息 | 是
channel | String | 渠道信息。ANDROID可选值WX\_APP / ALI\_APP。IOS值为IAP| 是
amount | int | 充值金额，单位元 | 是
title | String | 充值标题| 是
deviceType | String | 设备类型，ANDROID/IOS| 是

### 微信支付和支付宝支付返回公共参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
billNo | String | 订单号 | RET2Z250C626E6U085
content | String | 支付参数 | ANDROID 返回参照：微信支付附加参数 JSONString 或 支付宝支付附加参数
productId | String | ios内购产品id | IOS 内购返回

### [微信支付附加参数](https://pay.weixin.qq.com/wiki/doc/api/app/app.php?chapter=9_12&index=2)
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
app_id | String | 应用ID | wx8888888888888888
partner_id | String | 商户号 | 1900000109
prepay_id | String | 预支付交易会话ID | WX1217752501201407033233368018
package | String | 扩展字段 | Sign=WXPay
nonce_str | String | 随机字符串	| 5K8264ILTKCH16CQ2502SI8ZNMTM67VS
timestamp | String | 时间戳 | 1412000000 
pay_sign | String | 签名 | C380BEC2BFD727A4B6845133519F3AD6 


### 支付宝支付附加参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
order_string | String | app支付请求参数字符串，主要包含商户的订单信息.key=value形式，以&连接。参数描述如参照[https://docs.open.alipay.com/204/105465/](https://docs.open.alipay.com/204/105465/)|charset=utf-8&method=alipay.trade.app.pay&sign=I....D%3D&notify_url=https%3A%2F%...8b757fd&version=1.0&app_id=2016070801592943&sign_type=RSA2&timestamp=2018-12-24+11%3A45%3A18&alipay_sdk=alipay-sdk-java-dynamicVersionNo&format=json&biz_content={\"out_trade_no\":\"REE2O321E1S3H0L4Z4\",\"total_amount\":\"1.0\",\"subject\":\"充值\",\"product_code\":\"QUICK_MSECURITY_PAY\"}



## <h3 id='2.15'>2.15 充值列表</h3>

#### URL:   */api/account/rechargelist*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | Header信息 | 是
status | String | 充值状态  I:未支付  S:充值成功  F:充值失败| 否
billNo | String | 充值订单号| 否


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
list | List<Obejct> | 充值订单列表 | 参见 [RechargeBean](#RechargeBean)


## <h3 id='2.16'>2.16 意见反馈</h3>
#### URL:   */api/account/opinion*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
images | String[] | 图片链接数组 | 是
feedback | String | 反馈内容| 是
deivceId | String | 设备id| 否
deviceType | String | 设备类型| 否
mobileModel | String | 手机型号 | 否


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


## <h3 id='2.17'>2.17 我的推荐信息</h3>
#### URL:   */api/account/recommendinfo*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
askCode | String | 我的邀请码 |
recommendCode | String | 我绑定的邀请码
accountCount | int | 我推荐人的数量
couponCount | int | 我推荐获取的优惠券数量 
couponSumAmount| double |我推荐获取的优惠券总额


## <h3 id='2.18'>2.18 内购回调</h3>
#### URL:   */api/account/recommendinfo*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
certificate | String | ios 支付凭证
orderNo | String | 支付订单号





# <h2 id='3'>3.绘本相关</h2>
## <h3 id='3.1'>3.1 绘本列表</h3>
#### URL:   */api/picturebook/list*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | Header信息 | 是
skip | String | 起始位置| 是
limit | long | 条数 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
list | List\<Object\>|  参见附录 [PictureBookBean](#PictureBookBean)


## <h3 id='3.2'>3.2 绘本下载</h3>
#### URL:   */api/picturebook/download*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | Header信息 | 是
pictureBookId | long | 绘本id| 是
lastOffset | long | 偏移量 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


## <h3 id='3.3'>3.3 绘本分享解锁</h3>
#### URL:   */api/picturebook/share*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | Header信息 | 是
pictureBookId | long | 绘本id| 是
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----



# <h2 id='4'>4.课件相关</h2>
## <h3 id='4.1'>4.1 课程</h3>
#### URL:   */api/unit/lessons*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
unitId | long | 课件id | 是
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
lessons  | List\<Object\> | 课件明细 | 参见附录 [LessonBean](#LessonBean)

### PS: auth=true，unlock=true才能看，auth=true,unlock=false,不能看，因为前面的课还没学完，auth=false，unlock=false，表示前面有课没学完，并且这个课需要购买才能学（同样提示“学完钱前面的课”）。auth=false，unlock=true表示前面的课已经学完了，但是这个课程需要购买才能学


## <h3 id='4.2'>4.2 课程下载</h3>
#### URL:   */api/unit/downloadlesson*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*

####断点下载的方法是:*获取这个方法返回的连接,在头部添加,Range: bytes=<first-byte-pos>-<last-byte-pos>,例如:Range: bytes 1024-2048表示下载1024-2048的内容; Range: bytes 1024- 表示下载1024之后的内容,注意,这个是闭合区间,0-1实际下载的是第0个第1个两个字节*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
lessonId | long | 课程id | 是
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
url  | String | 下载链接 | 有效时间 1小时




# <h2 id='5'>5.宝宝相关</h2>
## <h3 id='5.1'>5.1 学习</h3>
#### URL:   */api/kid/study*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
### !!打开任何素材前需要调用此方法，每个课件解锁需要保存进度上传自定义flag
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
type | String | 学习类型 LESSON:课件/PICTUREBOOK：绘本| 是
id | long | 更新type LESSON：课件id/PICTUREBOOK：绘本id |是
flag |int | 自定义学习位置 大于0:覆盖之前学习进度 0：会返回之前学习进度| 是 
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
flag | int |学习位置 0:从新开始| 0

# <h2 id='6'>6.配置相关(无需登录)</h2>
## <h3 id='6.1'>6.1 主页配置</h3>
#### URL:   */api/config/index*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
configs |Map| 模块配置是否显示 | 0 ：不显示
activity |Map| 模块是否显示限免标签 | 0 ：不显示
ids |Map | 模块跳转的课包id | 
picturebooks | List<Object> | 推荐绘本列表 | 参见 [PictureBookBean](#PictureBookBean)

### configs/activity MAP 对应
key| 类型 | 含义 | 示例 
---- | ---- | ---- | ----
BANNER_ZRPD| int |自然拼读 开关/跳转的课包id | 0:不显示(限时免费)/课包id
BANNER_ZXKC| int |主线课程 开关/跳转的课包id | 0:不显示(限时免费)/课包id
BANNER\_LIST\_RG| int |英语儿歌 开关 | 0:不显示(限时免费)
BANNER\_LIST\_GAME| int |互动游戏 开关 | 0:不显示(限时免费)
BANNER\_LIST\_HB| int |英语绘本 开关 | 0:不显示(限时免费)



# <h2 id='7'>7.文章 (无需登录)</h2>
## <h3 id='7.1'> 7.1 发现列表</h3>
#### URL:   */api/article/findlist*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
skip | int | 其实位置 | 是
limit | int | 显示多少条 | 是

### 返回参数
参数名 | 类型 | 含义 
---- | ---- | ----  
list |List\<Object\>|  参见附录 [ArticleBean](#ArticleBean)

## <h3 id='7.2'> 7.2 发现点击</h3>
#### URL:   */api/article/findclick*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
id | long | 发现文章id | 是

### 返回参数
参数名 | 类型 | 含义 
---- | ---- | ----  


# <h2 id='8'>8.订单</h2>
## <h3 id='8.1'> 8.1 贝壳消费</h3>
#### URL:   */api/order/buy*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
type | String | 商品类型 UNIT:课包/PICTUREBOOK:绘本| 是
goodsId | long | 商品id UNIT：课包id/PICTUREBOOK：绘本id| 是
couponId | long | 优惠券id 大于0使用| 否
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
orderNo| String | 订单号

# <h2 id='9'>9.APP信息</h2>
##<h3 id='9.1'> 9.1 获取APPID</h3>
#### URL:   */api/app*
#### Method: *GET*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
app_id | app_id | 微信appId|









## 附录
### <h3 id='AccountCacheBean'>AccountCacheBean</h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
id  | Long | 账户id
account  | String | 账号
type  | String | 账户类型
lastLoginTime  | Long | 最后登录时间戳
continuityLoginDays  | Integer | 连续登录天数
status  | String | 账户状态
nickname  | String | 昵称
avatar  | String | 头像
mobile  | String | 手机号码  不为空则视为绑定过手机号码
openId | String | 微信openId  不为空则视为绑定过微信
sex  | Integer | 性别 0:女 1：男
city  | String | 城市
province  | String | 省份
country  | String | 国家
kidId  | long | 选中的宝宝id
askCode | String | 自己的邀请码 唯一（注册时自动生成）
recommendCode | String | 推荐人/代理商的 邀请码


### <h3 id='KidBean'> KidBean </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
id  | Long | 宝宝id
nickname  | String | 昵称
parentId  | Long | 账户id
sex  | Integer | 性别 0:女 1：男
birthday | Long | 生日时间戳
avatar | String | 头像
status | String | A:选中 I:未选中
age | int | 年龄


###  <h3 id='LessonBean'> LessonBean </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
id  | long | 课件明细id
unitId | long | 课包id
lesson | int | 第几节课
title | String | 标题
describe | String | 描述
image | String | 图片路径
duration | int | 时长 单位：分钟
scoreRule | String | 得分规则
vip | int | 权限  参见 [VIP](#VIP)
unlock | boolean | 是否解锁
auth| boolean | 是否有权限，判断是否购买
downloadSize | long | 下载文件大小 字节

### <h3 id='ArticleBean'> ArticleBean </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
id | int | 文章id
title| String | 文章标题
describe | String | 描述
recommend | String | 引荐
url | String | 引用文章url
releaseTime | long | 发布时间戳
image | String | 图片路径
count | long | 阅读数

### <h3 id='AccountBalanceBean'> AccountBalanceBean </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
accountId | long | 用户账户id
amount | Double | 账户总金额
freezeAmount | Double | 账户冻结金额
useableAmount | Double | 真实可用金额

### <h3 id='AccountCouponBean'> AccountCouponBean </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
id | long | 优惠券id
couponId | long | 优惠券模板id
title | String | 标题
accountId | long | 账户id
type | String | 类型 COUPON:现金券 SALE:折扣券
num |double | COUPON:抵用金额  SALE: 打多少折
fullPrice| double | 满多少金额使用
startTime | long | coupon 使用的开始时间戳
endTime | long | coupon 使用的结束时间戳
status | String | 状态 A:未使用  S:已使用 I:已过期作废
orderNo | String | 使用的订单号

### <h3 id='WEIXINPAYMAP'> WEIXINPAYMAP </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
pay_sign| String | pay_sign
partner_id|String | partner_id
package | String | package
prepay_id | String | prepay_id
nonce_str |String | nonce_str
timestamp | String | 时间戳（10位，秒）


### <h3 id='RechargeBean'> RechargeBean </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
id| long | 订单id
accountId | long | 账户id
billNo | String | 充值订单号
amount | double | 充值金额
num | Double | 充值等换贝壳数量
channel | String | 充值渠道 WX_APP：微信 ALI_APP：支付宝 IAP：IOS内购
status | String | 状态 I：未支付 S:充值成功 F:充值失败
remark | String | 备注
finisTime | Date | 订单完成时间
createTime | Date | 订单创建时间
tradeNo | String | 外部订单号




### <h3 id='PictureBookBean'> PictureBookBean </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
id | int | 绘本id
title| String | 绘本标题
description | String | 描述
image | String | 图片路径
author | String | 作者
vip | int | 参见 [VIP](#VIP)
needShare | int | 是否需要 分享解锁 （VIP=0 时判断）
price| double | 单价
count| long | 显示点击数
auth | boolean |是否有权限
fileSize | long | 下载文件大小 字节
shareImage | String | 分享图片
shareContent | String | 分享文案


### <h3 id='VIP'> VIP </h3>
数值 | 含义 
----  | ---- 
0|  没有权限限制
50 | 部分免费 部分需要购买
60 | 需要购买




   






   





  






 


  

   

  
 














 










 


      
   




