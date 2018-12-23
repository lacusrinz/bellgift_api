# 幼教接口

版本号 | 完成日期 |生效时间| 修改人 | 变更描述
---- | ------- | ----- | ----- | -------
1.0.1 | 2018.12.12 | 2018.12.12 16：35 | 忠琪 | 去除登录返回的logininfo对象只返回token，宝宝列表添加字段kid，新增接口 2.12 绑定推荐人邀请码，AccountCacheBean 新增字段 askCode,recommendCode
1.0.2 | 2018.12.12 | 2018.12.12 20:00 | 忠琪 | 1.AccountBalanceBean 的useableAmount 改成 usableAmount 2.course >> unit courseItem >>lesson 涉及接口:2.1,4.1,5.1 
1.0.3 | 2018.12.13 | 2018.12.13 13:00 | 忠琪 | /api/config/index 添加跳转课包ids ,通过ids里面的id 向/api/unit/lessons 取课程 与后台数据交互统一
2.0.0|2018.12.23 | 2018.12.23 18:00 | 忠琪 | 1. 【2.9 用户优惠券列表丰富帅选条件】2.【7.1发现，4.1 课程列表 新增返回参数】 3.【重做 5.1 学习】99.【新增接口:2.13,7.2,8.1】

## API请求地址
#### https://bell.beecloud.cn
#### 请求头里面 token 身份认证
#### 返回 resultCode 为 0 时为正常调用



## 1.1 获取短信验证码
#### URL:   */api/auth/sms*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile | String | 手机号码|是



## 1.2 手机登录
#### URL:   */api/auth/login*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile | String | 手机号码|是
code| String | 短信验证码|是
touristId |long | 游客Id,当前游客账号升级成手机用户,信息不丢失| 否
deviceId | String | 设备唯一id|否
deviceType | String | 设备类型 IOS/ANDROID |否


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
token  | String | token | 79767d55b2544d2c8594fecf1c21fa15 
accountId  | long | 用户id | 123456 



## 1.3 获取微信跳转路径
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


## 1.4 微信登录
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


## 1.5 上传图片
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


# 2.账户相关（需要 token 验证 ）

## 2.1 账户信息
#### URL:   */api/account/info*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
info  | Object | 账户信息 | 参见附录 AccountCacheBean
balance | Objcet | 资金账户 | 参见 #AccountBalanceBean

## 2.2 添加宝宝
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

## 2.3 宝宝列表
#### URL:   */api/account/kids*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
kids | List<Object> | 宝宝列表 | 宝宝参见附录KidBean
kid | Object | 当前选中的宝宝信息| 宝宝参见附录KidBean

## 2.4 切换宝宝
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


## 2.5 修改用户信息
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

## 2.6 修改宝宝信息
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


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----

## 2.7 手机号码绑定
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

## 2.8 用户资金账户
#### URL:   */api/account/balance*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
balance | Objcet | 资金账户 | 参见 #AccountBalanceBean

## 2.9 用户优惠券列表
#### URL:   */api/account/coupons*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
type |String | 优惠类型 COUPON:优惠券 SALE:折扣券| 否
status | String | 优惠券状态 | |否 I:过期 A:正常  S:已使用
target | String | 使用范围 （优惠券可以精确到课包）,购买商品时精确帅选| 否 UNIT:课包 
targetId| String | 目标id 根据target | UNIT 课包id


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
list | List<Object> | 优惠券列表 | 参见 #AccountCouponBean




## 2.10 微信绑定
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
 

## 2.11 微信解绑
#### URL:   */api/account/wxunbinding*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----

## 2.12 绑定推荐人邀请码
#### URL:   */api/account/recommendcode*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
askCode| String| 邀请码 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----

## 2.13 绑定推荐人邀请码
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





# 4.课件相关
## 4.1 课程
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
lessons  | List<Object> | 课件明细 | 参见附录 LessonBean



# 5.宝宝相关

## 5.1 学习
#### URL:   */api/kid/study*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
### !!打开任何素材前需要调用此方法，每个课件解锁需要保存进度上传自定义flag
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
type | String | 学习类型 LESSON:课件| 是
id | long | 更新type LESSON：课件id |是
flag int | 自定义学习位置| 是 
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
flag | int |学习位置 0:从新开始| 0

# 6.配置相关

## 6.1 主页配置
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

### 返回参数
key| 类型 | 含义 | 示例 
---- | ---- | ---- | ----
BANNER_ZRPD| int |自然拼读 开关/跳转的课包id | 0:不显示(限时免费)/课包id
BANNER_ZXKC| int |主线课程 开关/跳转的课包id | 0:不显示(限时免费)/课包id
BANNER\_LIST\_RG| int |英语儿歌 开关 | 0:不显示(限时免费)
BANNER\_LIST\_GAME| int |互动游戏 开关 | 0:不显示(限时免费)
BANNER\_LIST\_HB| int |英语绘本 开关 | 0:不显示(限时免费)



# 7.文章

## 7.1 发现列表
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
list |List<Object>|  参见附录 ArticleBean

## 7.2 发现点击
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


# 8.订单
## 8.1 贝壳购买
#### URL:   */api/order/buy*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
type | String | 商品类型 UNIT:课包| 是
goodsId | long | 商品id UNIT：课包id| 是
couponId | long | 优惠券id 大于0使用| 否
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
orderNo| String | 订单号









## 附录
### AccountCacheBean
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


### KidBean
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


### LessonBean
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
vip | int | 权限  参见 VIP
unlock | boolean | 是否解锁
auth| boolean | 是否有权限，判断是否购买

### ArticleBean
参数名 | 类型 | 含义 
---- | ---- | ---- 
id | int | 文章id
title| String | 文章标题
describe | String | 描述
recommend | String | 引荐
url | String | 引用文章url
releaseTime | long | 发布时间戳
image | String | 图片路径
color | String | 色号
count | long | 阅读数

### AccountBalanceBean
参数名 | 类型 | 含义 
---- | ---- | ---- 
accountId | long | 用户账户id
amount | Double | 账户总金额
freezeAmount | Double | 账户冻结金额
useableAmount | Double | 真实可用金额

### AccountCouponBean
参数名 | 类型 | 含义 
---- | ---- | ---- 
id | long | 优惠券id
couponId | long | 优惠券模板id
title | String | 标题
accountId | long | 账户id
type | String | 类型 COUPON:优惠券 SALE:折扣券
num |double | COUPON:抵用金额  SALE: 打多少折
fullPrice| double | 满多少金额使用
startTime | long | coupon 使用的开始时间戳
endTime | long | coupon 使用的结束时间戳
status | String | 状态 A:未使用  L:锁定（使用中）
orderNo | String | 使用的订单号

### WEIXINPAYMAP
参数名 | 类型 | 含义 
---- | ---- | ---- 
pay_sign| String | pay_sign
partner_id|String | partner_id
package | String | package
prepay_id | String | prepay_id
nonce_str |String | nonce_str
timestamp | String | 时间戳（10位，秒）





### VIP
数值 | 含义 
----  | ---- 
0| 没有权限
10 | 需要用户注册登录（非游客）
60 | 需要购买






   






   





  






 


  

   

  
 














 










 


      
   




