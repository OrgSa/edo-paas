.. Contents::
.. sectnum::

文件管理接口
=================

“IRevisionManager”: 版本管理
-------------------------------------

- save(comment='', metadata={}): 存为一个新版本
- retrieve(selector=None, preserve=()): 获得某一个版本
- getHistory(preserve=()): 得到版本历史清单信息
- remove(selector, comment="", metadata={}, countPurged=True): 删除某个版本 
- getWorkingVersionData(): 得到当前工作版本的版本信息，取出来后，在外部维护数据内容
- orderedFolders(): 返回排序后的文件夹集合 
- updateOrder(order): 更新排序


“ISessionAuthorizer”: 临时授权
------------------------------------------------
主要用于文件下载的临时授权，比如在借阅时候的临时授权

- set_permissions(permissions)：设置权限
- check_permission(permission): 检查是否有某个权限
- list_permissions()：列出全部的权限

IFolderManager
------------------
addFile(name, title=u'', description=u'', content_type='text/plain', data='')

添加一个文件

File对象
------------
- get_data(): 得到文件的数据
- set_data(data, filename=None, content_type=None)

  设置文件的内容, filename也是用来计算content_type的, 2个二选一就行

相关方法
-----------------------

- “renderFilePreview”: 文件预览组件
- createShortCut(doc, folder, request)：创建快捷方式
