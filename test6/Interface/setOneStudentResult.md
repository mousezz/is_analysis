#### 用例： 评定成绩
- 权限：老师登录后可以查看
- 功能：  设置一个学生的部分实验成绩和评语。    
- API请求地址： 接口基本地址/api/setOneStudentResults
- 请求方式 ： post
- 请求实例：

```
  {         
      "STU_NO": "201510414221", 
      "GITHUN_NAME": "haozi", 
      "STU_CLASS": "软件15-2", 
      "STU_NAME": "张三", 
      "data": [
          {
          "GRADE_ID":1,
          "TEST_ID": "233", 
          "COURSE_NO": "4051", 
          "STU_NO":"201510414221",
          "GRADE":88.8,
          "MOME":"XX部分很不错",
          }
      ] 
  }

```
- 请求参数说明：

参数名称	| 说明
---|---
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
