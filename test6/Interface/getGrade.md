#### 用例： 分数列表
- 权限： 学生/老师登录后可以看到,访客不能看到。
- 功能： 返回所有分数的列表。
- API请求地址： 接口基本地址/api/getGrade
- 请求方式 ： GET
- 请求参数说明: 无
```
 {
      "status": true,
      "info": "获取结果成功",
      "total": 36,
      "data": [
          {
          "GRADE_ID":2,
          "COURSE_NO":"41052",
          "STU_NO":"201510414221",
          "TEST_ID":"15",
          "GRADE":88.8,
          "MOME":"表现优异",
          "ADDTIME": "2018-05-22 17:48:01",
          ...
          },
          
          {
          ...其他分数
          }
      ]
  }

```
- 返回参数说明：

参数名称	| 说明
---|---
status | bool类型，true表示正确的返回，false表示有错误
info | 返回结果说明信息
total |返回分数数量
data | 所有分数的数组
GRADE_ID | 	数据库自增
COURSE_NO |课程编号
STU_NO |学生编号
TEST_ID |实验编号
GRADE| 分数1
MOME|评价
ADDTIME | 增加日期
