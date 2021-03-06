﻿.. Contents::
.. sectnum::


object_notify (重要，最常用)
======================================
object_notify可采用用户对对象的订阅方式(短信、邮件、系统消息)，进行消息发送::

    def object_notify(context=None, body=None, title='', to_pids=None, action='', from_pid=None, 
            exclude_me=True, exclude_ids=[], attachments=[], methods=None):
        """ 把消息发送给相关人员, 不同的通知方式，采用不同的通知文本
     
        body: 用户输入的消息文本
        title: 用户输入的标题信息
        to_pids: 如果为空，发送给对象的订阅人
        action: 用于自定义标题: 张三 - event: title
        exclude_me: 是否允许自己给自己发通知
        exclude_ids: 需要排除的人
        """

notifier_message
=============================

系统xmpp通知工具接口：::

    send (title, body, to_pids,from_id=None, exclude_ids=[], context=None, attachments=[], action='')


通知效果::

  张三 action : [title]body
  关联对象: context
  附件：attachment 1
        attachment 2

注意：根据不同的action，以及不同的context类型，自动选择不同的channel进行发送

notifier_email: 电子邮件
=====================================
可直接发送邮件，有个to_emails参数::

    send (title, body, to_pids, to_emails=[], from_id=None, exclude_ids=[], context=None, attachments=[], action='')

邮件效果::

    邮件标题：张三 action：title
    邮件正文：body
    
              关联对象：名称 http://xxx
              附件：

notifier_sms: 短信
=====================================
可直接发送短信，有个to_numbers参数::

    send (title, body, to_ids, to_numbers=[], from_id=None, exclude_ids=[], context=None, attachments=[], action='')

短信效果::

   张三 action：[title] body , 关联对象是 xxx


action的定义
==============================
每个action对应的各种翻译msgid为： action_xxx

- share： 分享
- new : 新建
- upload：上传
- comment: 评论
- new_revision: 更新版本
- fix_revision: 定版
- workflow_sign ： 触发流程
- workflow_resign ： 更改流程
