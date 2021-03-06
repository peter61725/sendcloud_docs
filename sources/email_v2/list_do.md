
地址列表为用户批量发送时使用.
    
你可以使用 API 对地址列表进行查询, 添加, 修改, 删除操作.

也可以对地址列表中地址成员进行查询, 添加, 修改, 删除操作.
    
- - -

##查询地址列表 ( 批量查询 )
    
**URL**    
```
http://api.sendcloud.net/apiv2/addresslist/list
```
    
**HTTP请求方式** 
```bash
post    get
```
    
**参数说明**
    
|参数|类型|必须|说明|
|:---|:---|:---|:---|
|apiUser|string|是|API_USER|
|apiKey|string|是|API_KEY|
|address|list|否|别名地址的列表, 多个用 `;` 分隔|
|start|int|否|查询起始位置, 取值区间 [0-], 默认为 0|
|limit|int|否|查询个数, 取值区间 [0-100], 默认为 100|
    
**请求示例**    
```
http://api.sendcloud.net/apiv2/addresslist/list?apiUser=***&apiKey=***&limit=2
```
    
**返回值说明**
    
|参数|说明|
|:---|:---| 
|name|地址列表的名称|
|address|列表别称地址, 使用该别称地址进行调用, 格式为xxx@maillist.sendcloud.org|
|memberCount|地址列表包含的地址个数|
|description|地址列表描述|
|listType|地址列表类型|
|gmtCreated|地址列表创建时间|
|gmtUpdated|地址列表修改时间|
    
**返回值示例**    
```
{
    statusCode: 200,
    info: {
        total: 1,
        count: 1,
        dataList: [{
            gmtCreated: "2015-09-15 20:29:01",
            gmtUpdated: "2015-09-15 20:29:01",
            address: "developers4@sendcloud.com",
            description: "desc",
            listType: 0,
            memberCount: 0,
            name: "211"
        }]
    },
    message: "请求成功",
    result: true
}

```

- - -

##添加地址列表
    
**URL**
```
http://api.sendcloud.net/apiv2/addresslist/add
```
    
**HTTP请求方式**
```bash
post    get
```
    
**参数说明**
    
|参数|类型|必须|说明|
|:---|:---|:---|:---|
|apiUser|string|是|API_USER|
|apiKey|string|是|API_KEY|
|address|string|是|别称地址, 使用该别称地址进行调用, 格式为xxx@maillist.sendcloud.org|
|name|string|是|列表名称|
|desc|string|否|对列表的描述信息|
|listType|int|否|列表的类型. 0: 普通地址列表, 默认为0|
    
**请求示例**    
```
http://api.sendcloud.net/apiv2/addresslist/add?apiUser=***&apiKey=***&address=justfortest@maillist.sendcloud.org&name=testlist&desc=test
```
    
**返回值说明**
    
|参数|说明|
|:---|:---| 
|address|别称地址, 使用该别称地址进行调用|
|memberCount|列表中地址数|
|name|列表名称|
|description|列表描述信息|
|listType|地址列表类型|
|gmtCreated|地址列表创建时间|
|gmtUpdated|地址列表修改时间|

**返回值示例**    
```
{
    statusCode: 200,
    info: {
        data: {
            gmtCreated: "2015-09-28 17:59:15",
            gmtUpdated: "2015-09-28 17:59:15",
            address: "developers41@sendcloud.com",
            memberCount: 0,
            description: "41",
            listType: 0,
            name: "developer41"
        }
    },
    message: "请求成功",
    result: true
}
```
- - -

##删除地址列表

**URL**
```
http://api.sendcloud.net/apiv2/addresslist/delete
```
    
**HTTP请求方式**
```bash
post    get
```
    
**参数说明**
    
|参数|类型|必须|说明|
|:---|:---|:---|:---|
|apiUser|string|是|API_USER|
|apiKey|string|是|API_KEY|
|address|string|是|别称地址, 使用该别称地址进行调用, 格式为xxx@maillist.sendcloud.org|
    
**请求示例**    
```
http://api.sendcloud.net/apiv2/addresslist/delete?apiUser=***&apiKey=***&address=newtest@maillist.sendcloud.org
```
    
**返回值说明**

|参数|说明|
|:---|:---|
|count|成功删除的个数|
    
**返回值示例**
```
{
    statusCode: 200,
    info: {
        count: 1
    },
    message: "请求成功",
    result: true
}
```
    
- - -
##修改地址列表

**URL**
```
http://api.sendcloud.net/apiv2/addresslist/update
```
    
**HTTP请求方式**
```bash
post    get
```
    
**参数说明**
    
|参数|类型|必须|说明|
|:---|:---|:---|:---|
|apiUser|string|是|API_USER|
|apiKey|string|是|API_KEY|
|address|string|是|别称地址, 使用该别称地址进行调用, 格式为xxx@maillist.sendcloud.org|
|newAddress|string|否|修改后的别称地址|
|name|string|否|修改后的列表名称|
|desc|string|否|修改后的列表描述信息|
    
**说明**
```
参数须包含【newAddress】或者【name】或者【description】的组合    
```
    
**请求示例**    
```
http://api.sendcloud.net/apiv2/addresslist/update?apiUser=***&apiKey=***&address=justfortest@maillist.sendcloud.org&name=newtest
```
    
**返回值说明**

|参数|说明|
|:---|:---|
|count|成功修改的个数|
    
**返回值示例**
```
{
    statusCode: 200,
    info: {
        count: 1
    },
    message: "请求成功",
    result: true
}
    
```
    
- - -
    
##查询列表成员 ( 批量查询 )
    
**URL**
```
http://api.sendcloud.net/apiv2/addressmember/list
```
    
**HTTP请求方式**
```bash
post    get
```
    
**参数说明**
    
|参数|类型|必须|说明|
|:---|:---|:---|:---|
|apiUser|string|是|API_USER|
|apiKey|string|是|API_KEY|
|address|string|是|地址列表的别称地址|    
|start|int|否|查询起始位置, 取值区间 [0-], 默认为 0|
|limit|int|否|查询个数, 取值区间 [0-100], 默认为 100|
    
**请求示例**
```
http://api.sendcloud.net/apiv2/addressmember/list?apiUser=***&apiKey=***&address=newtest@maillist.sendcloud.org
```        
    
**返回值说明**
    
|参数|说明|
|:---|:---|
|gmtCreated|成员创建时间|
|gmtUpdated|成员修改时间|
|address|所属地址列表|
|member|成员邮件地址|
|name|成员姓名|
|vars|变量|
    
**返回值示例**
```
{
  "statusCode": 200,
  "info": {
    "dataList": [
      {
        "gmtCreated": "2015-04-30 11:15:43",
        "gmtUpdated": "2015-04-30 11:15:43",
        "address": "test@maillist.sendcloud.org",
        "member": "001@160it.com",
        "name": "001",
        "vars": ""
      },
      {
        "gmtCreated": "2015-04-30 11:17:01",
        "gmtUpdated": "2015-04-30 11:17:01",
        "address": "test@maillist.sendcloud.org",
        "member": "01@mail.yedao.cc",
        "name": "002",
        "vars": ""
      },
      {
        "gmtCreated": "2015-04-30 11:16:41",
        "gmtUpdated": "2015-04-30 11:16:41",
        "address": "test@maillist.sendcloud.org",
        "member": "057966@gmail.com",
        "vars": ""
      }
    ],
    "total": 11378,
    "count": 3
  },
  "message": "请求成功",
  "result": true
}
```

- - -
    
##查询列表成员
    
**URL**
```
http://api.sendcloud.net/apiv2/addressmember/get
```
    
**HTTP请求方式**
```bash
post    get
```
    
**参数说明**
    
|参数|类型|必须|说明|
|:---|:---|:---|:---|
|apiUser|string|是|API_USER|
|apiKey|string|是|API_KEY|
|address|string|是|地址列表的别称地址|    
|members|list|是|列表成员地址|    
    
**请求示例**
```
http://api.sendcloud.net/apiv2/addressmember/get?apiUser=***&apiKey=***&address=newtest@maillist.sendcloud.org&members=ben@ifaxin.com
```        
    
**返回值说明**
    
|参数|说明|
|:---|:---|
|gmtCreated|成员创建时间|
|gmtUpdated|成员修改时间|
|address|所属地址列表|
|member|成员邮件地址|
|name|成员姓名|
|vars|变量|
    
**返回值示例**
```
{
  "statusCode": 200,
  "message": "请求成功",
  "result": true,
  "info": {
    "dataList": [
      {
        "gmtCreated": "2015-04-30 11:15:43",
        "gmtUpdated": "2015-04-30 11:15:43",
        "address": "***",
        "member": "001@160it.com",
        "name": "001",
        "vars": ""
      }
    ],
    "count": 1
  }
}
```

- - -

##添加列表成员
    
**URL**
```
http://api.sendcloud.net/apiv2/addressmember/add
```
     
**HTTP请求方式**
```bash
post    get
```
    
**参数说明**
    
|参数|类型|必须|说明|
|:---|:---|:---|:---|
|apiUser|string|是|API_USER|
|apiKey|string|是|API_KEY|
|address|string|是|地址列表的别称地址|    
|members|list|是|需要添加成员的地址, 多个地址用 `;` 分隔|
|names|list|否|地址成员姓名, 多个地址用 `;` 分隔|    
|vars|list|否|替换变量, 与 members 一一对应, 变量格式为 {"money":"1000"} , 多个用 `;` 分隔|

**说明**
```
1. 每次请求最多可以添加1000个成员
2. 如果包含 vars 变量, 则必须与 members 的成员数量一致
3. 添加 vars 变量, 注意 key 不需要 带上 '%'
4. vars 变量中, key 为 name 的变量会被参数 name 覆盖
5. 地址列表发送时, 可以使用全局变量 recipient, 值为收件人的邮箱地址
```
    
**请求示例**
```
http://api.sendcloud.net/apiv2/addressmember/add?apiUser=***&apiKey=***&address=yourlist@maillist.sendcloud.org&members=1@1.com;2@2.com&vars={"money":"99"};{"money":"900"}
```
    
**返回值说明**
    
|参数|说明|
|:---|:---|
|count|添加成功的地址数|
    
**返回值示例**
    
```
{
    statusCode: 200,
    info: {
        count: 2
    },
    message: "请求成功",
    result: true
}
```
    
- - -
    
##修改列表成员
    
**URL**
```
http://api.sendcloud.net/apiv2/addressmember/update
```
    
**HTTP请求方式**
```bash
post    get
```
    
**参数说明**
    
|参数|类型|必须|说明|
|:---|:---|:---|:---|
|apiUser|string|是|API_USER|
|apiKey|string|是|API_KEY|
|address|string|是|地址列表的别称地址|    
|members|list|是|需要更新成员的旧地址, 多个地址用 `;` 分隔|
|newMembers|list|是|需要更新成员的新地址, 多个地址用 `;` 分隔,并且必须和members中的成员一一对应|
|names|list|否|地址成员姓名, 多个地址用 `;` 分隔|    
|vars|list|否|替换变量, 与 members 一一对应, 变量格式为 {"money":"1000"} , 多个用 `;` 分隔|

**说明**
```
1. 每次请求最多可以修改1000个成员
```
    
**请求示例**
```
http://api.sendcloud.net/apiv2/addressmember/update?apiUser=***&apiKey=***&address=yourlist@maillist.sendcloud.org&members=1@1.com;2@2.com&vars={"money":"199"};{"money":"1900"}
```
    
**返回值说明**
    
|参数|说明|
|:---|:---|
|count|成功修改地址数|
    
**返回值示例**
```
{
    statusCode: 200,
    info: {
        count: 2
    },
    message: "请求成功",
    result: true
}
```
    
- - -
    
##删除列表成员
   
**URL**
```
http://api.sendcloud.net/apiv2/addressmember/delete
```
    
**HTTP请求方式**
```bash
post    get
```
    
**参数说明**
    
|参数|类型|必须|说明|
|:---|:---|:---|:---|
|apiUser|string|是|API_USER|
|apiKey|string|是|API_KEY|
|address|string|是|地址列表的别称地址|    
|members|list|是|需要删除成员的地址, 多个地址用 `;` 分隔|
    
**请求示例**
```
http://api.sendcloud.net/apiv2/addressmember/delete?apiUser=***&apiKey=***&address=newtest@maillist.sendcloud.org&members=3@3.com;4@4.com
```
   
**返回值说明**
    
|参数|说明|
|:---|:---|
|count|成功删除地址数|
    
**返回值示例**
```
{
    statusCode: 200,
    info: {
        count: 2
    },
    message: "请求成功",
    result: true
}
```

