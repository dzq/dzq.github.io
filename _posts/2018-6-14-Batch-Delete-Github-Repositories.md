# 批量删除 Github Repositories

------

Github的Repositories在删除的时候需要输入Repositories的名称以减少误删除,对于fork了大量仓库的人来说删除它们简直就是一个噩梦.

于是我就开始寻找批量删除方案,只找到了一个 [https://github.com/l294265421/deletegithubproject]

在使用的时候各种缺少类库(请原谅我对于Java的各种不熟悉),最终也没能运行起来.

后来找到了Github REST API V3 [https://developer.github.com/v3/]
但是这个API不太好懂,所以页面又提供了很多第三方类库.
[https://developer.github.com/v3/libraries/]

中间先是尝试了一下JS版本的,出现了各种问题.最终选择了Python版本的.最后成功了

------
进入主题
1 安装Python和pip

参考链接: https://blog.csdn.net/lengqi0101/article/details/61921399/
2 使用pip安装PyGitHub
参考链接: https://pygithub.readthedocs.io/en/latest/introduction.html
3 代码
新建git.py,输入以下内容,使用python运行
```python
from github import Github
g = Github(username, password)
for repo in g.get_user().get_repos():
    print(repo.name)
    repo.delete()
```
4 存在的问题
如果仓库太多,可能需要多运行几次

~End~
