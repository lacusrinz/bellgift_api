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
list  | List<Object> | 社区模块列表 | 参见附录 [HotPostDto](#HotPostDto)


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
list  | List<Object> | 社区模块列表 | 参见附录 [ForumPostListDto](#ForumPostListDto)



## <h3 id='1.4'>1.4 权限列表</h3>
#### URL:   */api/forum/authlist*
#### Method: *POST*
#### 请求参数格式: *JSON: Map*
### 传入参数
参数名 | 类型 | 含义  | 是否必填
---- | ---- | ---- | ----
token | String | heard 参数| 否 


### 返回参数
参数名 | 类型 | 含义 | 示例
---- | ---- | ---- | ----
KIDSONG  | List<Long> | 儿歌权限id集合 | 
UNIT  | List<Long> | 课包权限id集合 | 
PICTUREBOOK  | List<Long> | 绘本权限id集合 | 







## 附录
### <h3 id='ForumCommonityBean'>ForumCommonityBean</h3>
参数名 | 类型 | 含义 
---- | ---- | ---- 
key | String | 社区key
title| String | 社区名称
icon| String | 社区图标
describe| String | 社区描述


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
context | String |发布内容
releaseTime | Date | 发布时间
image | String | 单张图片url
images | String[] | 图片集合
imageCount | int | 图片集合图片数量
videoImage | String | 视频截图
clickCount | long | 点击数量
replyCount | long | 回复数量



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









 










 


      
   




