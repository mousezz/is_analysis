#### 用例： 查看成绩、评定成绩
- 权限：学生：只能查看自己的成绩，即接口参数stu_no必须等于登录学生的stu_no 老师：可以查看所有学生的成绩。
- 功能： 返回一个学生的所有实验成绩和实验评价。
- API请求地址： 接口基本地址/api/getOneStudentResult/<term_id>/<course_no>/<test_id>/<stu_no>
- 请求方式 ： GET
- 请求参数说明: 

参数名称 | 说明
---|---
term_id | 学期编号
course_no| 课程编号
test_id| 实验编号
stu_no| 学生编号
- 返回实例：
```
  {         
      "status": true,
      "info": "success",    
      "STU_NO": "201510414221", 
      "GITHUN_NAME": "haozi", 
      "STU_CLASS": "软件15-2", 
      "STU_NAME": "张三", 
      "total": 6,
      "data": [
          {
          "GRADE_ID":1,
          "TEST_ID": "66", 
          "COURSE_NO": "41051", 
          "STU_NO":"201510414221",
          "GRADE":88.8,
          "MOME":"XX部分还需要改进",
          "ADDTIME": "2018-04-01 00:48:01"
          }
      ] 
  }

```
- 返回参数说明：

参数名称	| 说明
---|---
status | bool类型，true表示正确的返回，false表示有错误
info | 返回结果说明信息
STU_NO |学生编号
GITHUN_NAME |GITHUB用户名
STU_CLASS |学生班级
STU_NAME |学生姓名
total |返回记录
data |返回结果的数组
GRADE_ID| 分数编号
TEST_ID |实验编号
COURSE_NO |课程编号
STU_NO |学生编号
GRADE |分数
MOME |评价
ADDTIME |新增时间

