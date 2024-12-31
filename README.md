> #### 作者主页：[舒克日记](https://blog.csdn.net/cativen)
>
>  简介：Java领域优质创作者、Java项目、学习资料、技术互助
>
> <b><font color=red>文中获取源码</font></b>

# 项目介绍

该毕业设计使用了当前较为流行的spring boot，spring，spring mvc，mybatis，shiro框架分页处理使用了pagehelper进行操作，前台使用了模板语言thymeleaf，界面较为炫酷，适合年轻朋友。开发工具采用的是IDEA。该系统主要解决了理财中的一些问题，

包含功能：权限管理，用户信息管理，理财产品管理、工资管理、网贷管理等功能

# 环境要求

1.运行环境：最好是java jdk1.8,我们在这个平台上运行的。其他版本理论上也可以。

2.IDE环境：IDEA,Eclipse,Myeclipse都可以。推荐IDEA;

3.tomcat环境：Tomcat7.x,8.X,9.x版本均可

4.硬件环境：windows7/8/10 4G内存以上；或者Mac OS;

5.是否Maven项目：是；查看源码目录中是否包含pom.xml;若包含，则为maven项目，否则为非maven.项目

6.数据库：MySql5.7/8.0等版本均可；

# 技术栈

运行环境：jdk8 + tomcat9 + mysql5.7 + windows10

服务端技术：Java、Spring、SpringMVC、Mybatis，SSM

# 使用说明

1.使用Navicati或者其它工具，在mysql中创建对应sq文件名称的数据库，并导入项目的sql文件；

2.使用IDEA/Eclipse/MyEclipse导入项目，修改配置，运行项目；

3.将项目中config-propertiesi配置文件中的数据库配置改为自己的配置，然后运行；

# 运行指导

idea导入源码空间站顶目教程说明(Vindows版)-ssm篇：

http://mtw.so/5MHvZq

源码址：[http://www.codegym.top](http://www.codegym.top/)。

# 运行截图

首页，账号：admin，密码：123456

![image20241021234318888](https://img-blog.csdnimg.cn/img_convert/9e140a4268e9507d2b8f3b9fa71b4f69.png)

![image20241021234900862](https://img-blog.csdnimg.cn/img_convert/22a18d90a63abc592c176b9bbaf541df.png)

用户信息：

![image20241021234918856](https://img-blog.csdnimg.cn/img_convert/9d471e4b04e5aaae055d8e311e6eef29.png)

理财管理：

![image20241021234937888](https://img-blog.csdnimg.cn/img_convert/83bac82dad255438ad7433002c4d2b36.png)

工资管理：

![image20241021234957889](https://img-blog.csdnimg.cn/img_convert/55812055be2604621ec0284df8a8d8a2.png)

权限管理：

![image20241021235014893](https://img-blog.csdnimg.cn/img_convert/9a0eb9d7387637207c573fa096ba4b51.png)

### 代码

```
    public DetailEmpVo detail(Long uid) {
        DetailEmpVo vo = new DetailEmpVo();
        //查询员工信息
        Employee employee = super.getById(uid);
        BeanUtils.copyProperties(employee, vo);

        //补全角色信息
        Set<String> roleNames = new HashSet<>();
        if (employee.getIsAdmin() == true) {
            //查询所有角色
            List<Role> list = roleService.list();
            for (Role role : list) {
                roleNames.add(role.getName());

            }
        } else {
            Set<Role> roles = roleService.queryByEid(uid);
            for (Role role : roles) {
                roleNames.add(role.getName());
            }
        }
        vo.setRoleNames(roleNames);
        return vo;
    }
```
