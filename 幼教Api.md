# 幼教接口

版本号 | 完成日期 | 修改人 | 变更描述
---- | ------- | ----- | -------
1.0.1 | 2018.12.12 | 忠琪 | 去除登录返回的logininfo对象只返回token，宝宝列表添加字段kid，新增接口 2.12 绑定推荐人邀请码，AccountCacheBean 新增字段 askCode,recommendCode


## API请求地址
#### https://bell.beecloud.cn
#### 请求头里面 token 身份认证
#### 返回 resultCode 为 0 时为正常调用


# 1.Auth(以下接口无需token)

## 1.1 游客登录
#### URL:   */api/auth/touristlogin*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
deviceId | String | 设备唯一id|是
deviceType | String | 设备类型 IOS/ANDROID |是


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
token  | String | token | 79767d55b2544d2c8594fecf1c21fa15 
accountId  | long | 游客Id | 123456 

#### result 

```
{
  "resultCode": 0,
  "resultMsg": "登录成功",
  "errorMsg": null,
  "data": {
    "accountId": 107,
    "token": "79767d55b2544d2c8594fecf1c21fa15"
  }
}
```


## 1.2 获取短信验证码
#### URL:   */api/auth/sms*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile | String | 手机号码|是



## 1.3 手机登录
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



## 1.4 获取微信跳转路径
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


## 1.5 微信登录
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


## 1.6 上传图片
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



# 4.课件相关

## 4.1 明细
#### URL:   */api/course/items*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
courseId | long | 课件id | 是
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
items  | List<Object> | 课件明细 | 参见附录 CourseItemBean



# 5.宝宝相关

## 5.1 上传学习记录
#### URL:   */api/kid/study*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
courseitemId | long | 课件明细id | 是
score | int | 分数/成绩 |是
achievement | int | 评分 | 是
timeConsuming | long | 耗时秒 | 是
accuracyRate | double | 正确率 | 是  
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----

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

### 返回参数
key| 类型 | 含义 | 示例 
---- | ---- | ---- | ----
BANNER_ZRPD| int |自然拼读 开关 | 0:不显示(限时免费)
BANNER_ZXKC| int |主线课程 开关 | 0:不显示(限时免费)
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


### CourseItemBean
参数名 | 类型 | 含义 
---- | ---- | ---- 
id  | long | 课件明细id
courseId | long | 课件id
lesson | int | 第几节课
title | String | 标题
describe | String | 描述
image | String | 图片路径
duration | int | 时长 单位：分钟
scoreRule | String | 得分规则
vip | int | 权限  参见 VIP
unlock | boolean | 是否解锁

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
orderId | String | 使用的订单id
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






   






   





  






 


  

   

  
 














 










 


      
   




