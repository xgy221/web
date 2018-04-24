# web
web应用程序
Python 编程从入门到实践：项目3 Web应用程序
Django 2.0.4
1.改url为path：

web文件夹下urls.py:

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('learning_logs.urls')),
    path('users/', include('users.urls')),
]

learning_logs文件夹下urls.py:

"""定义learning_logs的URL模式"""

from django.urls import path

from . import views

app_name = 'learning_logs'

urlpatterns = [
    # 主页
    path('', views.index, name='index'),

    # 显示所有的主题
    path('topics/', views.topics, name='topics'),

    # 特定主题的详细页面
    path('topics/<int:topic_id>', views.topic, name='topic'),

    # 用于添加新主题的网页
    path('new_topic/', views.new_topic, name='new_topic'),

    # 用于添加新条目的页面
    path('new_entry/<int:topic_id>', views.new_entry, name='new_entry'),

    # 用于编辑条目的页面
    path('edit_entry/<int:entry_id>', views.edit_entry, name='edit_entry'),
]

users文件夹下urls:

"""为应用程序users定义URL模式"""

from django.urls import path
from django.contrib.auth.views import login

app_name = 'users'

from . import views

urlpatterns = [
    # 登录页面
    path('login/', login, {'template_name': 'users/login.html'}, name='login'),

    # 注销
    path('logout/', views.logout_view, name='logout'),

    # 注册页面
    path('register/', views.register, name='register'),
]

2.reverse导出（其他导出报错，网上查一下就好）：
from django.urls import reverse

3.添加外键
topic = models.ForeignKey(Topic, on_delete=models.CASCADE)

只记得这么多需要改的地方了。。。