# 实验5:图书管理系统数据库设计与界面设计
|  姓名  |      学号      |     班级      |
| :--: | :----------: | :---------: |
|  谢颜浩  | 201510414221 | 软工2班 |

## 1.数据库表设计

## 1.1. Book表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|ISBN|varchar2(14)|主键|否| | | 为书本印刷的ISBN号|
|bookname|varchar2(60)| |否||||
|author|varchar2(50)| |是||||# 实验5:图书管理系统数据库设计与界面设计
|  姓名  |      学号      |     班级      |
| :--: | :----------: | :---------: |
|  谢颜浩  | 201510414221 | 软工2班 |

## 1.数据库表设计

## 1.1. 预约书籍表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|BookNo|varchar2(14)||否| | | 预约的书籍|
|PersonNo|varchar2(60)|主键 |否||||愉悦的人员
|BookingTime|varchar2(50)| |否|||预约时间|


## 1.2. 借出书籍表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|BookNo|varchar2(32)|主键|否||||
|PersonNo|varchar2(32)| |否| '管理员'|||
|LendTime|varchar2(32)| |否| '123456'| ||
|LeastTime|varchar2(32)| |否| '123456'| ||

## 1.3. 归还书籍表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|BookNo|varchar2(32)|主键|否||||
|PersonNo|varchar2(32)| |否| | ||
|ReturnTime|varchar2(32)| |否| '123456'| | 为空时密码为123456，密码采用32位MD5加密|
|Fine|varchar2(50)| |是| | |该读者所在学院| 

## 1.4. 书籍表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|BookNo|varchar2(32)|主键、外键|否|| |Reader.userID|
|BookName|varchar2(50)| |否| | |学生专业|
|Arthur|varchar2(10)| |否| | |学生年级|
|ISBN|varchar2(32)|主键、外键|否|| |Reader.userID|
|Publish|varchar2(50)| |否| | |学生专业|
|price|varchar2(10)| |否| | |学生年级|
|BookState|varchar2(50)| |否| | |学生专业|
|BookClass|varchar2(10)| |否| | |学生年级|
## 1.5. 借书卡表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|CardNo|varchar2(32)|主键、外键|否| |Reader.userID||
|PersonNo|varchar2(50)| |否| | |老师职称|
|LostTag|varchar2(50)| |否| | |老师职称|

## 1.6. 借书者表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|PersonNo|varchar2(32)|主键|否| | ||
|Password|varchar2(32)|外键|否| |Administrator.userID||
|PersonInfo|varchar2(14)|外键|否| |Book.ISBN||
## 1.7. 普通管理员表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|AdminID|varchar2(32)|主键|否| | ||
|Password|varchar2(32)|外键|否| |Reader.userID||

## 1.8. 系统管理员表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|RootId|varchar2(32)|主键|否| | ||
|Password|varchar2(32)|外键|否| |Reader.userID||

***

## 2. 界面设计
## 2.1. 图书归还界面设计
![pic1](pic.PNG)
- 用例图参见：图书归还用例
- 类图参见：Book类，Reader类，LendRecord类
- 顺序图参见：图书归还顺序图
- API接口如下：

1. 获取用户未归还图书API

- 功能：用于获取某用户全部未归还图书
- 请求地址： http://localhost/v1/api/get_unreturnbooks_4reader
- 请求方法：POST
- 请求参数：

|参数名称|必填|说明|
|:-------:|:-------------: | :----------:|
|userID|是|根据读者编号获取其未归还图书列表 |

- 返回实例：
```
{
	"unreturnbooks_4reader": [{
		"ISBN": "9787513506915",
		"bookname": "翻译美学理论",
		"author": "刘宓庆",
		"startDate": "2018-03-03",
		"isRenew": "true,
		"activeTime": 30,
		"returnDate": null
	}, {
        "ISBN": "9787544627634",
		"bookname": "翻译能力培养",
		"author": "舍夫纳",
		"startDate": "2018-03-15",
		"isRenew": true,
		"activeTime": 30,
		"returnDate": null
	}, {
        "ISBN": "9787310028306",
		"bookname": "当代国外翻译理论导读",
		"author": "谢天振",
		"startDate": "2018-04-21",
		"isRenew": false,
		"activeTime": 30,
		"returnDate": null
	}],
    "readerLendBook": {
        "userID": "201510418736",
        "username": "螺蛳粉",
        "major": "食品加工",
        "grade": "2015级"
    },
	"length": 3,
	"status": 1
}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|unreturnbooks_4reader|该用户未归还图书的集合|
|readerLendBook|该读者的用户信息|
|length|未归还图书集合的长度|
|status|获取结果，为1时表示成功获取，为0时表示获取失败|

2. 归还图书API
- 功能：用于向系统提交需要归还的图书项目
- 请求地址： http://localhost/v1/api/return_books
- 请求方法：POST
- 请求参数：

|参数名称|必填|说明|
|:-------:|:-------------: | :----------:|
|userID|是|根据读者编号归还其借阅图书 |
|ISBN|是|待归还图书的ISBN号 |

- 返回实例：
```
{
	"length": 2,
	"status": 1
}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|length|成功归还图书数量|
|status|获取执行结果，为1时表示都成功执行，为0时表示存在执行失败|


 

|publisher|varchar2(100)| |是||||
|price|double| |否|0.0|||
|totalNum|int| |否|0| |即该图书库存的总量|
|restNum|int| |否|0| |目前可借的图书量|

## 1.2. Administrator表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|userID|varchar2(32)|主键|否||||
|username|varchar2(32)| |否| '管理员'|||
|password|varchar2(32)| |否| '123456'| |为空时密码为123456，密码采用32位MD5加密|

## 1.3. Reader表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|userID|varchar2(32)|主键|否||||
|username|varchar2(32)| |否| | ||
|password|varchar2(32)| |否| '123456'| | 为空时密码为123456，密码采用32位MD5加密|
|academy|varchar2(50)| |是| | |该读者所在学院| 

## 1.4. Student表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|userID|varchar2(32)|主键、外键|否|| |Reader.userID|
|major|varchar2(50)| |否| | |学生专业|
|grade|varchar2(10)| |否| | |学生年级|

## 1.5. Teacher表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|userID|varchar2(32)|主键、外键|否| |Reader.userID||
|positionalTitle|varchar2(50)| |否| | |老师职称|

## 1.6. ManageBookRecord表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|manageBookRecordID|varchar2(32)|主键|否| | ||
|userID|varchar2(32)|外键|否| |Administrator.userID||
|ISBN|varchar2(14)|外键|否| |Book.ISBN||
|manageDate|datetime| |否| | |管理图书的时间|
|action|varchar2(10)| |否| | |管理图书的动作，add添加图书，delete为删除图书，update为更新图书信息|
|manegeNum|int| |否| | |管理图书的数量|

## 1.7. LendRecord表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|lendRecordRecordID|varchar2(32)|主键|否| | ||
|userID|varchar2(32)|外键|否| |Reader.userID||
|ISBN|varchar2(14)|外键|否| |Book.ISBN||
|startDate|datetime| |否| | |借阅图书的开始时间|
|activeTime|int| |否|30| |一次借阅时间长度，单位为天|
|isRenew|tinyint| |否|0| 0-1|是否续借图书，1为已续借，0为未续借|
|returnDate|datetime| |是| | |归还图书的时间，若为空代表未归还|

## 1.8. BookRecord表
|字段|类型|主键，外键|可以为空|默认值|约束|说明|
|:-------:|:-------------:|:------:|:----:|:---:|:----:|:-----|
|bookRecordRecordID|varchar2(32)|主键|否| | ||
|userID|varchar2(32)|外键|否| |Reader.userID||
|ISBN|varchar2(14)|外键|否| |Book.ISBN||
|bookDate|datetime| |否| | |预定图书的时间|
|activeTime|int| |否|7| |预定图书的有效期，单位为天|
|isCannel|tinyint| |否|0| 0-1|此预订是否取消，1表示已取消，0表示未取消|
***

## 2. 界面设计
## 2.1. 图书归还界面设计
![pic1](pic.PNG)
- 用例图参见：图书归还用例
- 类图参见：Book类，Reader类，LendRecord类
- 顺序图参见：图书归还顺序图
- API接口如下：

1. 获取用户未归还图书API

- 功能：用于获取某用户全部未归还图书
- 请求地址： http://localhost/v1/api/get_unreturnbooks_4reader
- 请求方法：POST
- 请求参数：

|参数名称|必填|说明|
|:-------:|:-------------: | :----------:|
|userID|是|根据读者编号获取其未归还图书列表 |

- 返回实例：
```
{
	"unreturnbooks_4reader": [{
		"ISBN": "9787513506915",
		"bookname": "翻译美学理论",
		"author": "刘宓庆",
		"startDate": "2018-03-03",
		"isRenew": "true,
		"activeTime": 30,
		"returnDate": null
	}, {
        "ISBN": "9787544627634",
		"bookname": "翻译能力培养",
		"author": "舍夫纳",
		"startDate": "2018-03-15",
		"isRenew": true,
		"activeTime": 30,
		"returnDate": null
	}, {
        "ISBN": "9787310028306",
		"bookname": "当代国外翻译理论导读",
		"author": "谢天振",
		"startDate": "2018-04-21",
		"isRenew": false,
		"activeTime": 30,
		"returnDate": null
	}],
    "readerLendBook": {
        "userID": "201510418736",
        "username": "螺蛳粉",
        "major": "食品加工",
        "grade": "2015级"
    },
	"length": 3,
	"status": 1
}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|unreturnbooks_4reader|该用户未归还图书的集合|
|readerLendBook|该读者的用户信息|
|length|未归还图书集合的长度|
|status|获取结果，为1时表示成功获取，为0时表示获取失败|

2. 归还图书API
- 功能：用于向系统提交需要归还的图书项目
- 请求地址： http://localhost/v1/api/return_books
- 请求方法：POST
- 请求参数：

|参数名称|必填|说明|
|:-------:|:-------------: | :----------:|
|userID|是|根据读者编号归还其借阅图书 |
|ISBN|是|待归还图书的ISBN号 |

- 返回实例：
```
{
	"length": 2,
	"status": 1
}
```
- 返回参数说明：
    
|参数名称|说明|
|:-------:|:-------------: |
|length|成功归还图书数量|
|status|获取执行结果，为1时表示都成功执行，为0时表示存在执行失败|


 
