#### 用例：  选择课程
- 权限：访客。
- 功能： 登录到平台。
- API请求地址： 接口基本地址/api/login
- 请求方式 ： post
```
- 请求实例：
 {
      "status": true,
      "info": "获取结果成功",
      "type":students,
      "data": [
          {
          "ID":19,
          "COR_NO":"00001",
          "GRADES":"2015",
          "CALSS":"2"
          "STATUS":"1",
          "ADDTIME": "2018-05-22 17:48:01",
          ...
          },
          
          {
          ...其他实验
          }
      ]
}

```
- 请求参数说明：

参数名称	| 说明
---|---
id|学生学号，由type决定。
grades|学生的年级
class|学生的班级
type|用户类型，学生或者老师

- 返回实例：
```
{         
      "status": true,
      "info": "success"
      "TEST":"返回实验列表"
  }
```


参数名称 | 说明
---|---
status | bool类型，true表示正确的返回，false表示有错误
info | 返回结果说明信息
