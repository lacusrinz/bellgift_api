# 贝尔恩物公众号API

## API请求地址
#### http://182.92.3.98:4589
#### 请求头里面 openid 身份认证
#### 返回 resultCode 为 0 时为正常调用

## 目录
[1.代理申请 ](#1)  
 &nbsp; &nbsp; [ 1.1获取代理信息](#1.1)  
 &nbsp; &nbsp; [ 1.2获取短信验证码](#1.2)  
 &nbsp; &nbsp; [ 1.3 手机短信验证 ](#1.3)  
 &nbsp; &nbsp; [ 1.4 保存代理信息 ](#1.4)  
 &nbsp; &nbsp; [ 1.5 创建推广图片 ](#1.5)     
 &nbsp; &nbsp; [ 1.6 消息列表 ](#1.6)     
 &nbsp; &nbsp; [ 1.7 消息标记已读 ](#1.7)   
 [2.微信API ](#2)  
 &nbsp; &nbsp; [ 2.1微信授权获取code](#2.1)  
 &nbsp; &nbsp; [ 2.2 微信授权获取openid](#2.2)  
 &nbsp; &nbsp; [ 2.3 微信获取accessToken](#2.3)  
 &nbsp; &nbsp; [ 2.4 微信获取用户信息](#2.4)  
 &nbsp; &nbsp; [ 2.5 发送模板消息](#2.5)   
 [3.授权代理接口 ](#3)  
 &nbsp; &nbsp; [ 3.1资金信息](#3.1)  
 &nbsp; &nbsp; [ 3.2提现信息](#3.2)  
 &nbsp; &nbsp; [ 3.3 提现](#3.3)  
 &nbsp; &nbsp; [ 3.4 提现列表](#3.4)  
 &nbsp; &nbsp; [ 3.5 统计](#3.5)  
 
 
 
# <h2 id='1'>1. 代理申请</h2>
## <h3 id='1.1'>1.1 获取代理信息</h3>
#### URL:   /wx/agent/info
#### Method: GET
#### 请求参数格式: json
### 传入参数


### 返回参数
参数名 | 类型 |  含义 | 示例
---- | ---- | ---- | ----
agent  | map | 代理信息 |  如返回结果所示 
status  | string | 代理商状态 |  N 尚未申请 P 待审核 A 成功  I 失败

#### 返回结果

	{
	  "resultCode": 0,
	  "resultMsg": "OK",
	  "errorMsg": null,
	  "data": {
	    "status": "P", //代理商状态
	    "unreadNum" : 2, //消息未读总计
	    "agent": { //代理详细信息
	      "id": 1,
	      "mobile": "159xxxx", //手机号
	      "name": "jason", //姓名
	      "wechat": "xxx", //微信号
	      "province": "江苏", //省
	      "city": "苏州", //市
	      "district": "工业园区", //区
	      "freeTime": 0, //空闲时间
	      "job": 0, //工作职业
	      "friendsNum": 0, //好友数量
	      "openid": "ofEy7uK2JsSOXVpHHYErRPtrdVWg", 
	      "avatar": "https://example.com", //头像
	      "status": "P", //审核状态
	      "reason": "",
	      "remark": "非常赞", // 推广优势
	      "createTime": 1546950315000,
	      "updateTime": 1547005322000,
	      "purchased": "0" //是否购买 0 No  1 Yes
	    }
	  }
	}

## <h3 id='1.2'>1.2 获取短信验证码</h3>
#### URL:   /wx/agent/sendCode
#### Method: POST
#### 请求参数格式: json
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile | String | 手机号码| 是

### 返回结果

	{
	  "resultCode": 0,
	  "resultMsg": "OK",
	  "errorMsg": null,
	  "data": "发送成功"
	}


## <h3 id='1.3'>1.3 手机短信验证</h3>
#### URL:   /wx/agent/verifyCode
#### Method: POST
#### 请求参数格式: json
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile | String | 手机号码|是
code| String | 短信验证码|是

### 返回结果

	{
	  "resultCode": 0,
	  "resultMsg": "OK",
	  "errorMsg": null,
	  "data": "验证成功"
	}


## <h3 id='1.4'>1.4 保存代理信息</h3>
#### URL:   /wx/agent/add
#### Method: POST
#### 请求参数格式: json
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
mobile | String | 手机号码|是
name| String | 姓名|是
wechat| String | 微信号 |是
province| String | 省 |是
city | String | 市 |是
district| String | 区 |是
freeTime| int | 空闲时间 |是
job | int | 职业 |是
friendsNum | int |  好友数 |是
purchased | String | 是否购买 | 1 是 0 否
remark | String | 推广优势 | 是

### 返回结果
	
	{
	  "resultCode": 0,
	  "resultMsg": "OK",
	  "errorMsg": null,
	  "data": "保存成功"
	}

## <h3 id='1.5'>1.5 创建推广图片</h3>
#### URL:   /wx/agent/createCard
#### Method: POST
#### 请求参数格式: json
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
tempId | String | 模板ID。空／不赋值：默认模板，为模板索引：会选择相应的模板文件 | 否
type | String | 操作类型。空／不赋值：默认创建，为“base64”：返回base64内容  | 否

### 返回结果
	
	{
	  "resultCode": 0,
	  "resultMsg": "OK",
	  "errorMsg": null,
	  "data": {"base64" : "xxxxx..."} //返回base64内容
	}

## <h3 id='1.6'>1.6 消息列表</h3>
#### URL:   /wx/notice/list
#### Method: POST
#### 请求参数格式: json
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
skip |	int |	查询起始位置, 默认为0| 否
limit|	int |	查询的条数, 默认为150 | 否

### 返回结果

	{
	  "resultCode": 0,
	  "resultMsg": "OK",
	  "errorMsg": null,
	  "data": {
	    "total": 3,   //通知总数
	    "list": [
	      {
	        "id": 6,
	        "agentId": 173,
	        "type": "WITHDRAW_SUCCESS",
	        "title": "提现成功通知", //通知标题
	        "message": "你的报酬已经提现成功,提现金额202.0元.", //通知详情
	        "mark_read" : "0"  //是否已读 "0" 未读 "1" 已读
	        "createTime": 1546941470000, //创建时间
	        "updateTime": 1546941470000
	      },
	      {
	        "id": 5,
	        "agentId": 173,
	        .....
	      }  
	 }
## <h3 id='1.7'>1.7 消息标记已读</h3>
#### URL:   /wx/notice/markRead
#### Method: POST
#### 请求参数格式: json
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
id | int | 消息记录ID	 | 是 

### 返回结果
	
	{
	  "resultCode": 0,
	  "resultMsg": "OK",
	  "errorMsg": null,
	  "data": "标记成功"
	}

	 
# <h2 id='2'>2 微信API </h2>
## <h3 id='2.1'>2.1 微信授权获取code</h3>
#### URL:   /wx/auth
#### Method: GET

### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
redirectUrl | String | 地址，必须encode| 否

	 
## <h3 id='2.2'>2.2 微信授权获取openid</h3>
#### URL:   /wx/openid
#### Method: GET

### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
code | String | 微信code| 是

### 返回结果

	{
		"resultCode": 0,
		"resultMsg": "OK",
		"errorMsg": null,
		"data": {
			"openid": "xxxxxxx"
		}
	}

## <h3 id='2.3'>2.3 微信获取accessToken</h3>
#### URL:   /wx/accessToken
#### Method: POST
#### 请求参数格式: json

### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
openid | String | 微信openid| 是

### 返回结果

	{
		"resultCode": 0,
		"resultMsg": "OK",
		"errorMsg": null,
		"data": {
			"accessToken": "xxxxxxx"
		}
	}
	
## <h3 id='2.4'>2.4 微信获取用户信息</h3>
#### URL:   /wx/info
#### Method: POST
#### 请求参数格式: json

### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
openid | String | 微信openid| 是

### 返回结果

	{
		"resultCode": 0,
		"resultMsg": "OK",
		"errorMsg": null,
		"data": {
			"openid": "xxxxxxx",
			"headimgurl" : "xxxxx",
			"nickname": "xxxxxxx",
			...
		}
	}	


## <h3 id='2.5'>2.5  发送模板消息</h3>
#### URL:   /wx/sendMsg
#### Method: POST
#### 请求参数格式: json

### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
openid | String | 微信openid| 是
type | String | 消息分类：withdraw 提现，apply 申请 | 是
totalFee | String | 提现金额，单位分 | 否（type= withdraw时必填）

### 返回结果

	{
		"resultCode": 0,
		"resultMsg": "OK",
		"errorMsg": null,
		"data": "发送成功"
	}


# <h2 id='3'>3.授权代理接口</h2>
## <h3 id='3.1'>3.1 资金信息</h3>
#### URL:   /wx/authagent/balance
#### Method: POST
#### 请求参数格式: json
### 传入参数


### 返回参数
参数名 | 类型 |  含义 | 示例
---- | ---- | ---- | ----


#### 返回结果
	{
	  "resultCode": 0,
	  "resultMsg": "OK",
	  "errorMsg": null,
	  "data": {
	    "balance": {
	      "agentId": 999,//代理商id
	      "amount": 12345,// 总的账户金额
	      "freezeAmount": 221,//账户冻结金额
	      "usableAmount": 12124//账户可用金额
	    }
	  }
	}


## <h3 id='3.2'>3.2 提现信息</h3>
#### URL:   /wx/authagent/withdrawinfo
#### Method: POST
#### 请求参数格式: json
### 传入参数


### 返回参数
参数名 | 类型 |  含义 | 示例
---- | ---- | ---- | ----


#### 返回结果
	{
	  "resultCode": 0,
	  "resultMsg": "OK",
	  "errorMsg": null,
	  "data": {
	    "withdrawCount": 7,//提现笔数
	    "withdrawAmount": 829.3//提现总金额
	  }
	}

## <h3 id='3.3'>3.3 提现</h3>
#### URL:   /wx/authagent/withdraw
#### Method: POST
#### 请求参数格式: json
### 传入参数


### 返回参数
参数名 | 类型 |  含义 | 示例
---- | ---- | ---- | ----
amount | double | 提现金额| 是
message | String | 提现备注 | 否

#### 返回结果

	{
	  "resultCode": 0,
	  "resultMsg": "OK",
	  "errorMsg": null,
	  "data": {
	    "billNo": "WDE1D0E324L55934S4" // 提现订单号
	  }
	}


## <h3 id='3.4'>3.4 提现列表</h3>
#### URL:   /wx/authagent/withdrawlist
#### Method: POST
#### 请求参数格式: json
### 传入参数


### 返回参数
参数名 | 类型 |  含义 | 示例
---- | ---- | ---- | ----
status | String | 状态 不传(空)：全部  S:成功 F:失败 P:待处理 PS:非失败| 否
limit | int | 每页显示 | 否
skip | int | 其实位置 | 否

#### 返回结果

	{
	  "resultCode": 0,
	  "resultMsg": "OK",
	  "errorMsg": null,
	  "data": {
	    "list": [
	      {
	        "id": 15, //id
	        "agentId": 999,//代理商id
	        "billNo": "WD60U5O8D3F646P8X9",//提现订单号
	        "amount": 220, // 提现金额
	        "status": "P", //提现状态 P:待处理 S:成功 F:驳回
	        "message": "sdfsdf", // 代理商提现留言
	        "remark": null,// bell 管理员备注 驳回理由
	        "finishTime": null, //订单处理时间
	        "createTime": 1547105836000,//创建日期
	        "updateTime": 1547105836000,//修改时间
	        "payImage": null// 打款凭证
	      }
	    ]
	  }
	}

## <h3 id='3.5'>3.5 统计</h3>
#### URL:   /wx/authagent/report
#### Method: POST
#### 请求参数格式: json
### 传入参数


### 返回参数
参数名 | 类型 |  含义 | 示例
---- | ---- | ---- | ----


#### 返回结果

		{
	  "resultCode": 0,
	  "resultMsg": "OK",
	  "errorMsg": null,
	  "data": {
	    "totalPayCount": 1, //总的邀请支付用户
	    "totalCount": 3,//总的邀请用户数量
	    "list": [
	      {
	        "month": 1546272000000,// 月份时间戳
	        "count": 1,// 月的邀请用户数量
	        "payCount": 1//月的邀请支付用户
	      }
	    ]
	  }
	}
   





  






 


  

   

  
 














 










 


      
   





