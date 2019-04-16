# 幼教接口

版本号 | 完成日期 |生效时间| 修改人 | 变更描述
---- | ------- | ----- | ----- | -------
1.0.1 | 2018.12.12 | 2018.12.12 16：35 | 忠琪 | 去除登录返回的logininfo对象只返回token，宝宝列表添加字段kid，新增接口 2.12 绑定推荐人邀请码，AccountCacheBean 新增字段 askCode,recommendCode
1.0.2 | 2018.12.12 | 2018.12.12 20:00 | 忠琪 | 1.AccountBalanceBean 的useableAmount 改成 usableAmount 2.course >> unit courseItem >>lesson 涉及接口:2.1,4.1,5.1 
1.0.3 | 2018.12.13 | 2018.12.13 13:00 | 忠琪 | /api/config/index 添加跳转课包ids ,通过ids里面的id 向/api/unit/lessons 取课程 与后台数据交互统一
2.0.0|2018.12.23 | 2018.12.23 18:00 | 忠琪 | 1. 【2.9 用户优惠券列表丰富筛选条件】2.【7.1发现，4.1 课程列表 新增返回参数】 3.【重做 2.12 兑换码兑换 5.1 学习】99.【新增接口:1.7,2.13,2.14,2.15,2.16,2.17,4.2,7.2,8.1】
2.0.1 | 2018.12.24 | 2018.12.24 18:00 | 魏德旺 | 新增接口【1.6 微信授权，2.14 充值（包括微信app，支付宝app支付两种方式） 3.1 绘本列表 3.2 绘本下载 9.1获取微信appId】。更新【5.1 支持绘本学习，绘本解锁】
2.0.2 | 2019.1.17 | 2019.1.17 16:00 | 忠琪 | 新增接口【4.3 课包信息，8.2 贝壳数量计算】
2.0.2 | 2019.2.16 | 2019.2.16 11:00 | 魏德旺| 新增接口【10，11】
2.1.0 | 2019.2.18 | 2019.2.18 16:00 | 忠琪 | 新增接口【儿歌相关,收藏相关】,账户分开Ios安卓不通用
2.1.1 | 2019.2.25 | 2019.2.25 16:00 | 忠琪 | 新增接口【1.8，1.9】,修改【1.4 微信登录前需要调1.8验证是否注册过，未注册过的需要获取手机信息一并传入； 【全局】用户类型添加类型：TOURIST（游客模式）】
2.1.2 | 2019.3.19 | 2019.3.2X | 忠琪 | 3.1 绘本查询条件添加vip, lesson，绘本，儿歌新增materId(运营手动约定维护,日志分析使用)
2.1.3 | 2019.3.26 | 2019.3.2X | 忠琪 | 新增 0.主页接口, 绘本列表 添加label字段,儿歌添加 label,count字段，6.1添加 kidsongs 儿歌列表 6.1 主页以后不再维护--尽快切到 0;
2.1.4 | 2019.4.8 | 2019.4.10 | 忠琪 | 0.主页 CourseDto 新增字段；课程相关添加 原价和标签；绘本添加原价 


## API请求地址
#### https://bell.beecloud.cn
#### 请求头里面 token 身份认证
#### 返回 resultCode 为 0 时为正常调用

## 目录
[0.主页 (非强制登录)](#0)  
[1.AUTH (无需登录)](#1)  
 &nbsp; &nbsp; [ 1.1获取短信验证码](#1.1)  
 &nbsp; &nbsp; [ 1.2手机登录](#1.2)  
 &nbsp; &nbsp; [ 1.3 获取微信跳转路径](#1.3)  
 &nbsp; &nbsp; [ 1.4 微信登录](#1.4)  
 &nbsp; &nbsp; [ 1.5 上传图片](#1.5)  
 &nbsp; &nbsp; [ 1.6 微信授权](#1.6)  
 &nbsp; &nbsp; [ 1.7 预约账户绑定](#1.7)  
 &nbsp; &nbsp; [ 1.8 openId 验证是否存在](#1.8)  
 &nbsp; &nbsp; [ 1.9 游客登录](#1.9) 
 &nbsp; &nbsp; [ 1.10 三方账户验证](#1.10)  
 &nbsp; &nbsp; [ 1.11 三方登录](#1.11) 
 &nbsp; &nbsp; [ 1.12 设备记录](#1.12)   
 
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
&nbsp; &nbsp; [ 2.19 已购课程](#2.19)  

 [3.绘本相关](#3)  
&nbsp; &nbsp; [ 3.1 绘本列表](#3.1)  
&nbsp; &nbsp; [ 3.2 绘本下载](#3.2)  
&nbsp; &nbsp; [ 3.3 绘本分享解锁](#3.3)  
&nbsp; &nbsp; [ 3.4 绘本信息](#3.4)  

 [4.课件相关](#4)  
&nbsp; &nbsp; [ 4.1 课程列表](#4.1)  
&nbsp; &nbsp; [ 4.2 课程下载](#4.2)  
&nbsp; &nbsp; [ 4.3 课包信息](#4.3)  

 [5.宝宝相关](#5)  
&nbsp; &nbsp; [ 5.1学习/(获取/上传 学习记录)](#5.1)  
&nbsp; &nbsp; [ 5.2收藏/取消收藏](#5.2)  

[6.配置相关(无需登录)](#6)  
&nbsp; &nbsp; [ 6.1 主页配置](#6.1)  

[7.文章 (无需登录)](#7)  
&nbsp; &nbsp; [ 7.1 发现列表](#7.1)  
&nbsp; &nbsp; [ 7.2 发现点击](#7.2)  

[8.订单 ](#8)  
&nbsp; &nbsp; [ 8.1 贝壳消费](#8.1)  
&nbsp; &nbsp; [ 8.2 贝壳数量计算](#8.2)  

[10.微信订阅号Auth (无需登录)](#10)  
 &nbsp; &nbsp; [ 10.1获取短信验证码](#10.1)  
 &nbsp; &nbsp; [ 10.2手机登录](#10.2)  
 &nbsp; &nbsp; [ 10.3 获取微信跳转路径](#10.3)  
 &nbsp; &nbsp; [ 10.4 微信认证登录](#10.4)  
 &nbsp; &nbsp; [ 10.5 充值订单信息](#10.5)  

[11.微信订阅号平台上账户操作(需登录)](#11)  
 &nbsp; &nbsp; [ 11.1 充值](#11.1)  
 &nbsp; &nbsp; [ 11.2 退出账号](#11.2)    
 &nbsp; &nbsp; [ 11.3 账户token验证](#11.3)
    
 
 [12.儿歌相关](#12)  
 &nbsp; &nbsp; [ 12.1 儿歌分类列表](#12.1)  
 &nbsp; &nbsp; [ 12.2 儿歌列表](#12.2)   
 &nbsp; &nbsp; [ 12.3 儿歌下载](#12.3)   



# <h2 id='0'>0.主页(非强制登录)</h2>
#### URL:   */api/index*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | heard 参数 只要登录状态就一定要传|非强制 

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
banners  | List | 轮播图列表 | 参见附录 [BannerBean](#BannerBean) 
courses  | List | 课程列表 | 参见附录 [CourseDto](#CourseDto) 
picturebooks  | List | 绘本列表 | 参见附录 [PictureBookBean](#PictureBookBean) 
kidsongs  | List | 轮播图列表 | 参见附录 [KidSongBean](#KidSongBean) 




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
wxUuid | String | 微信授权唯一 unionid | 是
nickname | String | 昵称 | 否
avatar| String | 头像 | 否
city| String | 城市 | 否
country| String | 国家 | 否
province| String | 省份 | 否
sex| int | 性别 性别 0:女 1：男 | 是
mobile| String | 手机号码 | 1.8 false 未注册过必传
code| String | 手机验证码 | 1.8 false 未注册过必传


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

## <h3 id='1.8'>1.8 微信openId验证是否存在</h3>
#### URL:   */api/auth/openidcheck*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
openid | String | 微信openid|是
wxUuid | String | 微信授权唯一 unionid | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
isHave | boolean | 是否存在 true:存在，false:不存在，需要授权后先获取手机号码|


## <h3 id='1.9'>1.9 游客登录</h3>
#### URL:   */api/auth/touristlogin*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
deviceType | String | 设备类型 IOS/ANDROID|是
deviceId | String | 设备ID|是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
token  | String | token | 79767d55b2544d2c8594fecf1c21fa15 
accountId  | long | 用户id | 123456 



## <h3 id='1.10'>1.10 三方账户验证是否存在</h3>
#### URL:   */api/auth/sfcheck*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
type | String | 三方渠道类型 :HUAWEI|是
uuid | String | 三方渠道唯一ID | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
isHave | boolean | 是否存在 true:存在，false:不存在，需要授权后先获取手机号码|


##  <h3 id='1.11'>1.11 三方登录</h3>
#### URL:   */api/auth/sflogin*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
deviceId | String | 设备唯一id | 是
deviceType | String | 设备类型 IOS/ANDROID |是
type | String | 三方渠道类型 :HUAWEI|是
uuid | String | 三方渠道唯一ID | 是
nickname | String | 昵称 | 否
avatar| String | 头像 | 否
sex| int | 性别 性别 0:女 1：男 | 是
mobile| String | 手机号码 | 1.10 false 未注册过必传
code| String | 手机验证码 | 1.10 false 未注册过必传

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
token  | String | token | 79767d55b2544d2c8594fecf1c21fa15 
accountId  | long | 用户id | 123456 


##  <h3 id='1.12'>1.12 设备记录</h3>
#### URL:   */api/auth/deviceflag*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
deviceId | String | 设备唯一id | 是
deviceType | String | 设备类型 IOS/ANDROID |是
electricNum | String | 设备电量 double 类型的String字符|是
timestamp | long | 时间戳 毫秒 |是
source | String | 来源 如：（官方,华为,H5活动） 标识key|否
area | String | 地区金纬度|否
sign | String | 签名 （口述,不外传） | 是



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
wxUuid | String | 微信授权唯一 unionid | 是

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
content | Map | 支付参数 | ANDROID 返回参照：微信支付附加参数 JSONString 或 支付宝支付附加参数
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
skip | String | 起始位置| 是
limit | long | 条数 | 是


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
token | String | Header信息 | 是
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
token | String | Header信息 | 是


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
startDate | String | 开始日期 | 2019.02.03
askCode | String | 我的邀请码 |
recommendCode | String | 我绑定的邀请码
accountCount | int | 我推荐人的数量
couponCount | int | 我推荐获取的优惠券数量 
couponSumAmount| double |我推荐获取的优惠券总额


## <h3 id='2.18'>2.18 内购回调</h3>
#### URL:   */api/account/iosnotify*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | Header信息 | 是
certificate | String | ios 支付凭证 | 是
orderNo | String | 支付订单号 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


## <h3 id='2.19'>2.19 已购课程</h3>
#### URL:   */api/account/purchased*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | Header信息 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
units | List | 已购课包列表 |[UnitBean](#UnitBean)
picturebooks | List | 已购绘本列表 | [PictureBookBean](#PictureBookBean)





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
vip | int | -1：全部 0（默认）:免费绘本 60：付费绘本

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


## <h3 id='3.4'>3.4 绘本信息</h3>
#### URL:   */api/picturebook/info*
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
picturebook | Object|  参见附录 [PictureBookBean](#PictureBookBean)


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


## <h3 id='4.3'>4.3 课包信息</h3>
#### URL:   */api/unit/info*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
unitId | long | 课件id | 是
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
info  | Object | 课包信息 | 参见附录 [UnitBean](#UnitBean)




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
finish| boolean | 是否已学完 （true:表示已学完,解锁下节课时）| 否
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
flag | int |学习位置 0:从新开始| 0

## <h3 id='5.2'>5.2 收藏</h3>
#### URL:   */api/kid/collect*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
type | String | 类型 LESSON:课件/PICTUREBOOK：绘本 UNIT:课包 KIDSONG:儿歌| 是
targetId | long | 对应类型的 材料id |是
collect | booean | 不传或者 true为 收藏, false:取消收藏 | 否

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


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
kidsongs | List<Object> | 推荐儿歌列表 | 参见 [KidSongBean](#KidSongBean)

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

## <h3 id='8.2'> 8.2 贝壳数量计算</h3>
#### URL:   */api/order/calculate*
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
payAmount| double | 消费贝壳数量

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


# <h2 id='10'>10. 微信订阅号Auth (无需登录)</h2>
## <h3 id='10.1'>[ 10.1获取短信验证码](#1.1) </h3>


## <h3 id='10.2'>10.2 手机登录</h3>
#### URL:   */api/auth/officialaccount/login*
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
nickname | String | 用户昵称 | 


## <h3 id='10.3'>10.3 获取微信跳转路径</h3>
#### URL:   */api/auth/officialaccount/wxredirect*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
url  | String | 微信回调路径 | https://open.weixin.qq.com/connect/qrconnect?appid=?appid=...... 


## <h3 id='10.4'>10.4 微信认证登录</h3>
#### URL:   */api/auth/officialaccount/wxlogin*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
unionId  | String | 同一个微信开放平台帐号下的移动应用、网站应用和公众帐号，用户的unionid是唯一的 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
token  | String | token | 79767d55b2544d2c8594fecf1c21fa15 
accountId  | long | 用户id | 123456 
nickname | String | 用户昵称 | 


## <h3 id='10.5'>10.5 充值列表</h3>

#### URL:   */api/auth/officialaccount/rechargeinfo*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
rechargeNo | String | 充值订单号| 是



### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
info | Obejct | 充值订单 | 参见 [RechargeBean](#RechargeBean)


# <h2 id='11'>11. 微信订阅号平台上账户操作(需登录)</h2>
## <h3 id='11.1'>11.1 充值</h3>

#### URL:   * /api/officialaccount/recharge*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | Header信息 | 是
amount | float | 充值金额，单位分 | 是
title | String | 充值标题| 是
deviceType | String | 设备类型，ANDROID/IOS| 是

### 微信支付和支付宝支付返回公共参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
billNo | String | 订单号 | RET2Z250C626E6U085
sign | String | 充值签名 | 

## <h3 id='11.2'>11.2 退出账号</h3>

#### URL:   * /api/officialaccount/logout*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | Header信息 | 是

### 微信支付和支付宝支付返回公共参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ---- 


## <h3 id='11.3'>11.3 token验证失效</h3>

#### URL:   * /api/officialaccount/tokencheck*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | Header信息 | 是

### 微信支付和支付宝支付返回公共参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ---- 
login | boolean | 是否已经登录过 | true
accountId  | long | 用户id | 123456 
nickname | String | 用户昵称 | 




# <h2 id='12'>12.儿歌相关</h2>
##<h3 id='12.1'> 12.1 儿歌分类</h3>
#### URL:   */api/song/categorys*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | Header信息 | 是
device_id | String | Header信息 | 是
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
list | List<Object> | 分类列表| 参见 [SelectedDto](#SelectedDto)



##<h3 id='12.2'> 12.2 儿歌列表</h3>
#### URL:   */api/song/list*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | Header信息 | 是
device_id | String | Header信息 | 是
category | String | 分类 | 否 （参见 12.1）[SelectedDto](#SelectedDto)
skip | int | 分页其实位置 |是
limit | int | 分页数量 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
list | List<Object> | 分类列表| 参见 [KidSongBean](#KidSongBean)


## <h3 id='12.3'>12.3 儿歌下载</h3>
#### URL:   */api/song/download*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*

####断点下载的方法是:*获取这个方法返回的连接,在头部添加,Range: bytes=<first-byte-pos>-<last-byte-pos>,例如:Range: bytes 1024-2048表示下载1024-2048的内容; Range: bytes 1024- 表示下载1024之后的内容,注意,这个是闭合区间,0-1实际下载的是第0个第1个两个字节*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
songId | long | 课程id | 是
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
url  | String | 下载链接 | 有效时间 1小时



## 附录
### <h3 id='AccountCacheBean'>AccountCacheBean</h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
id  | Long | 账户id
account  | String | 账号
type  | String | 账户类型 NORMAL:正常登录用户,TOURIST：游客模式
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
shareImage | String | 分享url 含自己推广二维码图片的url


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
version | int | 版本号 
materId| String | 素材ID 运营手动维护

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
accountId | long | 账户id
billNo | String | 充值订单号
amount | double | 充值金额
num | Double | 充值等换贝壳数量
channel | String | 充值渠道 WX_APP：微信 ALI_APP：支付宝 IAP：IOS内购 WX_JSAPI:微信公众号
status | String | 状态 I：未支付 S:充值成功 F:充值失败 P:秒支付button，等待充值回调
remark | String | 备注
finisTime | Date | 订单完成时间
createTime | Date | 订单创建时间
tradeNo | String | 外部订单号
title| String | 充值标题
ip| String | 充值ip
tradeNo | String | 外部订单号
bcId | String | beecloud 订单id
source | String | 支付来源




### <h3 id='PictureBookBean'> PictureBookBean </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
id | int | 绘本id
title| String | 绘本标题
description | String | 描述
icon | String | 列表图标路径
image | String | 封面图片路径
author | String | 作者
vip | int | 参见 [VIP](#VIP)
needShare | int | 是否需要 分享解锁 （VIP=0 时判断）
originalPrice | double | 原始价格 大于0,则有效;0 只显示 price
price| double | 单价
count| long | 显示点击数
auth | boolean |是否有权限
fileSize | long | 下载文件大小 字节
shareImage | String | 分享图片
shareContent | String | 分享文案
androidShareUrl| String | 安卓分享路径
iosShareUrl | String | ios 分享路劲
version | int | 版本号
materId| String | 素材ID 运营手动维护
label | String | 列表标签

### <h3 id='UnitBean'> UnitBean </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
id | long | 课包id
title| String | 课包标题
describe | String | 描述
image | String | 图片路径
minAge | int | 适合最小年龄
maxAge | int | 适合最大年龄
originalPrice | double | 原始价格 大于0,则有效;0 只显示 price
price | double | 售价
vip | int | 参见 [VIP](#VIP)
label | String | 标签


### <h3 id='SelectedDto'> SelectedDto </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
key | String | key
value| String | 值（描述）

### <h3 id='KidSongBean'> KidSongBean </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
id | long | id
title | String | 标题
image | String | image
categorySrc | String | 分类描述
collect | boolean | 是否收藏
version | int | 版本号
materId| String | 素材ID 运营手动维护
count | long | 点击数 
label | String | 列表标签


### <h3 id='BannerBean'> BannerBean </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
picture | String | banner 图片url
type | String | 类型 BLANK:只显示图片,不跳转;URL:完整的url 路径;ACTION:app内部跳转事件
link | String | 链接/事件 URL:直接跳转 ACTION:[ unit:{课包id}// 课包详情页;  picturebook{绘本id}// 绘本详情页;kidsong:{儿歌id}// 儿歌详情页; goods:{商品id}// 商品详情页;post:{帖子id}// 帖子详情页]

### <h3 id='CourseDto'> CourseDto </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
type | String |课程类型  BLANK: 站位,不跳转（即将上线); UNIT:课包;COMMUNITY:社区
jump | String | 跳转id/key（根据type 区分）    如:课包id，社区key
icon | String | 列表图标
vip | int |  参见 [VIP](#VIP)
label | String | 标签
originalPrice | double | 原始价格 大于0,则有效;0 只显示 price
price | double | 目前真实售价
title | String | 课程名称
color | String | 课程名称背景色号

 

### <h3 id='VIP'> VIP </h3>
数值 | 含义 
----  | ---- 
0|  没有权限限制
50 | 部分免费 部分需要购买
60 | 需要购买




   






   





  






 


  

   

  
 














 










 


      
   




