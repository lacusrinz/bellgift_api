# 贝尔商城接口

版本号 | 完成日期 |生效时间| 修改人 | 变更描述
---- | ------- | ----- | ----- | -------
1.0.1 | 2019.2.28 | 2019.2.28 15：00 | wdw | 1商品信息，2订单操作


## API请求地址
#### http://182.92.3.98:4590
#### 请求头里面 token 身份认证
#### 返回 resultCode 为 0 时为正常调用

## 目录
[1.商品信息 (需登录)](#1)  
 &nbsp; &nbsp; [ 1.1商品详情](#1.1)  
 &nbsp; &nbsp; [ 1.2商品列表](#1.2)  
 &nbsp; &nbsp; [ 1.3商品图文描述 ](#1.3)  
 
 [2.订单操作（需登录）](#2)  
&nbsp; &nbsp; [ 2.1下单](#2.1)  
&nbsp; &nbsp; [ 2.2取消订单](#2.2)  
&nbsp; &nbsp; [ 2.3订单列表](#2.3)  


<h2 id='1'>1.商品信息 (需登录)</h2>
<h3 id='1.1'>1.1商品详情</h3>

#### URL:   * /api/commodity/detail*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | token | 是
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
thumbnail |string | 缩率图 | http://qimg.hxnews.com/2019/0130/1548847547525.jpg
title |string | 名称 | 贴纸
subtitle |string | 副产品副标题（特点） | `自主品牌 | 包换包退 | 官方直售`
label |string | 主产品标签 | 课程配套教具
activityTitle |string | 活动 | 下单即随机附送贝尔小礼物
specifications |string |产品参数 | `{"品牌":"贝尔恩物英语","材质":"毛绒","尺寸":"10cm X 20cm X 10cm"}`
showPrice |int | 产品价格,单位分 | 37800
category |string | 所属类型 | DICTIONARY
sort |int | 权重 | 1
sales |int | 月销量（可能用不到）| 1234
totalSales | int |总销量 | 89734
status | string |状态 | A   
createTime | long |创建时间| 1551144795000
updateTime | long |修改时间| 1551144795000  
selling | int |待支付商品数量（暂时未用到） | 2   
docId | long |商品图文描述id| 1   
resourceIds | string |商品资源id,数组表示| [1,2,3]   
resources | array |见商品资源详情 |   

### 商品资源详情 
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
id  | long | 商品id | 1
price |int | 产品价格,单位分 | 37800
costPrice |int | 产品成本价格,单位分 | 27800
thumbnail |string | 缩率图 | http://qimg.hxnews.com/2019/0130/1548847547525.jpg
stock |int | 库存 | 2344
title |string | 名称 | 商品1
properties| string | 属性|`{"颜色":"绿色","大小","S号"}`
status | string |状态 | A 
createTime | long |创建时间| 1551144795000
updateTime | long |修改时间| 1551144795000  
selling | int |待支付商品数量（暂时未用到） | 2   
            
<h3 id='1.2'>1.2商品列表</h3>

#### URL:   * /api/commodity*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
hot | int | 热销产品 0:非（默认） 1:是 | 否
limit | int |查询总数，默认20 | 否
skip | int | 分页用到 | 否
type | int | 商品列表必填 ALL/STATIONERY/TOY | 否
sorts | array | 排序方式 | 否

### 排序方式
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
orderField | string | 排序方式，默认创建时间排序 PRICE/TOTALSALES/HOT | 否
orderType | string | 升序/降序，默认升序 ASC/DESC| 否

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
data  | map | 见商品概述 |

### 商品概述
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
id  | long | 商品id | 1
subjectPicture |string | 主图 | http://qimg.hxnews.com/2019/0130/1548847547525.jpg
thumbnail |string | 缩率图 | http://qimg.hxnews.com/2019/0130/1548847547525.jpg
title |string | 名称 | 贴纸
subtitle |string | 副产品副标题（特点） | `自主品牌 | 包换包退 | 官方直售`
label |string | 主产品标签 | 课程配套教具
showPrice |int | 产品价格,单位分 | 37800
totalSales |int | 销量 | DICTIONARY

<h3 id='1.3'>1.3商品图文描述</h3>

#### URL:   * /api/commodity/doc*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
commodityId | long | 商品id | 是
version | string |版本 | 否

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
data  | map | 见商品图文详情 |

### 商品图文详情
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
id  | long | 商品图文详情id | 1
title  | string | 标题 | 课本
context  | string | 内容 | `<p><img src="http://preqiniu.beecloud.cn/1dcc0d473dd1426087addf302fe4c2b5"/></p><p><span style="text-decoration: underline;">三扥结婚</span></p><ol class=" list-paddingleft-2" style="list-style-type: decimal;"><li><p>23</p><p>&nbsp; &nbsp; &nbsp;三扥看带坑距</p></li></ol><p>sdf<span style="color: rgb(118, 146, 60);">sdfsdf<span style="color: rgb(255, 255, 0);">dsfgdfg<span style="color: rgb(36, 64, 97);">dsg</span></span></span><br/></p><p><br/></p>`
version  | string | 版本 | 1
status  | string | 状态 | A
createTime | long |创建时间| 1551144795000
updateTime | long |修改时间| 1551144795000  


<h2 id='2'>2.订单操作 (需登录)</h2>
<h3 id='2.1'>2.1下单</h3>

#### URL:   * /api/order/create*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
city | string | 市 | 是
county | string |县 | 是
province | string |省 | 是
road | string |街道 | 是
detail | string |详情 | 否
name | string |名称 | 是
phone | string |电话 | 是
remark | string |备注 | 否
commonCouponId | long |通用优惠券 | 否
couponIds | array |优惠券 | 否
disAmount |  int |优惠金额 | 否
freightCost | int |运费 | 是
payAmount | int |支付费用 | 是
totalAmount | int |总费用 | 是
totalNum | int |总数量 | 是
orders | array | 见商品资源信息 | 是
  

### 商品资源信息 
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
commodityId | long |商品id | 是
resourceId | long | 商品资源id | 是
couponId | long |优惠券id| 否
num | int |数量 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
orderId | long | 订单id | 1
  
<h3 id='2.2'>2.2取消订单</h3>

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

<h3 id='2.3'>2.3订单列表</h3>

#### URL:   * /api/order *
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
orderStatus | string |订单状态 PAYING(待付款)/CANCEL/PAID（待发货）/SENT（已发货）/COMPLETED（已完成） | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
id | long | 订单id | 1
accountId | long | 账号id | 1
orderNo | long |订单号 | BS3332L028Q9B952E3
remark | string |备注|remark  
totalNum | int | 购买数量 | 2 
couponId |long| 优惠券 | 111 
ip | string | ip |0:0:0:0:0:0:0:1  
totalAmount  | int | 总价格 | 14000 
disAmount  | int | 优惠价格 | 100 
payAmount  | int | 支付金额 |2000 
freightCost  | int | 运费 | 1000 
deliveryNo  | string | 快递单号 |SF23048832234 
deliveryName  | long | 快递名称 | 顺丰快递 
finishTime  | long | 交易完成时间 | 1551321146000 
province | string | 省 |江苏  
city | string|市 |苏州  
county | string|县区 |工业园区  
road | string|街道 |若水路  
detail | string|详细地址 |H栋  
phone | string|手机号 |15209090909  
name | string|姓名 |wdw 
outerTradeNo  | string | 外部交易号 | WX934r3jdewr3 
orderStatus | string | 订单状态 |CANCEL  
status | string |状态 |A  
createTime  | long | 订单创建时间 |1551232090000 
updateTime  | long | 修改时间 |1551321146000 
leftTime | long | 支付剩余时间| 60 










  

   

  
 














 










 


      
   




