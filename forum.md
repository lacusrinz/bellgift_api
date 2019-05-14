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
 &nbsp; &nbsp; [ 1.10回复](#1.10)  
 &nbsp; &nbsp; [ 1.11回复列表](#1.11)  
 &nbsp; &nbsp; [ 1.12回复详情](#1.12)  
 &nbsp; &nbsp; [ 1.13回复删除](#1.13)  
 &nbsp; &nbsp; [ 1.14七牛token获取](#1.14) 
 
 



# <h2 id='1'>1. 论坛</h2>
## <h3 id='1.1'>1.1 社区模块列表</h3>
#### URL:   */api/forum/communities*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
list  | List<Object> | 社区模块列表 | 参见附录 [ForumCommunityBean](#ForumCommunityBean)

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
flag | int | 分类标签  1: 推荐 2：收藏 3：发帖 4：已回复 5:热门帖子(点击数) 6:app专区| 否 
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
#### URL:   */api/forum/communityhome*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
key | String | 社区key | 是


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
community | Object | 社区信息 |参见附录 [ForumCommunityBean](#ForumCommunityBean)
activePostList  | List| 活动帖子列表 | 参见附录 [ForumPostListDto](#ForumPostListDto)


## <h3 id='1.6'>1.6 帖子详情(部分需要登录购买)</h3>
#### URL:   */api/forum/postdetail*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | heard 参数 | token | 否
postId | long | 帖子id | 是
timestamp | long | 时间戳 | 否
sign | String | 签名（规则口口相传）| 否



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
action | int | 1:帖子收藏,2:帖子点赞，3：帖子举报  12:回复点赞 13：回复举报 | 是
tId | long | 帖子id ,回复id | 是
cancel | boolean | true: 取消/撤回  false:(默认)| 


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
imageUrl | String |图片文件路劲 | 否
voiceUrl| String |音频文件路劲| 否
voiceTime| double |音频文件时长 | 否
videoUrl| String |视频文件路劲 | 否
videoImage| String |音频文件截图 | 否


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
flag | int |   2：倒序查看 3：正序查看 | 是
aId | long | 分享人的id,（第一页传, timestamps 失效）第二页起别传,传timestamps
getimestamps | long | 大于该时间戳的数据  配合flag
letimestamps | long | 小于该时间戳的数据  配合flag
limit | int | 分页数量| 否 
skip | int | 分页其实位置| 否
loadrank |boolean |是否加载点赞排名 

### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
reply | Object | 回复对象 |参见附录 [ForumReplyDto](#ForumReplyDto)


## <h3 id='1.12'>1.12 回复详情</h3>
#### URL:   */api/forum/replydetail*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
postId | long | 帖子id | 是
replyId | long | 回复帖子的id | 是
onlyMaster | boolean | 是否只看楼主 true:只看楼主,false(不传) 默认排序| 否
limit | int | 分页数量| 否 
skip | int | 分页其实位置| 否 


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
list | List | 回复对象 |参见附录 [ForumReplyDto](#ForumReplyDto)


## <h3 id='1.13'>1.13 回复删除</h3>
#### URL:   */api/forum/replydelete*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
replyId | long | 回复帖子的id | 是


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----


## <h3 id='1.14'>1.14 七牛token获取</h3>
#### URL:   */api/forum/qtk*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
tk | String | 七牛token|
tp | String | 七牛文件路径域名





## 附录
### <h3 id='ForumCommunityBean'>ForumCommunityBean</h3>
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
context | String |发布摘要
releaseTime | Date | 发布时间
images | String[] | 图片集合
imageCount | int | 图片集合图片数量
videoImage | String | 视频截图
clickCount | long | 点击数量
replyCount | long | 回复数量
appSort| int | app排序权重
appIcon | String | app图标


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
context | String |发布摘要
html | String | 详情html   {{BBS[文件id]}}
collect| boolean |是否收藏
praise | boolean | 是否点赞
report | boolean | 是否举报
sourceMap|Map| 文件对象  文件Id:文件对象 [文件对象](#文件对象)
inApp | boolean | 是否在app内

### <h3 id='文件对象'> 文件对象 </h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
screenshot|String |视频截图
category | 文件类型 | 1：图片 2：视频  3：语音
voiceTime | int | 语音时长
url | String | 文件url



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
replyContext | String |回复上一层回复内容
replyVoice | String | 回复上一层回复语音
replyVideo | String | 回复上一层回复视频
replyVideoImage | String |回复上一层回复视频截图
replyImage | String |回复上一层回复图片
context | String |回复内容
voice | String |回复语音
video | String |回复视频
videoImage | String |回复视频截图
image | String |回复图片
replyCount | long |回复数
praiseCount | long |点赞数
praise | boolean | 是否点赞
report | boolean | 是否举报
replyDate | Date | 回复时间
forumLevel | String | 论坛等级 SPROUTING_NEW:萌新,DAREN:达人
appellation | String | 称号 本月之星
score | double | 评分 （0-5）分
isrank|boolean | 是否排名数据
 


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









 










 


      
   




