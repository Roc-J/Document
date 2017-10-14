# Flask Web开发 邮件功能之windows遇到的坑

windows开发真的很坑，一些环境变量设置了...大家都懂得

先来说一下关于环境问题

#### 系统：windows
#### 安装的是Anaconda，一键式安装

本文介绍如何使用Flask-Mail发送邮件。

Flask-Mail连接到简单邮件传输协议（SMTP）服务器，并把邮件交给这个服务器发送。

## 0.安装Flask-Mail

在Anaconda中安装，一条命令搞定

>pip install flask-mail

## 1.Flask-Mail发送邮件

本实例是用163邮箱账户为例发送电子邮件的。

>注意，163常用的收件，发件服务器的地址和端口是什么。

第一步：使用163邮箱，需要先登录客户端进行设置，点击设置>POP3/SMTP/IMAP

![](https://raw.githubusercontent.com/Roc-J/Document/master/photos/step1.PNG)

第二步：点击左侧客户端授权密码

![](https://raw.githubusercontent.com/Roc-J/Document/master/photos/step2.PNG)

进行相关操作开启客户端授权码

>注意，这个客户端授权码是下文要用到的密码

以下是一个简单的代码：flask_email.py

	# -*- coding:utf-8 -*-
	# Author: Roc-J

	from flask import Flask
	from flask_mail import Mail, Message
	import os

	app = Flask(__name__)
	#下面是SMTP服务器配置
	app.config['MAIL_SERVER'] = 'smtp.163.com' #电子邮件服务器的主机名或IP地址
	app.config['MAIL_PORT'] = '465' #电子邮件服务器的端口
	app.config['MAIL_USE_TLS'] = False  #启用传输层安全
	app.config['MAIL_USE_SSL'] = True
	app.config['MAIL_USERNAME'] = os.environ.get('MAIL_USERNAME') #邮件账户用户名
	app.config['MAIL_PASSWORD'] = os.environ.get('MAIL_PASSWORD') #邮件账户的密码

	mail = Mail(app)

	@app.route('/')
	def index():
	    msg = Message('主题', sender=app.config['MAIL_USERNAME'], recipients=['646481338@qq.com'])
	    msg.body = '文本 body'
	    msg.html = '<b>HTML</b> body'
	    mail.send(msg)

	    return '<h1>邮件发送成功</h1>'


	if __name__ == '__main__':
	    app.run()

上面的注释已经写得很明确了，其中邮件用户名和密码要存储到环境变量中，在windows下设置是很有意思的。

打开cmd到当前程序目录下，在命令行中输入

	set MAIL_USERNAME=youremail
	set MAIL_PASSWORD=

>注意，这里的密码是刚刚客户端设置的客户端授权码的密码，不是邮箱的密码。

![](https://raw.githubusercontent.com/Roc-J/Document/master/photos/step3.PNG)

>注意，cmd设置环境变量不需要加引号，直接输入内容即可，并且要注意！注意！注意！这个设置是临时变量，因此不要关闭这个terminal，直接在下面运行该程序

在cmd中接着刚才那两条语句

>python flask_email.py

就可以正确的运行了~
好了，虽然很简单，但是刚开始一直没有出来效果。

![](https://raw.githubusercontent.com/Roc-J/Document/master/photos/step4.PNG)