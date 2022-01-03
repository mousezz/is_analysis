# 实验1：业务流程建模

|      学号      | 
| :----------: | 
|  谢颜浩  | 

## 流程图1：考试及成绩管理流程

##### **PlantUML源码如下：**

```
@startuml
|教务处|
:安排考试;
#ff6e6e:考试安排表;
|教师|
:出卷;
split
#hotPink:A、B试卷;
split again
#ff6e6e:打印审批表;
|系主任|
:审批签字;
#ff6e6e:打印审批表;
|教务处|
end split
:打印试卷;
#ff6e6e:试卷;
|学生|
:参加考试;
#ff6e6e:答卷;
|教师|
:阅卷出成绩;
fork
#ff6e6e:成绩单;
|教务处|
if (有不及格？) then (有)
:安排补考;
note left
补考安排表
end note
endif
|教师|
fork again
#ff6e6e:答卷;
:装订存档;
end fork
:期末流程结束;
@enduml
```

![](./考试及成绩管理.png)

## 流程图2： 客户维修服务流程

**PlantUML源码如下：**

```
@startuml
|客户|
start
:申请服务;
|业务经理|
if(是新客户吗？) then(是)
    :登记客户信息;
else(不是)
endif
:上门勘察;
:制定方案;
|客户|
if(满意吗？) then(否)
    stop
else(是)
    :签订服务合同;
endif
|业务经理|
fork
:安排工人;
fork again
:安排材料;
end fork
:填写派工单;
|工人|
:领取材料;
:上门服务;
|客户|
:验收并填写反馈意见;
|业务经理|
:交回派工单;
|财务人员|
:结算收款;
stop
@enduml
```

![](./客户维修流程.png)
