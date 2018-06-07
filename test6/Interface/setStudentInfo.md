#### 用例： 修改学生信息
- 权限：学生/老师：修改自己的密码，必须先登录。
- 功能： 修改学生的基本信息。
- API请求地址： 接口基本地址/api/setPassword/<stu_no>
- 请求方式 ： post
- 请求实例：

```
  {         
      "stu_no":"201510414205",
      "data": 
          {
          "GITHUB_ NAME": "hwan",
          "ID":15,
          "STU_NO": "2015104142105",
          "STU_CLASS": "软件15-2",
          "STU_NAME": "张三",
          "STATUS":"1",
          "ADDTIME": "2018-05-22 17:48:01",
          ...
          }
  }

```
- 请求参数说明：

参数名称	| 说明
---|---
stu_no|学生学号
data | 学生信息集合
ID |数据库自增
GITHUB_ NAME | 	GITHUB 用户名
STU_NO | 学号
STU_CLASS| 班级
STATUS|是否正常
STU_NAME | 真实姓名
ADDTIME | 增加日期

- 返回实例：
```
{         
      "status": true,
      "info": "success"
  }
```


参数名称 | 说明
---|---
status | bool类型，true表示正确的返回，false表示有错误
info | 返回结果说明信息
