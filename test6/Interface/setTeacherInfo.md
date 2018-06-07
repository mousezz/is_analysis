#### 用例： 修改老师信息
- 权限：学生/老师：修改自己的信息，必须先登录。
- 功能： 修改老师的基本信息。
- API请求地址： 接口基本地址/api/setPassword/<tch_no>
- 请求方式 ： post
- 请求实例：

```
  {         
      "tec_no":"201510414205",
      "data": 
          {
          "GITHUB_ NAME": "zwdbox",
          "ID":15,
          "STU_NO": "201510414205",
          "STU_NAME": "赵老师",
          "STATUS":"1",
          "ADDTIME": "2018-05-24 17:48:01",
          ...
          }
  }

```
- 请求参数说明：

参数名称	| 说明
---|---
tec_no|老师学号
data | 老师信息集合
ID|数据库自增
GITHUB_ NAME | 	GITHUB 用户名
TEC_NO | 老师编号
TEC_NAME | 真实姓名
STATUS|是否正常
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


