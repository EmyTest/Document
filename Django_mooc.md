快速开发：  
  -python开发  
  -数据库orm系统  
大量内置应用：
   -后台管理系统
   -用户认证系统auth
   -会话系统session
   
安全性高
易于拓展


知识储备
    python基础  
    数据库相关基础  
    http协议  
    HTML&CSS  
    正则表达式  
    
https://code.ziqiangxuetang.com/django/django-tutorial.html


python -m pip install django【第一次打不开 配了环境变量还是打不开  然后卸载 换了命令  打开了网页 】    

##【Templates 介绍】       
HTML文件  
使用django模板语言（django template language   DTL）   
可以使用第三方   jinja2    

setting文件 --》  TEMPLATES --》  BACKEND 后面的数据 “django.template.backends.django.DjangoTemplates”      


开发一个template    
1、在app根目录下创建一个名叫Templates 的目录    
2、在该目录下创建HTML文件    
3、在views.py文件返回一个render   

DTL的初步使用    
render（）函数中支持一个叫dict类型的参数   
该字典是后台传递到模板的参数，键为参数名    
在模板中使用{{参数名}} 来直接使用    


django查找templates   
django按照installed_apps 中的添加顺序查找templates   
不同app下的templates目录中的同名.HTML文件会造成冲突    

解决templates冲突的方案    
在app的templates目录下创建以app名为名称的目录  
将HTML文件放入新创建的目录下   
 


models介绍  
django中的models是什么？  
通常，一个model对应数据库的一张数据表  
django中的models以类的形式表现  
它包含了一些基本字段以及数据的一些行为  

ORM 对象关系映射  
对象关系映射（object relation mapping）  
实现了对象和数据库之间的映射  
隐藏了数据库访问的细节，不需要编写sql语句  

编写models
步骤：  
在应用根目录下创建models.py，并引入models模块   
创建类，继承models.model，该类即是一张数据表  
在类中创建字段  

字段创建:  
字段即类里面的属性（变量）  
attr = models.CharField(max_length=64)  
其他见django官网  


生成数据表  
步骤  ：   
命令行中进入manage.py 同级 目录  
执行python manage.py makemigrations app 名（可选）  
再执行python manage.py migrate  

生成数据表  
查看  
django会自动在app/migrations/目录下生成移植文件  
执行python manage.py sqlmigrate 应用名 文件id  查看sql语句  
默认sqlite的数据库在项目根目录下 db.sqlite3  

查看并编辑db.sqlite3   
使用第三方软件  
sqlite expert personal  

页面呈现的数据  
后台步骤  
views.py 中 import models  
article = models.Article.objects.get(pk=1)  
rednder(request,page,{'article':article})

前端步骤  ：  
模板可直接使用对象以及对象的“.”操作  
{{article.title}}





admin
django自带的自动化数据管理界面  
配置admin：  
创建用户
python manage.py createsuperuser 创建超级用户

博客主页面
模板for循环
{% for xx in xxs %}

HTML语句
{% endfor %}
