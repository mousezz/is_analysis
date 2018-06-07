#### 用例： 学生列表
- 权限： 学生/老师都能看到列表，访客不能看到列表。
- 功能： 返回所有学生的列表。
- API请求地址： 接口基本地址/api/getStudents
- 请求方式 ： GET
- 请求参数说明: 无
```
 {
      "status": true,
      "info": "获取结果成功",
      "total": 51,
      "data": [
          {
          "GITHUB_ NAME": "haozi",
          "ID":15,
          "STU_NO": "201510414221",
          "STU_CLASS": "软件(本)15-2",
          "STU_NAME": "耗子",
          "STATUS":"1",
          "ADDTIME": "2018-05-22 17:48:01",
          "TERM_ID":2,
          "GRADE_ID":2,
          "TEST_ID":2,
          "COURSE_NO":25,
          "GRADE":95,
          "MOME":"省略。",
          ...
          },
          
          {
          ...其他学生
          }
      ]
  }

```
- 返回参数说明：

参数名称	| 说明
---|---
status | bool类型，true表示正确的返回，false表示有错误
info | 返回结果说明信息
total |返回学生人数
data | 所有学生的数组
GITHUB_ NAME | 	GITHUB 用户名
STU_NO | 学号
STU_NAME | 真实姓名
ADDTIME | 增加日期
ID | 数据库中编号
STATUS | 是否正常
TERM_ID | 学期编号
GRADE_ID | 成绩编号
TEST_ID | 实验编号
COURSE_NO | 课程编号
GRADE | 分数
