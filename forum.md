# 幼教社区接口



## API请求地址
#### https://bellapi.beecloud.cn
#### 返回 resultCode 为 0 时为正常调用
#### 测试 token ： e93c551329e44111b02a030e1c492ffd

## 目录
[1.论坛](#1)  
 &nbsp; &nbsp; [ 1.1社区模块列表](#1.1)  
 &nbsp; &nbsp; [ 1.2热门帖子列表](#1.2)  
 &nbsp; &nbsp; [ 1.3帖子列表](#1.3)  
 &nbsp; &nbsp; [ 1.4权限列表](#1.4)  
 &nbsp; &nbsp; [ 1.5社区主页](#1.5)  
 &nbsp; &nbsp; [ 1.6帖子详情(部分需要登录购买)](#1.6)  
 &nbsp; &nbsp; [ 1.7论坛综合事件](#1.7)  
 &nbsp; &nbsp; [ 1.8上传文件](#1.8)  
 &nbsp; &nbsp; [ 1.9删除文件](#1.9)  
 &nbsp; &nbsp; [ 1.10回复](#1.10)  
 &nbsp; &nbsp; [ 1.11回复列表](#1.11) 
 



# <h2 id='1'>1. 论坛</h2>
## <h3 id='1.1'>1.1 社区模块列表</h3>
#### URL:   */api/forum/commonities*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
list  | List<Object> | 社区模块列表 | 参见附录 [ForumCommonityBean](#ForumCommonityBean)

## <h3 id='1.2'>1.2 热门帖子列表</h3>
#### URL:   */api/forum/hotpost*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
list  | List| 社区模块列表 | 参见附录 [HotPostDto](#HotPostDto)


## <h3 id='1.3'>1.3 帖子列表</h3>
#### URL:   */api/forum/postlist*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
flag | int | 分类标签  1: 推荐 2：收藏 3：发帖 4：已回复| 否 
key | String | 社区key| 否 
vip | int | 参见 [VIP](#VIP)  不限权限的 不传或传null,别传0| 否 
loadReplyCount|boolean | 是否加载回复数 true:加载(默认)|否
searchKey | String | 搜索关键字 | 否
limit | int | 分页数量| 否 
skip | int | 分页其实位置| 否 

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
list  | List| 帖子列表 | 参见附录 [ForumPostListDto](#ForumPostListDto)



## <h3 id='1.4'>1.4 权限列表</h3>
#### URL:   */api/forum/authlist*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
KIDSONG  | List<Long> | 儿歌权限id集合 | 
UNIT  | List<Long> | 课包权限id集合 | 
PICTUREBOOK  | List<Long> | 绘本权限id集合 | 


## <h3 id='1.5'>1.5 社区主页</h3>
#### URL:   */api/forum/commonityhome*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
key | String | 社区key | 是


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
commonity | Object | 社区信息 |参见附录 [ForumCommonityBean](#ForumCommonityBean)
activePostList  | List| 活动帖子列表 | 参见附录 [ForumPostListDto](#ForumPostListDto)


## <h3 id='1.6'>1.6 帖子详情(部分需要登录购买)</h3>
#### URL:   */api/forum/commonityhome*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | heard 参数 | token | 否
postId | long | 帖子id | 是


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
post | Object | 帖子详情信息 |参见附录 [ForumPostDetailDto](#ForumPostDetailDto)


## <h3 id='1.7'>1.7 论坛综合事件</h3>
#### URL:   */api/forum/action*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
action | int | 1:帖子收藏,2:帖子点赞，3：帖子举报  13：回复举报 | 是
tId | long | 帖子id ,回复id | 是
cancel | boolean | true: 取消/撤回  false:(默认)| 


### 返回参数


##  <h3 id='1.8'>1.8 上传文件</h3>
#### URL:   */api/forum/uploadfile*
#### Method: *POST*
#### 请求参数格式: *form-data* !!!!!
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
file | File | 文件 | 是

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
fileId | long | 上传文件id |


## <h3 id='1.9'>1.9 删除文件</h3>
#### URL:   */api/forum/action*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
fileId | long | 文件id | 是

### 返回参数


## <h3 id='1.10'>1.10 回复</h3>
#### URL:   */api/forum/reply*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
postId | long | 帖子id | 是
replyId | long | 上级回复id | 否
context | String | 回复内容 | 否
imageFileId | long |图片文件id | 否
voiceFileId| long |音频文件id | 否
videoFileId| long |视频文件id | 否


### 返回参数

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
reply | Object | 回复对象 |参见附录 [ForumReplyDto](#ForumReplyDto)


## <h3 id='1.11'>1.11 回复列表</h3>
#### URL:   */api/forum/replylist*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
postId | long | 帖子id | 是
flag | int | 1: 只看楼主  2：倒序查看 3：正序查看 | 是
limit | int | 分页数量| 否 
skip | int | 分页其实位置| 否 

 


### 返回参数

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
list | List | 回复对象 |参见附录 [ForumReplyDto](#ForumReplyDto)












## 附录
### <h3 id='ForumCommonityBean'>ForumCommonityBean</h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
key | String | 社区key
title| String | 社区名称
icon| String | 社区图标
describe| String | 社区描述
postCount | long | 帖子数量


### <h3 id='HotPostDto'>HotPostDto</h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
key | String | 社区key
postId|Long|帖子id
rise | String| 帖子抬头
title| String | 帖子标题
count| long | 参与人数
vip | int | 权限 参见 [VIP](#VIP)
authType | String | 权限类型 参见 [AuthType](#AuthType)
authId | Long | 权限id（需购买指定素材）
avatars | List<String> | 参与人员头像url list


### <h3 id='ForumPostListDto'>ForumPostListDto</h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
key | String | 社区key
postId|Long|帖子id
rise | String| 帖子抬头
title| String | 帖子标题
vip | int | 权限 参见 [VIP](#VIP)
authType | String | 权限类型 参见 [AuthType](#AuthType)
authId | Long | 权限id（需购买指定素材）
label | int | 标签 权限 参见 [LABEL](#LABEL)
authorId|long | 发布者id 
avatar | String | 发布者头像
nickname| String | 发布者昵称
context | String |发布内容
releaseTime | Date | 发布时间
image | String | 单张图片url
images | String[] | 图片集合
imageCount | int | 图片集合图片数量
videoImage | String | 视频截图
clickCount | long | 点击数量
replyCount | long | 回复数量


### <h3 id='ForumPostDetailDto'>ForumPostDetailDto</h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
key | String | 社区key
postId|Long|帖子id
rise | String| 帖子抬头
title| String | 帖子标题
label | int | 标签 权限 参见 [LABEL](#LABEL)
authorId|long | 发布者id 
avatar | String | 发布者头像
nickname| String | 发布者昵称
releaseTime | Date | 发布时间
clickCount | long | 点击数量
replyCount | long | 回复数量
html | String | 详情html 
collect| boolean |是否收藏
praise | boolean | 是否点赞
report | boolean | 是否举报



### <h3 id='ForumReplyDto'> ForumReplyDto </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
key | String | 社区key
postId|Long|帖子id
replyId | Long | 当条回复id
floor | int | 楼层
accountId | long |回复者id
nickname| String | 回复者昵称
avatar| String | 回复者头像
replyAccountId| long |回复上一层回复者的id
replyNickname| String |回复上一层回复者的昵称
replyAvatar| String |回复上一层回复者的头像
context | String |回复内容
voice | String |回复语音
video | String |回复视频
videoImage | String |回复视频截图
image | String |回复图片
childs  |List|子回复集合 [ForumReplyDto](#ForumReplyDto)
 


### <h3 id='VIP'> VIP </h3>
数值 | 含义 
----  | ---- 
0|  没有权限限制
60 | 需要购买

### <h3 id='LABEL'> LABEL </h3>
数值 | 含义 
----  | ---- 
1|  置顶
2 | 活动

### <h3 id='AuthType'> AuthType </h3>
TYPE | 含义 
----  | ---- 
UNIT|  课包
PICTUREBOOK | 绘本
KIDSONG | 儿歌









 










 


      
   




